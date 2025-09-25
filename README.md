# EventPlanner

A simple client-side Event Planner web app built with plain HTML, CSS and JavaScript. It lets users create events, view event details, RSVP, and send mock or real email invitations using EmailJS.

Clone repository:
```bash
git clone https://github.com/samwel-gachiri/event-planner.git
```
## Features

- Create and store events locally (localStorage)
- Browse and search events
- View event details, RSVP, and see guest list
- Send invitation emails via EmailJS (or use built-in mock send for development)
- Simple dashboard and analytics

## Run locally (Windows PowerShell)

The app is a static site. To open it in your default browser from PowerShell, run:

```bash
# From the project root (where index.html lives)
start index.html
```

Or you can open the file directly from File Explorer by double-clicking `index.html`.


## Invitation / EmailJS setup

The app includes a UI to "Invite" someone from the event details screen. By default the app performs a mock send (useful for development). To send real emails, configure EmailJS:

1. Sign up at https://www.emailjs.com/
2. Create a Service and note the Service ID (e.g., `service_xxx`).
3. Create an Email Template and note the Template ID (e.g., `template_xxx`).
4. Get your EmailJS User ID (public key), e.g., `user_xxx`.

You can configure these values in two ways:

- Edit `script.js` and set `app.EMAILJS_USER_ID`, `app.EMAILJS_SERVICE_ID`, and `app.EMAILJS_TEMPLATE_ID`.
- Or open the browser DevTools console after the app loads and run:

```javascript
app.configureEmailJS({ userId: 'user_xxx', serviceId: 'service_xxx', templateId: 'template_xxx' });
```

Template variables the code sends by default: `to_email`, `to_name`, `event_title`, `event_date`, `event_time`, `event_venue`, `message`.

## Usage

1. Open `index.html` (see Run locally above).
2. Create an event via "Create Event".
3. View event details and click "Invite" to enter recipient email and send.
4. RSVP from event cards or the details page.

## Development notes

- The app stores events in `localStorage` under the key `eventPlannerEvents`.
- The invite modal and EmailJS integration are implemented client-side. For production usage, prefer server-side sending to protect credentials and improve deliverability.
- Basic validation is implemented for event fields and email format.

## License

MIT