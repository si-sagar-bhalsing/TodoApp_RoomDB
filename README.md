## Components of the Architecture:

### ViewModel:

- Acts as a bridge between the UI and the data layer, ensuring data survives configuration changes.
- Interacts with the DAO to fetch or update data.
- Example method: `todoDao.getAllData()`.

### DAO (Data Access Object):

- Defines the methods for accessing the database.
- Contains methods like `getAllData()`, `addTodo()`, and `deleteTodo()`.
- These methods are used to perform database operations.
  - Example method calls:
    - `getAllData()` to retrieve all records.
    - `addTodo()` to insert a new record.
    - `deleteTodo()` to remove a record.

### Entities:

- Represents the data structure for the database.
- Annotated classes that define the schema for the database tables.
- Example Entity: `Todo` with fields `id`, `title`, and `createdAt`.

### Room Database:

- The database layer that holds the data.
- Provides the main access point to the persisted data.
- Includes a method to get the DAO, like `getDao()`.

### Data Converters:

- Used to convert data types that are not supported by SQLite (e.g., converting `Date` objects to a format SQLite can store).
- Example: `DateConverter` for converting date fields.

## Data Flow:

### Fetching Data:

- The ViewModel calls `todoDao.getAllData()` on the DAO.
- The DAO retrieves all entities from the database.
- The data is then observed by the ViewModel, which updates the UI accordingly.

### Persisting Data:

- When a new `Todo` item is added, the ViewModel calls `todoDao.addTodo()`.
- The DAO inserts the new entity into the database.
- The database updates and persists the changes.

### Updating UI:

- The ViewModel observes changes in the data and updates the UI.
- This ensures the UI is always in sync with the data stored in the database.

---
