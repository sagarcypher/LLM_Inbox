# Inbox Zero AI

An intelligent email productivity assistant powered by Large Language Models (LLMs) that helps you achieve inbox zero by automatically triaging, summarizing, and generating responses for your emails.

## 🚀 Features

- **Gmail Integration**: Connect securely with OAuth 2.0
- **Smart Summarization**: AI-powered email summaries using Hugging Face models
- **Action Item Extraction**: Automatically identify tasks and assignees
- **AI Reply Suggestions**: Generate contextual responses with tone matching
- **Auto-categorization**: FYI, Action Needed, Calendar/Meeting, Invoice/Finance, Spam/Ignore
- **Analytics Dashboard**: Track productivity and AI effectiveness
- **Tone Personalization**: Learn from your writing style for better suggestions

## 🛠 Tech Stack

- **Backend**: Node.js, Express, TypeScript, SQLite, Gmail API
- **Frontend**: React, TypeScript, Tailwind CSS, Vite
- **AI/ML**: Hugging Face Free API (completely free!)
- **Auth**: JWT + Google OAuth 2.0
- **Database**: SQLite with optional ChromaDB for vector operations

## 📋 Prerequisites

- Node.js 18+ and npm
- Google Cloud Console account (for Gmail API)
- Hugging Face account (free) for AI processing

## 🔧 Installation

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/inbox-zero-ai.git
cd inbox-zero-ai
npm install
```

### 2. Google OAuth Setup
1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select existing
3. Enable Gmail API
4. Create OAuth 2.0 credentials (Web application)
5. Add redirect URI: `http://localhost:3000/auth/callback`

