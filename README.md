# Product Management API

This is a simple Product Management API built with Node.js, Express.js, and MongoDB. The API allows you to perform CRUD operations on products, as well as search, filter, and sort them.

## Features

- **Create, Read, Update, and Delete (CRUD) operations on products.**
- **Search products by name or category**
- **Filter products by category and price range.**
- **Sort products by price in ascending or descending order.**

## Technologies Used

- Node.js
- Express.js
- MongoDB with Mongoose
- dotenv for environment variables
- CORS for Cross-Origin Resource Sharing

## Setup

### Prerequisites

- Node.js and npm installed on your machine
- MongoDB installed and running locally or accessible via a cloud service

### Installation

1. Clone the repository:

    ```bash
    git clone https://github.com/sabrinara/FitFlex-server.git
    ```

2. Change directory into the project:

    ```bash
    cd product-management-api
    ```

3. Install the dependencies:

    ```bash
    npm install
    ```

4. Create a `.env` file in the root directory and add your environment variables:

    ```plaintext
    PORT=5000
    MONGODB_URI=mongodb://localhost:27017/yourdatabase
    ```

5. Start the server:

    ```bash
    npm run dev
    ```

6. Your server should now be running at `http://localhost:5000`.

## API Endpoints

### 1. **Add a Product**

   - **Endpoint:** `POST /api/products`
   - **Description:** Adds a new product to the database.
   - **Request Body Example:**

     ```json
     {
       "name": "Adjustable Dumbbell Set",
       "category": [ "Fitness Equipment", "Strength Training", "Dumbbells"],
       "price": 199.99,
       "quantity": 15,
       "description": "This adjustable dumbbell set includes multiple weights and allows for easy adjustment, perfect for both beginner and advanced users. The ergonomic design ensures comfort and safety during intense workouts.",
       "image": "https://images.unsplash.com/photo-1562771242-a02d9090c90c?q=80&w=1471&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
     }
     ```

   - **Response Example:**

     ```json
       {
        "_id": "66efbf2b0386dc7577fe3f42",
        "name": "Adjustable Dumbbell Set",
        "image": "https://images.unsplash.com/photo-1562771242-a02d9090c90c?q=80&w=1471&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
        "category": [
            "Fitness Equipment",
            "Strength Training",
            "Dumbbells"
        ],
        "price": 199.99,
        "quantity": 15,
        "description": "This adjustable dumbbell set includes multiple weights and allows for easy adjustment, perfect for both beginner and advanced users. The ergonomic design ensures comfort and safety during intense workouts.",
        "createdAt": "2024-09-22T06:54:35.416Z",
        "__v": 0
       }
     ```

### 2. **Get All Products**

   - **Endpoint:** `GET /api/products`
   - **Description:** Retrieves all products, with optional search, filter, and sort options.
   - **Query Parameters:**

     - `search`: (optional) Search products by name.
     - `categories`: (optional) Filter by categories, comma-separated.
     - `minPrice`: (optional) Minimum price for filtering.
     - `maxPrice`: (optional) Maximum price for filtering.
     - `sortBy`: (optional) Field to sort by (e.g., `price`).
     - `sortOrder`: (optional) Sort order, `asc` for ascending or `desc` for descending.

   - **Example Request:**

     ```plaintext
     GET /api/products?search=Dumbbell&categories=Fitness&minPrice=1&maxPrice=100&sortBy=price&sortOrder=asc
     ```

   - **Response Example:**

     ```json
     [
       {
        "_id": "66efbf2b0386dc7577fe3f42",
        "name": "Adjustable Dumbbell Set",
        "image": "https://images.unsplash.com/photo-1562771242-a02d9090c90c?q=80&w=1471&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
        "category": [
            "Fitness Equipment",
            "Strength Training",
            "Dumbbells"
        ],
        "price": 199.99,
        "quantity": 15,
        "description": "This adjustable dumbbell set includes multiple weights and allows for easy adjustment, perfect for both beginner and advanced users. The ergonomic design ensures comfort and safety during intense workouts.",
        "createdAt": "2024-09-22T06:54:35.416Z",
        "__v": 0
     }
     ]
     ```

