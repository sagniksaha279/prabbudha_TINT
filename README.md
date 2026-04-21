# PRABUDDHA 2026 - Tech Fest Website

A complete, responsive full-stack web application for managing a tech festival with user registration, event management, and admin functionality.

## Features

### Frontend
- ✅ Modern, responsive homepage with countdown timer
- ✅ Event browsing with category filtering and search
- ✅ Multi-step registration form with validation
- ✅ Contact/Query submission system with FAQ
- ✅ About page with event highlights
- ✅ Mobile-friendly design
- ✅ Smooth animations and transitions

### Backend
- ✅ Node.js/Express API server
- ✅ Full CRUD operations for users, events, registrations, and queries
- ✅ Input validation and error handling
- ✅ RESTful API endpoints
- ✅ Admin authentication and dashboard

### Database
- ✅ MySQL database with proper schema
- ✅ Tables for Users, Events, Registrations, Queries, FAQ, and Admin
- ✅ Indexes for performance optimization
- ✅ Referential integrity with foreign keys

### Admin Panel
- ✅ Admin login with secure authentication
- ✅ Dashboard with statistics and recent activities
- ✅ Query management with response system
- ✅ Event and user management
- ✅ Registration tracking

## Project Structure

```
Rumpi/
├── backend/
│   ├── server.js              # Main server file
│   ├── database.js            # Database connection
│   ├── schema.sql             # Database schema
│   ├── package.json           # Dependencies
│   ├── .env.example           # Environment variables example
│   ├── middleware/
│   │   └── validation.js      # Input validation & auth
│   └── routes/
│       ├── users.js           # User endpoints
│       ├── events.js          # Event endpoints
│       ├── registrations.js   # Registration endpoints
│       ├── queries.js         # Query endpoints
│       └── admin.js           # Admin endpoints
└── frontend/
    ├── index.html             # Homepage
    ├── about.html             # About page
    ├── events.html            # Events page
    ├── registration.html      # Registration page
    ├── contact.html           # Contact/Query page
    ├── admin.html             # Admin panel
    ├── css/
    │   ├── style.css          # Main styles
    │   ├── responsive.css     # Responsive styles
    │   └── admin.css          # Admin panel styles
    └── js/
        ├── api.js             # API wrapper
        ├── countdown.js       # Countdown timer
        ├── navbar.js          # Navigation
        ├── home.js            # Homepage
        ├── events.js          # Events page logic
        ├── registration.js    # Registration logic
        ├── contact.js         # Contact page logic
        └── admin.js           # Admin panel logic
```

## Setup Instructions

### Prerequisites
- Node.js (v14 or higher)
- MySQL (v5.7 or higher)
- npm (comes with Node.js)
- Modern web browser

### 1. Database Setup

1. Open MySQL client:
```bash
mysql -u root -p
```

2. Run the schema file:
```bash
source backend/schema.sql
```

Or copy and paste the contents of `backend/schema.sql` directly into MySQL client.

3. Verify tables are created:
```bash
SHOW TABLES FROM prabuddha_2026;
```

### 2. Backend Setup

1. Navigate to backend directory:
```bash
cd Rumpi/backend
```

2. Install dependencies:
```bash
npm install
```

3. Create `.env` file from `.env.example`:
```bash
cp .env.example .env
```

4. Edit `.env` with your MySQL credentials:
```env
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_password
DB_NAME=prabuddha_2026
DB_PORT=3306
PORT=5000
NODE_ENV=development
ADMIN_USERNAME=admin
ADMIN_PASSWORD=secure_password123
```

5. Start the server:
```bash
npm start
```

Server will run on `http://localhost:5000`

### 3. Frontend Setup

The frontend is static HTML/CSS/JS, so you can:

**Option A: Use a local server**
```bash
cd Rumpi/frontend
npx http-server
# or
python -m http.server 8000
```

**Option B: Open directly in browser**
- Open `Rumpi/frontend/index.html` in your browser

## API Endpoints

### Users
- `POST /api/users` - Register new user
- `GET /api/users` - Get all users (paginated)
- `GET /api/users/:id` - Get user by ID
- `PUT /api/users/:id` - Update user
- `DELETE /api/users/:id` - Delete user

### Events
- `GET /api/events` - Get all events
- `GET /api/events/:id` - Get event by ID
- `GET /api/events/list/categories` - Get event categories
- `POST /api/events` - Create event (admin)
- `PUT /api/events/:id` - Update event (admin)
- `DELETE /api/events/:id` - Delete event (admin)

