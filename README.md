# T⚬D⚬ - Vue.js Todo Application

A modern, responsive todo list application built with Vue.js 2 and Firebase, featuring real-time data synchronization, elegant UI with custom styling, and a smooth user experience.

## 📋 Overview

T⚬D⚬ is a full-featured task management application that allows users to create, edit, complete, and delete tasks with real-time cloud synchronization. The application features a minimalist black theme with colorful accents, custom checkboxes, and responsive design optimized for both desktop and mobile devices.

## ✨ Features

- **Create Tasks**: Add new tasks with a simple input field
- **Edit Tasks**: Click on any task to edit its content inline
- **Complete Tasks**: Mark tasks as completed with custom-styled checkboxes
- **Delete Tasks**: Remove tasks with a single click
- **Sort Tasks**: Alphabetically sort tasks using the sort button
- **Real-time Sync**: All tasks are synchronized with Firebase Firestore in real-time
- **Timestamps**: Each task displays when it was created
- **Responsive Design**: Fully responsive layout that works on desktop and mobile devices
- **Loading State**: Smooth loading animation while fetching data from Firebase
- **Empty State**: User-friendly message when no tasks exist
- **Persistent Storage**: Tasks are stored in Firebase and persist across sessions

## 🛠️ Technology Stack

### Frontend
- **Vue.js 2.6.11**: Progressive JavaScript framework for building user interfaces
- **Vue UUID 1.1.1**: For generating unique task identifiers
- **Axios 0.19.2**: HTTP client for making API requests
- **Awesome Bootstrap Checkbox 1.0.1**: Enhanced checkbox styling

### Backend & Database
- **Firebase 7.14.5**: Backend-as-a-Service platform
  - Firestore: NoSQL cloud database for storing tasks
  - Real-time synchronization
  - Cloud hosting capabilities

### Build Tools & Development
- **Vue CLI 4.3.0**: Standard tooling for Vue.js development
- **Babel**: JavaScript compiler for ES6+ compatibility
- **ESLint**: Linting utility for code quality
- **Webpack**: Module bundler (via Vue CLI)

## 📁 Project Structure

```
putanameto/
├── public/
│   ├── index.html          # Main HTML file
│   └── favicon.ico         # Application icon
├── src/
│   ├── assets/
│   │   ├── loader.gif      # Loading animation
│   │   └── vue-todo-app.png # App screenshot
│   ├── components/
│   │   ├── TodoComponent.vue  # Main todo container component
│   │   └── TodoList.vue       # Todo list display component
│   ├── App.vue             # Root Vue component
│   ├── main.js             # Application entry point
│   └── firestore.js        # Firebase configuration
├── babel.config.js         # Babel configuration
├── package.json            # Project dependencies and scripts
└── README.md              # Project documentation
```

## 🚀 Installation and Setup

### Prerequisites

- Node.js (version 12.x or higher recommended)
- npm (comes with Node.js)
- A Firebase account and project

### Step 1: Clone the Repository

```bash
git clone https://github.com/pappater/putanameto.git
cd putanameto
```

### Step 2: Install Dependencies

```bash
npm install
```

This will install all required packages listed in `package.json`, including Vue.js, Firebase, and development tools.

### Step 3: Firebase Configuration

The application is pre-configured with a Firebase project. If you want to use your own Firebase project:

