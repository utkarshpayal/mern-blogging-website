# Fullstack MERN Blogging Website

This is a fork of the "MERN Blogging Website" starter repository, used to follow the video tutorial.

Checkout website demo - [Demo](https://youtu.be/J7BGuuuvDDk)

![Thumbnail](https://c10.patreonusercontent.com/4/patreon-media/p/post/90122909/dd5363bd03fb4a6c8fcd5d15df98e6bf/eyJ3Ijo4MjB9/1.png?token-time=1697414400&token-hash=BZ-Mzp19WnBLcCFB8LmJFDw98mpnCRGcOCt_T615miY%3D)

## Current Status

This repository currently contains the **starter files** provided for the tutorial, not the finished website:

- **Implemented:** project scaffolding (Vite + React + Tailwind CSS frontend, Node/Express server `package.json`), global styles and Tailwind theme, image assets, a loader component, and the Mongoose schemas for users, blogs, comments and notifications.
- **Placeholders (empty files):** `server/server.js`, almost all frontend pages and components, and the helpers in `src/common/` (AWS, Firebase, session, date, pagination, page animation). These are filled in while following the tutorial.

Running the frontend right now shows a single heading ("MERN Blogging website by modern web").

## Planned Features (from the tutorial)

The finished website built in the tutorial includes:

1. Modern Blog Editor using Editor JS.
2. Google Authentication for Users
3. Dynamic Blog Pages on dynamic urls.
4. Search Page for Searching Blogs & users.
5. Dedicated Users Profile with their social links and written blogs.
6. Dedicated dashboard to manage blogs either published or draft.
7. Blog Post Analytics, editable and deletable.
8. Like interaction on Blogs with feature to comment on the blog.
9. Reply to comments. ( A nested Comment System )
10. Every interaction on site stores as a notification for their respective users.
11. Recent notification highlight separating them from old notifications.
12. Edit profile option to update social links, bio and username
13. Also user can change login password from settings.
14. Its mobile responsive with modern design + fade in animation on pages.

And much more.

## Tech Stack

**Frontend** (`blogging website - frontend/`)
- React 18 + Vite, React Router v6
- Tailwind CSS (PostCSS + Autoprefixer)
- Editor.js and plugins (header, list, image, embed, code, quote, marker, link, inline code)
- Firebase (client SDK, for Google authentication)
- Axios, Framer Motion, react-hot-toast, Flaticon UIcons

**Backend** (`server/`)
- Node.js (ES modules) + Express
- MongoDB with Mongoose
- bcrypt, jsonwebtoken, nanoid, cors, dotenv
- firebase-admin (Google auth verification) and aws-sdk (image uploads)
- nodemon for development

## Project Structure

```
blogging website - frontend/
├── src/
│   ├── common/       # Helper modules (placeholders)
│   ├── components/   # UI components (mostly placeholders)
│   ├── imgs/         # Logo, banner, 404 and default profile images
│   ├── pages/        # Page components (placeholders)
│   ├── App.jsx
│   ├── index.css     # Global styles
│   └── main.jsx
└── tailwind.config.js
server/
├── Schema/           # Mongoose models: User, Blog, Comment, Notification
├── requests.rest     # Sample HTTP request for testing the API
└── server.js         # Express server (placeholder)
```

### Data models (`server/Schema`)

- **User** (`users`) – personal info, social links, account info (blog/read counts), Google auth flag and references to the user's blogs.
- **Blog** (`blogs`) – `blog_id`, title, banner, description, content, tags, author, activity counters (likes, comments, reads, parent comments), comments and a `draft` flag.
- **Comment** (`comments`) – blog, blog author, comment text, nested `children`/`parent` replies and the commenter.
- **Notification** (`notification`) – notification type (like, comment, reply), the related blog, users and comments, and a `seen` flag.

## Setup

Prerequisites: Node.js and npm, plus a MongoDB database. Firebase and AWS accounts are needed later in the tutorial for Google sign-in and image uploads.

```bash
# Frontend
cd "blogging website - frontend"
npm install
npm run dev        # start the Vite dev server

# Backend (in another terminal)
cd server
npm install
npm start          # runs `nodemon server.js`
```

Other frontend scripts: `npm run build` (production build), `npm run preview` (preview the build), `npm run lint` (ESLint).

## Configuration

The server depends on `dotenv`, so it is expected to read its settings from a `.env` file in `server/`. No environment variables are referenced in the current code yet; the exact variable names (e.g. for the MongoDB connection, JWT secret and AWS credentials) are defined while following the tutorial (needs confirmation). Do not commit `.env` files or Firebase service-account keys.