### Registrations
- `POST /api/registrations` - Register for event
- `GET /api/registrations/user/:userId` - Get user registrations
- `GET /api/registrations/event/:eventId` - Get event registrations
- `PUT /api/registrations/:id` - Update registration status
- `DELETE /api/registrations/:id` - Cancel registration

### Queries
- `POST /api/queries` - Submit query
- `GET /api/queries` - Get all queries (admin)
- `GET /api/queries/:id` - Get query by ID
- `PUT /api/queries/:id/respond` - Respond to query (admin)
- `PUT /api/queries/:id/status` - Update query status (admin)
- `GET /api/queries/faq/all` - Get FAQ

### Admin
- `POST /api/admin/login` - Admin login
- `GET /api/admin/dashboard/stats` - Get dashboard statistics
- `GET /api/admin/dashboard/recent` - Get recent activities
- `GET /api/admin/registrations/all` - Get all registrations

## Testing the Application

### 1. Test User Registration
1. Open `http://localhost:8000/registration.html`
2. Fill in the form:
   - Name: Test User
   - Email: test@example.com
   - Phone: 9876543210
   - College: Test College
   - Year: 2nd Year
3. Select events and submit

### 2. Test Events Page
1. Open `http://localhost:8000/events.html`
2. View all events
3. Filter by category
4. Search events

### 3. Test Contact Form
1. Open `http://localhost:8000/contact.html`
2. Submit a query
3. View FAQ

### 4. Test Admin Panel
1. Open `http://localhost:8000/admin.html`
2. Login with:
   - Username: `admin`
   - Password: `secure_password123`
3. View dashboard, manage queries, events, and users

## Sample Data

To add sample events to the database:

```sql
INSERT INTO events (title, category, description, date, time, venue, max_participants, registration_fee)
VALUES 
('Code Wars', 'Coding', 'Competitive programming contest', '2026-05-01', '10:00:00', 'Hall A', 100, 0),
('Hackathon', 'Development', '24-hour hackathon event', '2026-05-02', '09:00:00', 'Hall B', 50, 200),
('AI Workshop', 'Workshop', 'Learn machine learning basics', '2026-05-03', '14:00:00', 'Lab 1', 80, 500);

INSERT INTO faq (question, answer, category, order_position)
VALUES
('When is the event?', 'PRABUDDHA 2026 is scheduled for May 1-3, 2026', 'General', 1),
('How do I register?', 'Visit the registration page and fill in your details', 'Registration', 2),
('What is the fee?', 'Most events are free. Some workshops have a nominal fee.', 'General', 3);
```

## Validation Rules

### User Registration
- **Name**: 3-100 characters
- **Email**: Valid email format
- **Phone**: 10-digit valid Indian number (6-9 as first digit)
- **College**: 3-150 characters
- **Year**: Must be selected

### Contact Query
- **Name**: Required
- **Email**: Valid email format
- **Subject**: Required
- **Message**: Minimum 10 characters

## Security Considerations

⚠️ **Production Notes:**
1. Never commit `.env` file to version control
2. Use HTTPS in production
3. Implement JWT tokens instead of simple token auth
4. Hash passwords using bcrypt
5. Add CORS restrictions
6. Implement rate limiting
7. Add email verification
8. Use environment variables for sensitive data

## Troubleshooting

### Database Connection Error
- Check MySQL is running: `mysql --version`
- Verify credentials in `.env`
- Check database exists: `SHOW DATABASES;`

### API Not Responding
- Check server is running: `npm start`
- Verify port 5000 is not in use: `netstat -ano | findstr :5000` (Windows)
- Check console for errors

### Frontend Not Loading
- Verify correct file paths
- Clear browser cache (Ctrl+Shift+Del)
- Check browser console for JavaScript errors (F12)

### CORS Issues
- Frontend and backend must be on correct hosts
- Check backend CORS configuration in `server.js`

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)
- Mobile browsers (iOS Safari, Chrome Mobile)

## Performance Optimization

- Database indexes on frequently queried fields
- Pagination for large data sets
- Lazy loading for images
- CSS minification recommended for production
- API response caching where applicable

## Future Enhancements

- Email notifications
- Payment gateway integration
- Certificate generation
- Event photos gallery
- Team registration
- Real-time notifications
- Social media integration
- Analytics dashboard

## Support & Contact

For issues and questions, contact the development team at:
- Email: dev@prabuddha2026.com
- Support: support@prabuddha2026.com

## License

This project is proprietary and for PRABUDDHA 2026 Tech Fest use only.

## Credits

Developed for PRABUDDHA 2026 - India's Premier Tech Festival

---

**Last Updated**: April 2026
**Version**: 1.0.0
