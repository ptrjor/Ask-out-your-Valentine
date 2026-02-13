# Valentine's Day Interactive Website (CodeKage)

A cute, interactive web page to ask someone to be your Valentine. Features playful button mechanics, heartwarming GIFs, and heart-shaped confetti.

## How It Works

1. The page presents the question **"Will you be my Valentine?"** alongside a cute GIF.
2. Clicking **No** swaps the GIF, changes the button text to increasingly desperate pleas, and grows the **Yes** button bigger and bigger.
3. Clicking **Yes** celebrates with a special GIF, a victory message, and a burst of heart-shaped confetti.

## Features

- **Growing "Yes" button** -- gets larger with every "No" click, making it impossible to ignore.
- **Desperate messages** -- the "No" button cycles through pleading texts like *"Pookie please"* and *"I'm gonna cry..."*.
- **Animated GIFs** -- seven different GIFs that react to the user's choices.
- **Heart confetti** -- pink heart-shaped confetti explosion on "Yes" using [canvas-confetti](https://www.npmjs.com/package/canvas-confetti).
- **Responsive design** -- looks great on desktop and mobile, powered by [Tailwind CSS](https://tailwindcss.com).

## Getting Started

1. Clone the repository:
   ```bash
   git clone https://github.com/CodeKageHQ/Ask-out-your-Valentine.git
   ```
2. Open `index.html` in your browser.

That's it -- no build step, no dependencies to install. Tailwind CSS and canvas-confetti are loaded via CDN.

## Save Responses with Google Forms (easiest option)

This project supports saving button clicks (`yes` / `no`) directly to a Google Form.

### 1) Create a form

Create a Google Form with at least one short-answer question, for example:

- `Answer` (required)
- `Visitor ID` (optional)

### 2) Get the form endpoint + entry IDs

1. Open your form and click **⋮ → Get pre-filled link**.
2. Fill sample values and click **Get link**.
3. Copy the URL and identify:
   - form action URL: `https://docs.google.com/forms/d/e/<form-id>/formResponse`
   - entry IDs from query params like `entry.123456789=sample`

### 3) Add config in `index.html`

Before the main `<script>` block, add:

```html
<script>
  window.VALENTINE_CONFIG = {
    googleFormActionUrl: 'https://docs.google.com/forms/d/e/<form-id>/formResponse',
    googleFormAnswerEntry: 'entry.1234567890',
    googleFormVisitorEntry: 'entry.0987654321', // optional
    notifyWebhookUrl: 'https://ntfy.sh/<your-topic>' // optional
  };
</script>
```

### 4) Get notified of answers

Choose one easy option:

- **Google Sheets notifications**: Link form responses to a sheet, then enable notification rules in Sheets.
- **Optional webhook** (`notifyWebhookUrl`): send instant alerts to ntfy, Discord webhook, Zapier/Make, etc.

## Other easy alternatives

- **Supabase**: more structured database if you want querying + auth later.
- **Formspree/Basin**: very simple form endpoint for static sites.
- **Discord webhook only**: quickest route if you just need notifications.

## Project Structure

```
Ask-out-your-Valentine/
├── images/
│   ├── image1.gif    # Default greeting
│   ├── image2.gif    # After 1st "No"
│   ├── image3.gif    # After 2nd "No"
│   ├── image4.gif    # After 3rd "No"
│   ├── image5.gif    # After 4th "No"
│   ├── image6.gif    # After 5th "No"
│   └── image7.gif    # "Yes" celebration
├── index.html        # The entire app (HTML + CSS + JS)
├── LICENSE
└── README.md
```

## Customization

Want to make it your own? Here are some easy tweaks inside `index.html`:

| What | Where | How |
|------|-------|-----|
| GIF images | `images/` folder | Replace the GIFs with your own (keep the same filenames) |
| "No" button messages | `NO_BUTTON_MESSAGES` array | Edit the strings to say whatever you like |
| Button growth speed | `GROWTH_PER_CLICK` / `FONT_GROWTH_PER_CLICK` constants | Lower the numbers for subtler growth |
| Confetti colors | `colors` array in the `yesButton` click handler | Swap in any hex color codes |
| Background gradient | `.gradient-background` in `<style>` | Change the hex colors |

## Technologies

- **HTML5** -- semantic markup with `<main>` and `<section>`
- **Tailwind CSS** -- utility-first styling via CDN
- **JavaScript** -- vanilla JS, no frameworks
- **canvas-confetti** -- lightweight confetti animation library

## Contributing

Contributions are welcome! Whether it's new GIF suggestions, design tweaks, or code improvements -- fork the repo and open a pull request.

## License

Open source under the [MIT License](LICENSE).

Happy Valentine's Day! ❤️
