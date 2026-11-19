# Implementation Plan - Dental Clinic Web Application

Create a responsive, full-stack, single-page web application for a Dental Clinic. The project will feature a Node.js/Express backend and an HTML/Tailwind CSS/Vanilla JS frontend, with an in-memory appointment booking system.

## User Review Required

> [!IMPORTANT]
> The application will use an in-memory array on the Node.js server to store appointments. This data will be cleared if the server restarts.

## Open Questions

> [!IMPORTANT]
> Which Tailwind CSS version should we use?
> - **Option A (Recommended):** Tailwind CSS v3 via CDN (`https://cdn.tailwindcss.com`). This is quick, requires no build step, and runs perfectly for a single-page prototype.
> - **Option B:** Tailwind CSS v4 via CDN/PostCSS if a build step is preferred.

## Proposed Changes

We will create the project inside the directory `C:\Users\msi\.gemini\antigravity\scratch\dental-clinic`.

---

### Backend

#### [NEW] [package.json](file:///C:/Users/msi/.gemini/antigravity/scratch/dental-clinic/package.json)
- Define dependencies: `express`, `cors`, `body-parser`.
- Set up start script.

#### [NEW] [server.js](file:///C:/Users/msi/.gemini/antigravity/scratch/dental-clinic/server.js)
- Set up Express server listening on port 3000.
- Serves static files from the `public` directory.
- Implement an in-memory array `appointments` to store booking data.
- Implement `POST /api/book` endpoint:
  - Validates `name`, `email`, `phone`, `date`, `time`.
  - Saves valid appointments to the in-memory array.
  - Returns a success JSON response.
- Implement `GET /api/appointments` endpoint (optional helper to inspect bookings).

---

### Frontend

#### [NEW] [public/index.html](file:///C:/Users/msi/.gemini/antigravity/scratch/dental-clinic/public/index.html)
- Responsive dental clinic single-page application.
- Uses Tailwind CSS CDN for modern teal/cyan styling.
- **Navbar:** Responsive layout with desktop links and mobile hamburger menu.
- **Hero Section:** Engaging headline, call-to-action to book, and Unsplash female dentist image.
- **Services Section:** A 3-column responsive grid showcasing Teeth Whitening, Orthodontics, and Dental Implants.
- **Booking Form:** Captures Name, Email, Phone, Preferred Date, and Time.
- **Vanilla JS:**
  - Hamburger menu toggle logic.
  - Event listener for form submission to POST to `/api/book`.
  - Display a beautiful custom success/error modal without page reload.
- **Footer:** Dummy contact info, clinic details, and copyright.

---

## Verification Plan

### Automated Tests
- Run simple curl/fetch validation to verify backend API endpoint validation.

### Manual Verification
- Start the server using `node server.js` and open the page in the browser.
- Verify the mobile responsive hamburger menu.
- Submit the booking form and verify the success modal popup.
- Verify validation handles empty or malformed fields on the backend.