### 3. Hugging Face API Setup
1. Visit [Hugging Face Settings](https://huggingface.co/settings/tokens)
2. Create a **FREE** API token
3. Copy the token for your .env file

### 4. Environment Configuration
Create `.env` file in project root:
```env
# Google OAuth Configuration  
GOOGLE_CLIENT_ID=your-google-client-id
GOOGLE_CLIENT_SECRET=your-google-client-secret
GOOGLE_REDIRECT_URI=http://localhost:3000/auth/callback

# Hugging Face Configuration (FREE!)
HUGGINGFACE_API_KEY=your-hugging-face-token

# JWT Configuration
JWT_SECRET=your-super-secret-jwt-key

# Optional: Database Configuration
# CHROMA_DB_PATH=http://localhost:8000
```

## 🏗️ Architecture

### Backend (Node.js + TypeScript)
- **Express.js** server with TypeScript
- **SQLite** database for application data
- **ChromaDB** vector database for tone embeddings
- **Gmail API** integration for email access
- **Hugging Face API** for free text processing and analysis
- **JWT** authentication with Google OAuth 2.0

### Frontend (React + TypeScript)
- **React 18** with TypeScript and modern hooks
- **Tailwind CSS** for responsive, beautiful UI
- **React Query** for efficient data fetching and caching
- **React Router** for navigation
- **Heroicons** for consistent iconography

## 📋 Prerequisites

- Node.js 18+ and npm
- Hugging Face API token (free)
- Google Cloud Console project with Gmail API enabled
- ChromaDB instance (optional - will fallback gracefully)

## 🛠️ Setup Instructions

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/inbox-zero-ai.git
cd inbox-zero-ai
```

### 2. Install Dependencies
```bash
# Install root dependencies
npm run install:all
```

### 3. Google OAuth Setup
1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select existing one
3. Enable the Gmail API
4. Create OAuth 2.0 credentials:
   - Application type: Web application
   - Authorized redirect URIs: `http://localhost:3000/auth/callback`
5. Copy the Client ID and Client Secret

### 4. Hugging Face API Setup
1. Visit [Hugging Face Settings](https://huggingface.co/settings/tokens)
2. Create a **FREE** API token
3. Copy the token

### 5. Environment Configuration
Create `.env` file in project root:
```env
# Server Configuration
PORT=3001
NODE_ENV=development
FRONTEND_URL=http://localhost:3000

# JWT Secret - Use a strong secret in production!
JWT_SECRET=your-super-secret-jwt-key-change-this-in-production

# Hugging Face Configuration (FREE!)
HUGGINGFACE_API_KEY=your-hugging-face-token-here

# Google OAuth Configuration
GOOGLE_CLIENT_ID=your-google-client-id-here
GOOGLE_CLIENT_SECRET=your-google-client-secret-here
GOOGLE_REDIRECT_URI=http://localhost:3000/auth/callback

# ChromaDB Configuration (optional)
CHROMA_DB_PATH=http://localhost:8000

# Logging
LOG_LEVEL=info
```

### 6. Start ChromaDB (Optional)
If you want tone personalization features:
```bash
# Using Docker
docker run -p 8000:8000 chromadb/chroma

# Or install locally
pip install chromadb
chroma run --host localhost --port 8000
```

### 7. Run the Application
```bash
# Development mode (runs both frontend and backend)
npm run dev

# Or run separately
npm run dev:server  # Backend on port 3001
npm run dev:client  # Frontend on port 3000
```

### 8. Access the Application
Open [http://localhost:3000](http://localhost:3000) and sign in with your Google account.

## 🔧 Production Deployment

### 1. Build the Application
```bash
npm run build
```

### 2. Environment Variables
Update your production environment variables:
- Use a strong JWT secret
- Set NODE_ENV=production
- Configure proper CORS origins
- Use production database URLs

### 3. Start Production Server
```bash
npm start
```

## 📊 Usage Guide

### Getting Started
1. **Sign In**: Use Google OAuth to connect your Gmail account
2. **Email Processing**: The app automatically fetches and processes your recent emails
3. **Dashboard**: View your email overview, analytics, and recent activity
4. **Categories**: Navigate through different email categories using the sidebar

### Working with Emails
- **View Summaries**: Each email shows an AI-generated summary highlighting key points
- **Action Items**: See extracted tasks with assignee information and priority levels
- **Reply Suggestions**: Use AI-generated replies or modify them to match your style
- **One-Click Actions**: Mark action items as done, send replies, or copy text

### Analytics & Improvement
- **Rate Content**: Provide feedback on summary and action item quality
- **Track Progress**: Monitor time saved and productivity improvements
- **View Trends**: Understand your email patterns and categories

## 🎯 Key Features in Detail

### Smart Email Summarization
- Analyzes entire email threads, not just individual messages
- Identifies key participants and their roles
- Extracts main discussion points and decisions made
- Provides clear, professional summaries in 2-3 sentences

### Action Item Extraction
- Uses advanced NLP to identify actionable tasks
- Determines task assignee (you vs. others)
- Assigns priority levels (low, medium, high)
- Formats as clear, checkable items

### Intelligent Reply Generation
- Considers thread context and conversation tone
- Matches sender's communication style
- Addresses questions and requests appropriately
- Learns from your past emails for personalization

### Auto-Categorization System
- **FYI**: Informational emails requiring no action
- **Action Needed**: Emails requiring specific responses or tasks
- **Calendar/Meeting**: Scheduling and meeting-related emails
- **Invoice/Finance**: Financial matters and billing
- **Spam/Ignore**: Low-priority or promotional content

### Tone Personalization Engine
- Analyzes your sent emails to understand communication patterns
- Creates embeddings of your writing style
- Adjusts future suggestions to match your tone
- Continuously improves with more data

## 🔒 Security & Privacy

- **OAuth 2.0**: Secure Google authentication without storing passwords
- **JWT Tokens**: Stateless authentication with configurable expiration
- **Data Encryption**: Sensitive data encrypted in transit and at rest
- **Minimal Permissions**: Only requests necessary Gmail scopes
- **Local Processing**: Email content processed securely on your infrastructure

## 🚧 Development

### Project Structure
```
inbox-zero-ai/
├── server/                 # Backend application
│   ├── src/
│   │   ├── database/      # Database models and setup
│   │   ├── middleware/    # Express middleware
│   │   ├── routes/        # API route handlers
│   │   ├── services/      # Business logic services
│   │   └── utils/         # Utility functions
│   ├── package.json
│   └── tsconfig.json
├── client/                 # Frontend application
│   ├── src/
│   │   ├── components/    # React components
│   │   ├── contexts/      # React contexts
│   │   ├── pages/         # Page components
│   │   ├── services/      # API services
│   │   └── types/         # TypeScript types
│   ├── package.json
│   └── tsconfig.json
└── package.json           # Root package.json
```

### Available Scripts
```bash
npm run dev              # Run both frontend and backend in development
npm run dev:server       # Run backend only
npm run dev:client       # Run frontend only
npm run build           # Build both applications for production
npm run start           # Start production server
npm run install:all     # Install all dependencies
```

### API Endpoints
- `GET /api/auth/google` - Get Google OAuth URL
- `POST /api/auth/google/callback` - Handle OAuth callback
- `GET /api/emails` - Fetch user emails
- `GET /api/emails/category/:category` - Get emails by category
- `POST /api/emails/reply` - Send email reply
- `GET /api/analytics/dashboard` - Get analytics overview
- `POST /api/analytics/feedback` - Submit user feedback

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgements

- Hugging Face for providing free AI models via their Inference API
- Google for Gmail API access
- The open-source community for excellent tools and libraries

## 📞 Support

If you encounter any issues or have questions:
1. Check the [Issues](https://github.com/your-username/inbox-zero-ai/issues) page
2. Create a new issue with detailed information
3. Join our community discussions

---

Built with ❤️ using modern web technologies to help you achieve inbox zero and boost productivity! 