1. Create a new Firebase project at [Firebase Console](https://console.firebase.google.com/)
2. Enable Firestore Database in your project
3. Get your Firebase configuration from Project Settings
4. Update the configuration in `src/firestore.js`:

```javascript
var firebaseConfig = {
    apiKey: "YOUR_API_KEY",
    authDomain: "YOUR_AUTH_DOMAIN",
    databaseURL: "YOUR_DATABASE_URL",
    projectId: "YOUR_PROJECT_ID",
    storageBucket: "YOUR_STORAGE_BUCKET",
    messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
    appId: "YOUR_APP_ID",
    measurementId: "YOUR_MEASUREMENT_ID"
};
```

5. In Firestore, create a collection named `to-do` (it will be created automatically when you add your first task)

### Step 4: Run the Application

```bash
npm run serve
```

The application will start on `http://localhost:8080` (or another port if 8080 is busy).

## 📱 Usage Guide

### Adding a Task
1. Type your task in the input field at the bottom
2. Press Enter or click outside the input field to save
3. The task will be added to the list and saved to Firebase

### Editing a Task
1. Click on any task text to enter edit mode
2. Modify the text as needed
3. Press Enter or click outside to save changes

### Completing a Task
1. Click the checkbox next to a task to mark it as complete
2. Completed tasks will have a strikethrough style
3. The completion status is saved to Firebase

### Deleting a Task
1. Click the red "x" button on the right side of any task
2. The task will be removed from both the UI and Firebase

### Sorting Tasks
1. Click the up arrow (△) in the header
2. Tasks will be sorted alphabetically

## 🔧 Available Scripts

### Development Server
```bash
npm run serve
```
Compiles and hot-reloads for development. The app will be available at `http://localhost:8080`.

### Production Build
```bash
npm run build
```
Compiles and minifies for production. Output will be in the `dist/` directory.

### Linting
```bash
npm run lint
```
Lints and fixes files using ESLint with Vue.js specific rules.

## 🎨 Component Architecture

### App.vue
The root component that wraps the entire application and imports the main TodoComponent.

### TodoComponent.vue
The main container component that:
- Manages application state
- Handles Firebase operations (CRUD)
- Implements sorting logic
- Displays loading state
- Passes data to TodoList component via props
- Receives events from TodoList component

### TodoList.vue
The presentation component that:
- Displays the list of tasks
- Handles user interactions (edit, delete, complete)
- Emits events to parent component
- Shows empty state when no tasks exist

## 🔐 Firebase Integration

The application uses Firebase Firestore for data persistence with the following operations:

### Create
New tasks are added to the `to-do` collection with a unique ID generated using UUID v1.

### Read
Tasks are fetched on component mount and displayed in the list.

### Update
Tasks can be updated in three ways:
- Marking as complete/incomplete
- Editing task text
- Changing edit mode

### Delete
Tasks are removed from both local state and Firebase collection.

### Data Structure
Each task in Firestore has the following structure:
```javascript
{
  id: "uuid-v1-string",
  task: "Task description",
  isCompleted: false,
  edit: true,
  time: "MM/DD/YYYY, HH:MM:SS AM/PM"
}
```

## 📱 Responsive Design

The application includes media queries for screens less than 700px wide, optimizing the layout for mobile devices with:
- Adjusted font sizes
- Responsive container widths
- Modified spacing and positioning
- Hidden decorative elements on small screens

## 🎨 Styling

- **Color Scheme**: Dark theme with colorful accents
  - Background: Black (#000000)
  - Text: Light gray (#DDDDDD)
  - Accents: Red (#EA5455), Green (#158467), Blue (#07689F), Orange (#F0A500)
- **Typography**: Avenir, Helvetica, Arial, sans-serif
- **Custom Components**: Hand-styled checkboxes and input fields
- **Visual Elements**: Decorative borders and dividers

## 🚀 Deployment

### Building for Production
```bash
npm run build
```

This creates an optimized production build in the `dist/` directory.

### Deployment Options

1. **Firebase Hosting**
   ```bash
   npm install -g firebase-tools
   firebase login
   firebase init
   firebase deploy
   ```

2. **Netlify**
   - Connect your GitHub repository
   - Set build command: `npm run build`
   - Set publish directory: `dist`

3. **Vercel**
   - Import your GitHub repository
   - Vercel will auto-detect Vue.js settings

4. **GitHub Pages**
   - Build the project
   - Deploy the `dist/` folder to gh-pages branch

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is open source and available for personal and commercial use.

## 🐛 Troubleshooting

### Port Already in Use
If port 8080 is already in use, Vue CLI will automatically try the next available port.

### Firebase Connection Issues
- Check that your Firebase configuration in `src/firestore.js` is correct
- Ensure Firestore is enabled in your Firebase Console
- Verify that your Firestore security rules allow read/write access

### Build Errors
- Delete `node_modules` and `package-lock.json`
- Run `npm install` again
- Clear npm cache: `npm cache clean --force`

## 📞 Support

For issues, questions, or contributions, please use the GitHub repository's issue tracker.

## 🔗 Additional Resources

- [Vue.js Documentation](https://vuejs.org/)
- [Firebase Documentation](https://firebase.google.com/docs)
- [Vue CLI Documentation](https://cli.vuejs.org/)
- [Firestore Documentation](https://firebase.google.com/docs/firestore)
