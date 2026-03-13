# School Management System

A modern, responsive web application for managing school data with role-based access control.

## Features

- **Authentication System**: Secure login for Admin, Teachers, and Students
- **Dashboard**: Overview of students, teachers, and classes
- **Class Management**: View all classes (Nursery to Class 10) with student and teacher assignments
- **Admin Controls**: Full CRUD operations for students and teachers
- **Role-based Access**: Different interfaces for different user types
- **Modern UI**: Clean, responsive design with Tailwind CSS

## Tech Stack

- **Frontend**: Next.js 15 with App Router, TypeScript, Tailwind CSS
- **Backend**: Next.js API Routes
- **Database**: SQLite with Prisma ORM
- **Authentication**: NextAuth.js with credentials provider
- **Styling**: Tailwind CSS

## Quick Start

### Prerequisites

- Node.js 18+ 
- npm or yarn

### Installation

1. **Clone and install dependencies:**
   ```bash
   cd web
   npm install
   ```

2. **Set up environment variables:**
   ```bash
   # Copy the example env file
   cp src/env.example .env
   ```

3. **Set up the database:**
   ```bash
   # Generate Prisma client
   npx prisma generate
   
   # Push schema to database
   npx prisma db push
   ```

4. **Seed the database:**
   ```bash
   # Run the seeding script
   npx tsx scripts/seed.ts
   ```

5. **Start the development server:**
   ```bash
   npm run dev
   ```

6. **Open your browser:**
   Navigate to [http://localhost:3000](http://localhost:3000)

## Default Login Credentials

After running the seed script, you can log in with:

- **Email/Username**: `admin` or `admin@example.com`
- **Password**: `admin123`
- **Role**: Admin (full access)

## Usage Guide

### For Administrators

1. **Login** with admin credentials
2. **Dashboard** shows overview of all data
3. **Manage Students**: Add, edit, remove students and assign classes
4. **Manage Teachers**: Add, edit, remove teachers and assign to classes
5. **Manage Classes**: View class details and assignments

### For Teachers

1. **Login** with teacher credentials (to be added)
2. **Dashboard** shows assigned classes and students
3. **View Class Details**: See students in each assigned class

### For Students

1. **Login** with student credentials (to be added)
2. **Dashboard** shows personal information and class details
3. **View Profile**: Access personal details and academic information

## Database Schema

### Core Models

- **User**: Authentication and role management
- **Student**: Student information with class assignment
- **Teacher**: Teacher information with class assignments
- **Class**: Class levels from Nursery to Class 10
- **ClassTeacher**: Many-to-many relationship between teachers and classes

### Optional Features

- **Attendance**: Track student attendance
- **Fees**: Manage fee collection and payments
- **Announcements**: School-wide or class-specific announcements

## API Endpoints

- `POST /api/auth/signin` - User authentication
- `GET /api/classes` - Get all classes with details
- `POST /api/dev/seed` - Seed admin user
- `POST /api/seed-classes` - Seed class data

## Development

### Project Structure

```
src/
├── app/                    # Next.js App Router
│   ├── (auth)/            # Authentication pages
│   ├── admin/             # Admin-only pages
│   ├── api/               # API routes
│   ├── classes/           # Class-related pages
│   └── dashboard/         # Dashboard pages
├── lib/                   # Utility functions
├── types/                 # TypeScript type definitions
└── generated/             # Generated Prisma client
```

### Adding New Features

1. **Database Changes**: Update `prisma/schema.prisma` and run `npx prisma db push`
2. **API Routes**: Add new routes in `src/app/api/`
3. **Pages**: Create new pages in appropriate directories
4. **Components**: Add reusable components as needed

### Database Management

```bash
# View database in Prisma Studio
npx prisma studio

# Reset database
npx prisma db push --force-reset

# Generate new migration
npx prisma migrate dev --name <migration-name>
```

## Deployment

### Environment Variables

Set these in production:

```env
DATABASE_URL="your-database-url"
NEXTAUTH_SECRET="your-secret-key"
NEXTAUTH_URL="your-domain"
```

### Build and Deploy

```bash
npm run build
npm start
```

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

This project is open source and available under the MIT License.
