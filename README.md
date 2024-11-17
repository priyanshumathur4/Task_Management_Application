# Task Management Web Application

This is a comprehensive task management system that empowers users to efficiently organize their tasks. The application utilizes **Spring Boot** on the backend and **MySQL** as the database.

## Features

### User Authentication
- **JWT-Based Security**: 
  - Users authenticate using **JSON Web Tokens (JWT)** for secure access.
  - JWT tokens are issued upon login and expire after a specified time (e.g., 1 hour).
  - Passwords are securely hashed before storage.

### Task Operations 
- **Add Tasks:** Users can effortlessly add new tasks to the system.
- **View Tasks:** A user-friendly interface allows for quick and easy reference to all tasks.
- **Edit Tasks:** Users have the flexibility to modify task details as needed.
- **Delete Tasks:** Unwanted tasks can be removed to keep the task list organized.
- **Mark as Complete:** Users can mark tasks as complete for effective progress tracking.

## Tech Stack
- **Server:** Java, Spring Boot  
- **Database:** MySQL
-  **Security**: JSON Web Tokens (JWT)

## Architecture
The Task Management System follows a client-server architecture. The backend is built using **Spring Boot** and handles all business logic and database operations. **MySQL** is used as the database to store task-related data.

## Modules
- **Backend:** Contains the Java and Spring Boot application responsible for handling business logic and database operations.
- **Database:** Contains the MySQL database schema and scripts for creating and managing the database.
- **Security:** Implements JWT for securing endpoints.

## Project Setup

### Backend Setup
1. Clone the repository.
2. Navigate to the backend directory.
3. Configure the MySQL database connection in `application.properties`.
4. Run the Spring Boot application using your IDE or the command line.

### Database Setup
1. Create a MySQL database.
2. Execute the database schema script provided in the database directory to create the necessary tables.
3. Update the database connection details in the backend `application.properties`.

### Postman Collection
To test the API endpoints, use the provided [Postman Collection](https://raw.githubusercontent.com/priyanshumathur4/Task_Management_Application/refs/heads/main/Task%20management.postman_collection.json). Import it into Postman to explore and interact with the API.


## API Endpoints Documentation

### Authentication Endpoints
#### 1. Register User
- **Endpoint**: `POST /api/auth/register`
- **Description**: Registers a new user.
- **Request Body**:
  ```json
  {
    "username": "gauravJwt10",
    "email": "gauravJwt10@example.com",
    "password": "12345678"
  }
- **Response Body:**
  ```json
  {
  "message": "User registered successfully"
  }

#### 2. Login User
- **Endpoint**: `POST /api/auth/login`
- **Description**:  Logs in a user and issues a JWT token.
- **Request Body**:
  ```json
  {
  "username": "gauravJwt10",
  "password": "12345678"
  }
- **Response Body:**
  ```json
  {
   "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
  }


### Task EndPoints
### 1. Create Task
- **Endpoint:** `POST /api/v1/tasks/user/{userId}`
- **Description:** Creates a new task for the specified user.
- **Request Body:**
  ```json
  {
  "task": "Complete project documentation",
  "details": "Work on API documentation",
  "completed": false,
  "taskCreatedAt": "2024-11-17"
  }
  
- **Response Body:**
   ```json
   {
    "message": "Task saved successfully",
  "data": {
    "id": 1,
    "task": "Complete project documentation",
    "details": "Work on API documentation",
    "completed": false,
    "taskCreatedAt": "Timestamp",
    "user": {
      "userId": 14,
      "username": "gauravJwt10",
      "email": "gauravJwt10@example.com"
    }
   }
  }


### 2. Get Task by ID
- **Endpoint**: GET- `GET /api/v1/tasks/{taskId}`
- **Description**: Retrieves a task by its ID.
- Response Body:
```json
{
  "message": "Found task",
  "data": {
    "id": 1,
    "task": "Complete project documentation",
    "details": "Work on API documentation",
    "completed": false,
    "taskCreatedAt": "Timestamp",
    "user": {
      "userId": 14,
      "username": "gauravJwt10",
      "email": "gauravJwt10@example.com"
    }
  }
}

```
### 3. Get All Tasks for User
- **Endpoint**: GET- `GET /api/v1/tasks/user/{userId}`
- **Description**: Retrieves all tasks for the specified user.
- Response Body:
```json

[
  {
    "id": 1,
    "task": "Complete project documentation",
    "details": "Work on API documentation",
    "completed": false,
    "taskCreatedAt": "Timestamp",
    "user": {
      "userId": 14,
      "username": "gauravJwt10",
      "email": "gauravJwt10@example.com"
    }
  }
]

```
### 4. Update Task
- **Endpoint**: PUT- `PUT /api/v1/tasks/{taskId}`
- **Description**: Updates the details of a task.
- Request Body:
```json

{
  "task": "Update API Documentation",
  "details": "Work on updating the API documentation",
  "completed": true
}
```
- Response Body:
```json

{
 "message": "Task updated successfully",
  "data": {
    "id": 1,
    "task": "Update API Documentation",
    "details": "Work on updating the API documentation",
    "completed": true,
    "taskCreatedAt": "Timestamp",
    "user": {
      "userId": 14,
      "username": "gauravJwt10",
      "email": "gauravJwt10@example.com"
    }
  }
}

```

### 5. Delete Task
- **Endpoint**: DELETE- `DELETE /api/v1/tasks/{taskId}`
- **Description**: Deletes a task by its ID.
- Response Body:
```json

{
  "message": "Task deleted successfully"
}

```
