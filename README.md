# TaskFlow — Task Manager App

A lightweight Kanban-style task manager with drag & drop, priority levels, and automatic local storage. Built with pure HTML, CSS, and JavaScript — no frameworks, no installation required.

---

## Features

- **Drag & Drop** — Drag task cards between columns effortlessly
- **3 Kanban Columns** — To Do → In Progress → Done
- **Priority Levels** — High (red), Medium (yellow), Low (green)
- **Live Progress Bar** — Completion percentage updates automatically
- **Local Storage** — Data persists across page refreshes via `localStorage`
- **Keyboard Shortcut** — Press `Enter` to add a task without clicking the button
- **Toggle Done** — Click the check icon on any card to mark it complete or revert
- **Delete Tasks** — Delete button appears on card hover
- **Responsive Layout** — Columns stack vertically on mobile screens

---

## Getting Started

### Running the App

No installation needed. Just open the file in any browser:

```
Double-click taskflow.html
```

Or open via terminal:

```bash
# macOS
open taskflow.html

# Linux
xdg-open taskflow.html

# Windows
start taskflow.html
```

### Adding a Task

1. Type the task name in the input field at the top
2. Select a priority level from the dropdown
3. Click **Add** or press `Enter`

### Moving Tasks

Click and hold a card, then drag it to the desired column:

| Column | Description |
|--------|-------------|
| **To Do** | Tasks not yet started |
| **In Progress** | Tasks currently being worked on |
| **Done** | Completed tasks |

### Card Actions

Hover over a card to reveal action buttons:

| Button | Action |
|--------|--------|
| ○ (circle) | Mark as done |
| ✓ (green check) | Revert to To Do |
| 🗑 (trash) | Permanently delete the task |

---

## Code Structure

The entire application lives in a single `taskflow.html` file with three main sections:

```
taskflow.html
├── <style>     — All styling (dark theme, animations, layout)
├── <body>      — HTML structure (topbar, add bar, 3-column board)
└── <script>    — App logic (state, render, drag & drop, localStorage)
```

### State Management

Tasks are stored in a plain JavaScript array:

```javascript
let tasks = [
  { id: 1, title: 'Task name', priority: 'high', col: 'todo', date: '11 May' },
  // ...
];
```

Every change (add, delete, move) triggers a save back to `localStorage`.

### Column Reference

| Column ID | Label |
|-----------|-------|
| `todo` | To Do |
| `doing` | In Progress |
| `done` | Done |

### Priority Reference

| Value | Label | Color |
|-------|-------|-------|
| `high` | High | Red |
| `med` | Medium | Yellow |
| `low` | Low | Green |

---

## Customization

### Changing the Color Theme

Edit the CSS variables in the `:root` block inside `<style>`:

```css
:root {
  --bg: #0f0f13;           /* Main background */
  --surface: #1a1a22;      /* Column/card surface */
  --surface2: #22222e;     /* Task card background */
  --accent-todo: #6c6cff;  /* To Do column accent */
  --accent-doing: #f5a623; /* In Progress column accent */
  --accent-done: #2dc98e;  /* Done column accent */
}
```

### Adding a New Column

1. Add a new column element in the HTML with `id="col-newname"`
2. Attach drag & drop handlers (`ondragover`, `ondrop`, `ondragleave`)
3. Register the new column in the `render()` function's column loop

### Changing Fonts

Fonts are loaded via Google Fonts. Replace the `<link>` tag and update the CSS variables:

```css
--font-head: 'YourFont', sans-serif;
--font-body: 'YourFont', sans-serif;
```

---

## External Dependencies

All loaded via CDN — no local installation needed:

| Dependency | Purpose | Source |
|------------|---------|--------|
| Syne & DM Sans | Typography | Google Fonts |
| Tabler Icons | UI icons (check, trash, inbox) | jsDelivr CDN |

The app works fully offline once CDN assets are cached by the browser.

---

## Browser Compatibility

| Browser | Status |
|---------|--------|
| Chrome 80+ | ✅ Fully supported |
| Firefox 75+ | ✅ Fully supported |
| Safari 14+ | ✅ Fully supported |
| Edge 80+ | ✅ Fully supported |

---

## License

Free to use and modify for personal or commercial purposes.
