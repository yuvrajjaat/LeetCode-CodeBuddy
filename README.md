# LeetCode Buddy Browser Extension

## Overview
LeetCode Buddy is a browser extension designed to enhance your coding journey by integrating with LeetCode. It features a well-structured backend and frontend for efficient management of user data, institutes, and friend lists.

This project includes:
- A **client** folder containing the frontend built using **Next.js** and **TypeScript**.
- A **server** folder containing the backend developed with **Node.js**, **Express**, and **MongoDB**.

---

## Tech Stack

### Frontend
- **Next.js**: Framework for server-side rendering and static site generation.
- **TypeScript**: For type-safe development.
- **Tailwind CSS**: For styling the user interface.
- **React Icons**: For intuitive icons in the navigation bar.

### Backend
- **Node.js**: JavaScript runtime for building the server-side logic.
- **Express.js**: Framework for creating REST APIs.
- **MongoDB**: NoSQL database for storing user, friend, and institute data.

---

## Folder Structure

### Client
- **src/components**
  - **auth**: Contains components like `LoginForm.tsx` and `SignupForm.tsx`.
  - **common**: Shared components like `Navbar.tsx` and `Appbar.tsx`.
  - **friends**: Components related to friends, such as `FriendList.tsx`.
  - **institute**: Components for institute-related features, such as `InstitutePage.tsx`.
  - **home**: Profile and onboarding components.
- **pages**: Contains route files for the app.
- **styles**: Global styles.
- **hooks, mutations, contexts**: For state management and API integration.

### Server
- **models**: MongoDB schemas for `Institute.js` and `User.js`.
- **schema**: Contains GraphQL schema definitions.
  - **mutation**: For creating/updating data.
  - **query**: For retrieving data.
  - **type**: Defines GraphQL types.
- **index.js**: Entry point for the backend server.

---

## Features

1. **Profile Management**: View and edit your profile details.
2. **Friend Management**: Add and view friends.
3. **Institute Management**: Manage institutes and their details.

---

## Getting Started

Follow these steps to run the project locally:

### Prerequisites
Make sure you have the following installed:
- **Node.js** (v16 or higher)
- **npm** or **yarn**
- **MongoDB**

### Steps

1. **Clone the Repository**
```bash
git clone <repository-url>
cd leetcode-buddy
```

2. **Setup Backend**
- Navigate to the `server` folder.
- Create a `.env` file and add the following variables:
  ```env
  MONGO_URI=<your-mongodb-connection-string>
  PORT=5000
  # Environment
  NODE_ENV=development
  ```
- Install dependencies and start the server:
  ```bash
  npm install
  npm run dev
  ```

3. **Setup Frontend**
- Navigate to the `client` folder.
- Install dependencies:
  ```bash
  npm install
  ```
- Create a production build:
  ```bash
  npm run build
  ```
- Export static files to the `out` directory:
  ```bash
  npm run export
  ```

4. **Load Extension in Browser**
- Open **Google Chrome**.
- Navigate to `chrome://extensions` in the address bar.
- Enable the **Developer Mode** toggle (found in the top-right corner).
- Click on **"Load Unpacked"**.
- Select the `out` folder generated in the `client` directory.

---

## Screenshots

1. **Profile Page**
   ![Screenshot 2025-01-20 141240](https://github.com/user-attachments/assets/db51ae75-1c18-42c9-8499-81497d4fdc0d)


2. **Friends List**
   
   ![image](https://github.com/user-attachments/assets/c924417f-359c-41ea-833f-34ee09de39ad)


3. **Institute Page**
   
   ![image](https://github.com/user-attachments/assets/2bb00c06-7b83-4e53-98b0-2b48a445eb37)


---

## How It Works  

### 1. User Flow  
- Users start by logging into the platform. Upon successful login, they are redirected to their profile page.  
- From the profile, users can manage their friends, view friend lists, and explore institutes they are associated with.  

### 2. Backend Functionality  
- The backend is built using **Node.js** with **Express** and **GraphQL**.  
- **GraphQL API**:  
  - The API is structured around a GraphQL schema that defines the types, queries, and mutations.  
  - Queries allow the client to fetch user data, friend lists, and institute details as needed.  
  - Mutations handle updates such as adding friends, updating institute logos, or editing profile information.  
- **Database Connection**:  
  - Data is stored in **MongoDB**, and GraphQL resolvers interact with the database to fetch or update records efficiently.  
  - Mongoose models (`User`, `Institute`) are used to map data and ensure consistency.  

### 3. Data Flow  
- On login, user credentials are sent to the API for verification.  
- The API validates credentials using stored data in MongoDB and generates an authentication token.  
- Once authenticated, GraphQL queries fetch user details and associated entities (like friends and institutes) and return them to the client.  

### 4. Dynamic Data Fetching  
- GraphQL queries dynamically fetch only the required fields, optimizing network usage and reducing payload size.  
- For instance:  
  - **Login**: User credentials are sent to a `/login` endpoint. On success, the token is used for all subsequent API requests.  
  - **Profile Data**: A GraphQL query like `{ user { name, email, friends } }` retrieves specific fields to populate the profile page.  
  - **Institute Data**: Queries like `{ institute { name, logo, students } }` fetch institute-specific information displayed on the UI.  

### 5. Frontend Integration  
- The frontend uses the GraphQL APIs to interact with the backend seamlessly. It sends queries and mutations via HTTP, processes the JSON responses, and dynamically updates the UI with the fetched data.  

This structure ensures a smooth and efficient flow of data between the backend and frontend, providing users with real-time updates and interaction capabilities.

---

## Contributing
Feel free to submit issues or pull requests to improve this project.

---

## Contact
For any questions or feedback, feel free to reach out to [yuvrajsogarwal@gmail.com].
