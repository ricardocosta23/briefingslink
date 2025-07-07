# PDF File Sharing Application

A simple web application for uploading PDF files and generating shareable links.

## Features

- Upload PDF files via drag-and-drop or file picker
- Generate shareable browser links for uploaded files
- File validation (PDF only, 10MB max size)
- File management (view, download, delete)
- Clean, responsive UI

## Local Development

1. Install dependencies:
```bash
npm install
```

2. Start the development server:
```bash
npm run dev
```

3. Open your browser to `http://localhost:5000`

## Vercel Deployment

### Prerequisites

1. Install Vercel CLI:
```bash
npm install -g vercel
```

2. Login to Vercel:
```bash
vercel login
```

### Deployment Steps

1. Build the project:
```bash
npm run build
```

2. Deploy to Vercel:
```bash
vercel --prod
```

### Environment Variables

For production deployment, you'll need to set up the following environment variables in your Vercel dashboard:

- `DATABASE_URL`: PostgreSQL connection string (if using database storage)
- `NODE_ENV`: Set to `production`

### File Storage Solution

✅ **Permanent Database Storage**: The application now stores PDF files directly in the database as base64-encoded data, ensuring:

1. **Permanent Storage**: Files are stored permanently in the database
2. **Vercel Compatible**: Works perfectly with Vercel's serverless environment
3. **No External Dependencies**: No need for additional cloud storage services
4. **Automatic Backup**: Files are backed up with your database

### Storage Details

- **File Format**: PDF files are converted to base64 and stored in the database
- **Size Limit**: 10MB per file (suitable for most PDF documents)
- **Memory Usage**: Files are processed in memory and stored efficiently
- **Access**: Files are served directly from the database with proper PDF headers

### Project Structure

```
├── client/          # React frontend
├── server/          # Express.js backend
├── shared/          # Shared types and schemas
├── Briefings/       # Local file storage (development only)
├── vercel.json      # Vercel deployment configuration
└── package.json     # Dependencies and scripts
```

## API Endpoints

- `GET /api/files` - Get all uploaded files
- `POST /api/files/upload` - Upload a new PDF file
- `GET /api/files/view/:filename` - View/download a file
- `DELETE /api/files/:id` - Delete a file

## Technology Stack

- **Frontend**: React 18, TypeScript, Tailwind CSS, Radix UI
- **Backend**: Express.js, TypeScript, Multer
- **Database**: PostgreSQL with Drizzle ORM
- **Build Tool**: Vite
- **Deployment**: Vercel