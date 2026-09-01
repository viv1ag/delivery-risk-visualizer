# Delivery Risk Visualizer

A zero-install, browser-based Gantt chart tool for engineering delivery planning. Simulate ticket delays, see cascading impacts across teams, and instantly know if your hard deadline is at risk - no server, no login, no setup required.

---

## Live Demo

Try it now: **https://viv1ag.github.io/delivery-risk-visualizer/**

---

## Quick Start

1. Download `index.html` from this repo (click the file → **Raw** → Save As)
2. Open it in Chrome or Firefox - that's it
3. Click **Load Sample** to explore a pre-built 3-team, 8-ticket demo plan

---

## Step-by-Step Guide

### Step 1 - Set Your Requirement

The **requirement** is the top-level delivery with a hard end date (e.g. a product release or compliance deadline).

1. Open the **Setup** tab (top navigation)
2. Under **Requirement**, enter:
   - **Name** - e.g. "Platform v2 Release"
   - **Hard End Date** - the fixed deadline your stakeholders have committed to
3. Changes save automatically

---

### Step 2 - Add Teams

Teams become swimlanes in the Gantt chart. Each team gets its own color and row.

1. In the **Teams** section, click **+ Add Team**
2. Enter the team name (e.g. "Backend", "Frontend", "Data")
3. Add as many teams as needed
4. To remove a team, click the trash icon - its tickets will also be removed

---

### Step 3 - Add Tickets

Tickets are the units of work (think Jira stories or tasks).

1. In the **Tickets** section, click **+ Add Ticket**
2. Fill in:
   - **Name** - short label shown on the Gantt bar (e.g. "API Auth")
   - **Team** - which swimlane this ticket belongs to
   - **Start Date** and **End Date** - the baseline planned dates
   - **Depends On** - select upstream tickets that must finish before this one starts (multi-select)
3. Repeat for all tickets in the plan

> **Tip:** Dates drive the Gantt bar position. Set realistic baseline dates - you'll simulate slippage separately.

---

### Step 4 - Switch to Gantt View

Click the **Gantt** tab in the top navigation.

You will see:
- **Swimlanes** - one horizontal row per team
- **Bars** - each ticket shown as a colored bar spanning its start-to-end dates
- **Dashed grey arrows** - dependency connections between tickets
- **Dashed red vertical line** - your hard deadline
- **Status badge** in the top bar - shows **✓ On track** (green) or **⚠ N days late** (red) at a glance

---

### Step 5 - Simulate a Delay

This is the core feature. Drag any bar to the right to simulate that ticket slipping.

1. Hover over a ticket bar - the cursor changes to a resize arrow
2. Click and drag right to add delay days
3. Watch downstream tickets automatically shift based on dependencies
4. The **status badge** updates instantly - if the deadline is breached, it turns red and shows how many days late
5. A red top banner also appears when the deadline is breached

> **Key behavior:** Dragging a ticket only delays it - it never moves earlier than its baseline. Upstream delays cascade forward; downstream tickets absorb the slip automatically.

---

### Step 6 - Use the Delay Sliders

The **bottom panel** ("Simulate Delay per Ticket") gives you precise numeric control.

1. Each ticket has its own slider showing delay in days (0 to 30)
2. Drag the slider or type a value to set an exact delay
3. All cascades and the deadline status update in real time
4. Click **Reset all** to clear all simulated delays at once

---

### Step 7 - Read the Gantt Chart

| Visual element | What it means |
|---|---|
| **Red bar** | Ticket is on the critical path - any further delay directly pushes the deadline |
| **Orange/amber bar** | Ticket's effective end date has passed the hard deadline |
| **Team color bar** | Normal - ticket has float and is not blocking delivery |
| **Dashed grey arrow** | Dependency: the downstream ticket cannot start until the upstream one finishes |
| **Dashed red vertical line** | Hard deadline |
| **⚠ N days late** badge | Latest ticket end is N days beyond the hard deadline |
| **✓ On track** badge | All tickets finish on or before the hard deadline |

---

### Step 8 - Save and Share Your Plan

#### Save to JSON
Click **Save JSON** - downloads a `.json` file with your full plan (requirement, teams, tickets, and current simulation state).

#### Load a saved plan
Click **Load JSON** → pick your saved file → the plan restores instantly, including any simulated delays.

#### Load the sample demo
Click **Load Sample** to replace the current plan with the built-in 3-team, 8-ticket demo (useful for onboarding others).

> **Note:** JSON save/load is fully browser-side - no file ever leaves your machine.

#### Auto-save
The tool auto-saves to your browser's `localStorage` every time you make a change. Refreshing the page restores your last state.

---

### Step 9 - Share with Stakeholders

Since the entire app is a single HTML file, sharing is simple:

- **GitHub Pages** - enable Pages on this repo (Settings → Pages → deploy from `main`) and share the URL
- **Email / Teams / Slack** - attach `index.html` directly; recipients open it in their browser with no installation
- **Shared drive** - drop it in a OneDrive / SharePoint folder; anyone with the link can open and use it
- **JSON plan files** - share `.json` plan files alongside `index.html` so teammates can load the same plan

---

## Feature Summary

| Feature | Details |
|---|---|
| Zero install | Single HTML file, open in any modern browser |
| Multi-team swimlanes | One row per team, color-coded |
| Dependency graph | Tickets depend on one or more upstream tickets |
| Cascading simulation | Drag to delay - all downstream dates auto-recalculate |
| Critical path | Computed automatically; critical tickets shown in red |
| Hard deadline tracking | Fixed red line + live "on track / N days late" badge |
| Delay sliders | Precise per-ticket delay control (0–30 days) |
| Save / Load JSON | Full plan persistence, browser-side only |
| Auto-save | Saves to localStorage on every change |
| No server needed | Fully offline capable after first load |

---

## File Structure

```
delivery-risk-visualizer/
├── index.html          # Entire application (React 18 + Tailwind, CDN-hosted)
└── sample-plan.json    # Pre-built 3-team, 8-ticket demo plan
```

---

## Browser Support

Chrome 90+ or Firefox 88+ recommended. Edge (Chromium) also works. Safari is untested.
