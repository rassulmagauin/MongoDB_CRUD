

```markdown
# Movie API

This is a simple Movie API implemented in Go. It provides CRUD (Create, Read, Update, Delete) operations for movies using MongoDB as the database.

## Installation

To use this API, make sure you have Go installed on your machine and a MongoDB server running.

1. Clone the repository:
   ```shell
   git clone https://github.com/your-username/movie-api.git
   ```
2. Change to the project directory:
   ```shell
   cd movie-api
   ```
3. Install the required dependencies:
   ```shell
   go mod download
   ```
4. Start the API server:
   ```shell
   go run main.go
   ```

The API server will start running on `http://127.0.0.1:8000`.

## API Endpoints

### Get Movie

Retrieves a movie by its ID.

- **URL:** `/v1/movies/{id}`
- **Method:** `GET`
- **URL Parameters:**
  - `id`: The ID of the movie to retrieve
- **Response:**
  - `200 OK`: Movie details in JSON format
  - `404 Not Found`: If the movie with the specified ID does not exist
  - `500 Internal Server Error`: If an error occurs

### Create Movie

Creates a new movie.

- **URL:** `/v1/movies`
- **Method:** `POST`
- **Request Body:** Movie details in JSON format
- **Response:**
  - `200 OK`: Newly created movie details in JSON format
  - `400 Bad Request`: If the request body is invalid
  - `500 Internal Server Error`: If an error occurs

### Update Movie

Updates an existing movie.

- **URL:** `/v1/movies/{id}`
- **Method:** `PUT`
- **URL Parameters:**
  - `id`: The ID of the movie to update
- **Request Body:** Movie details in JSON format
- **Response:**
  - `200 OK`: If the movie is updated successfully
  - `404 Not Found`: If the movie with the specified ID does not exist
  - `500 Internal Server Error`: If an error occurs

### Delete Movie

Deletes a movie.

- **URL:** `/v1/movies/{id}`
- **Method:** `DELETE`
- **URL Parameters:**
  - `id`: The ID of the movie to delete
- **Response:**
  - `200 OK`: If the movie is deleted successfully
  - `404 Not Found`: If the movie with the specified ID does not exist
  - `500 Internal Server Error`: If an error occurs

## Data Model

The API works with the following data model:

```go
type Movie struct {
    ID        primitive.ObjectID `json:"id" bson:"_id,omitempty"`
    Name      string             `json:"name" bson:"name"`
    Year      string             `json:"year" bson:"year"`
    Directors []string           `json:"directors" bson:"directors"`
    Writers   []string           `json:"writers" bson:"writers"`
    BoxOffice BoxOffice          `json:"boxOffice" bson:"boxOffice"`
}

type BoxOffice struct {
    Budget uint64 `json:"budget" bson:"budget"`
    Gross  uint64 `json:"gross" bson:"gross"`
}
```

## Dependencies

This API uses the following dependencies:

- `github.com/gorilla/mux`: A powerful URL router and dispatcher for Go.
- `go.mongodb.org/mongo-driver`: The official MongoDB driver for Go.