### 3. **Get a Single Product by ID**

   - **Endpoint:** `GET /api/products/:id`
   - **Description:** Retrieves a single product by its ID.
   - **Example Request:**

     ```plaintext
     GET /api/products/66efbf2b0386dc7577fe3f42
     ```

   - **Response Example:**

     ```json
      {
        "_id": "66efbf2b0386dc7577fe3f42",
        "name": "Adjustable Dumbbell Set",
        "image": "https://images.unsplash.com/photo-1562771242-a02d9090c90c?q=80&w=1471&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
        "category": [
            "Fitness Equipment",
            "Strength Training",
            "Dumbbells"
        ],
        "price": 199.99,
        "quantity": 15,
        "description": "This adjustable dumbbell set includes multiple weights and allows for easy adjustment, perfect for both beginner and advanced users. The ergonomic design ensures comfort and safety during intense workouts.",
        "createdAt": "2024-09-22T06:54:35.416Z",
        "__v": 0
     }
     ```

### 4. **Update a Product**

   - **Endpoint:** `PUT /api/products/:id`
   - **Description:** Updates an existing product by its ID.
   - **Request Body Example:**

     ```json
     {
       "name": "Treade Mill For Home",
       "category": [
        "Fitness Equipment",
        "Running",
        "Trade Mill"
        ],
        "price": 599.99,
        "quantity": 10,
        "description": "A compact and foldable treadmill, perfect for home workouts. Features adjustable speed settings, a built-in heart rate monitor, and an LCD display for tracking your progress.",
        "image": "https://images.unsplash.com/photo-1637666218229-1fe0a9419267?q=80&w=1470&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
     }
     ```

   - **Response Example:**

     ```json
     {
       "name": "Trade Mill For Home",
       "image": "https://images.unsplash.com/photo-1637666218229-1fe0a9419267?q=80&w=1470&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
       "category": [ "Fitness Equipment", "Running", "Treade Mill"],
       "price": 599.99,
       "quantity": 10,
       "description": "A compact and foldable treadmill, perfect for home workouts. Features adjustable speed settings, a built-in heart rate monitor, and an LCD display for tracking your progress.",
       "_id": "66efbca86b0eac6332f02387",
       "createdAt": "2024-09-22T06:43:52.591Z",
       "__v": 0
     }
     ```

### 5. **Delete a Product**

   - **Endpoint:** `DELETE /api/products/:id`
   - **Description:** Deletes a product by its ID.
   - **Example Request:**

     ```plaintext
     DELETE /api/products/60c72b2f9b1e8a1b0c8fbcf1
     ```

   - **Response Example:**

     ```json
     {
       "message": "Product deleted"
     }
     ```

### 6. **Get Products by Category**

   - **Endpoint:** `GET /api/products/category/:category`
   - **Description:** Retrieves all products in a specific category.
   - **Example Request:**

     ```plaintext
     GET /api/products/category/Fitness
     ```

   - **Response Example:**

     ```json
     [
        {
        "_id": "66efbb6f8351c3d90a88a193",
        "name": "Treade Mill For Home",
        "image": "https://images.unsplash.com/photo-1649068618811-9f3547ef98fc?q=80&w=1470&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
        "category": [
            "Fitness Equipment",
            "Running",
            "Trade Mill"
        ],
        "price": 599.99,
        "quantity": 12,
        "description": "A compact and foldable treadmill, perfect for home workouts. Features adjustable speed settings, a built-in heart rate monitor, and an LCD display for tracking your progress.",
        "createdAt": "2024-09-22T06:38:39.423Z",
        "__v": 0
        },
        {
        "_id": "66efbf2b0386dc7577fe3f42",
        "name": "Adjustable Dumbbell Set",
        "image": "https://images.unsplash.com/photo-1562771242-a02d9090c90c?q=80&w=1471&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
        "category": [
            "Fitness Equipment",
            "Strength Training",
            "Dumbbells"
        ],
        "price": 199.99,
        "quantity": 15,
        "description": "This adjustable dumbbell set includes multiple weights and allows for easy adjustment, perfect for both beginner and advanced users. The ergonomic design ensures comfort and safety during intense workouts.",
        "createdAt": "2024-09-22T06:54:35.416Z",
        "__v": 0
        }
     ]
     ```

## Notes

- Ensure MongoDB is running locally or use a cloud MongoDB service.
- The API supports searching, filtering, and sorting, which can be combined to refine product queries.

---

This `README.md` file should provide comprehensive information for users and developers to understand and use your Product Management API effectively.
