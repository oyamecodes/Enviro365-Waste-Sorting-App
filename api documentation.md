# Waste Management API Documentation

## Table of Contents
- [Waste Categories](#waste-categories)
- [Disposal Guidelines](#disposal-guidelines)
- [Recycling Tips](#recycling-tips)

## Waste Categories

### Resource: WasteCategory

#### Fields

id: Long             // Auto-generated primary key

name: String         // Category name (2-50 chars)

code: String         // 4 uppercase letters

description: String  // Category description

#### Endpoints

##### List All Categories

```http
GET /api/waste-categories
```

**Response** (200 OK):
```json
[
  {
    "id": 1,
    "name": "Plastic",
    "code": "PLST",
    "description": "All types of plastic waste including bottles, containers, and packaging"
  }
]
```

##### Get Single Category

```http
GET /api/waste-categories/{id}
```

**Response** (200 OK):
```json
{
  "id": 1,
  "name": "Plastic",
  "code": "PLST",
  "description": "All types of plastic waste including bottles, containers, and packaging"
}
```

##### Create Category

```http
POST /api/waste-categories
Content-Type: application/json
```

**Request Body:**
```json
{
  "name": "Electronics",
  "code": "ELEC",
  "description": "Electronic waste including phones, computers, and batteries"
}
```

**Response** (201 Created):
```json
{
  "id": 5,
  "name": "Electronics",
  "code": "ELEC",
  "description": "Electronic waste including phones, computers, and batteries"
}
```

##### Update Category

```http
PUT /api/waste-categories/{id}
Content-Type: application/json
```

**Request Body:**
```json
{
    "name": "Updated Plastic",
    "code": "PLST",
    "description": "Updated description for plastic waste"
}
```

**Response** (200 OK):
```json
{
    "id": 1,
    "name": "Updated Plastic",
    "code": "PLST",
    "description": "Updated description for plastic waste",
    "lastUpdated": "2024-02-16T12:00:00Z"
}
```

##### Delete Category

```http
DELETE /api/waste-categories/{id}
```

**Response** (204 No Content)

## Disposal Guidelines

### Resource: DisposalGuideline

#### Fields

id: Long             // Auto-generated primary key

title: String        // Guideline title

instructions: String // Detailed instructions

category: WasteCategory // Associated waste category

lastUpdated: LocalDateTime // Last update timestamp

#### Endpoints

##### List All Guidelines

```http
GET /api/disposal-guidelines
```

**Response** (200 OK):
```json
[
  {
    "id": 1,
    "title": "Plastic Recycling Guide",
    "instructions": "Clean and sort plastic items by type...",
    "categoryId": 1,
    "lastUpdated": "2024-02-16T12:00:00Z"
  }
]
```

##### Get Single Guideline

```http
GET /api/disposal-guidelines/{id}
```

**Response** (200 OK):
```json
{
    "id": 1,
    "title": "Plastic Recycling Guide",
    "instructions": "Clean and sort plastic items by type...",
    "categoryId": 1,
    "lastUpdated": "2024-02-16T12:00:00Z"
}
```

##### Create Guideline

```http
POST /api/disposal-guidelines
Content-Type: application/json
```

**Request Body:**
```json
{
    "title": "Glass Recycling Instructions",
    "instructions": "Separate glass by color and remove all caps...",
    "categoryId": 3
}
```

**Response** (201 Created):
```json
{
    "id": 2,
    "title": "Glass Recycling Instructions",
    "instructions": "Separate glass by color and remove all caps...",
    "categoryId": 3,
    "lastUpdated": "2024-02-16T12:00:00Z"
}
```

##### Update Guideline

```http
PUT /api/disposal-guidelines/{id}
Content-Type: application/json
```

**Request Body:**
```json
{
    "title": "Updated Plastic Recycling Guide",
    "instructions": "New instructions for plastic recycling...",
    "categoryId": 1
}
```

**Response** (200 OK):
```json
{
    "id": 1,
    "title": "Updated Plastic Recycling Guide",
    "instructions": "New instructions for plastic recycling...",
    "categoryId": 1,
    "lastUpdated": "2024-02-16T12:00:00Z"
}
```

##### Delete Guideline

```http
DELETE /api/disposal-guidelines/{id}
```

**Response** (204 No Content)

## Recycling Tips

### Resource: RecyclingTip

#### Fields

id: Long             // Auto-generated primary key

title: String        // Tip title

content: String      // Detailed content

applicableCategories: Set<WasteCategory> // Related categories

createdAt: LocalDateTime // Creation timestamp

lastUpdated: LocalDateTime // Last update timestamp

#### Endpoints

##### List All Tips

```http
GET /api/recycling-tips
```

**Response** (200 OK):
```json
[
  {
    "id": 1,
    "title": "Plastic Container Cleaning",
    "content": "Rinse all plastic containers before recycling...",
    "applicableCategories": ["PLST"],
    "createdAt": "2024-02-16T12:00:00Z",
    "lastUpdated": "2024-02-16T12:00:00Z"
  }
]
```

##### Get Single Tip

```http
GET /api/recycling-tips/{id}
```

**Response** (200 OK):
```json
{
    "id": 1,
    "title": "Plastic Container Cleaning",
    "content": "Rinse all plastic containers before recycling...",
    "applicableCategories": ["PLST"],
    "createdAt": "2024-02-16T12:00:00Z",
    "lastUpdated": "2024-02-16T12:00:00Z"
}
```

##### Create Tip

```http
POST /api/recycling-tips
Content-Type: application/json
```

**Request Body:**
```json
{
    "title": "Glass Sorting Guide",
    "content": "Sort glass by color to improve recycling efficiency...",
    "applicableCategories": ["GLAS"]
}
```

**Response** (201 Created):
```json
{
    "id": 2,
    "title": "Glass Sorting Guide",
    "content": "Sort glass by color to improve recycling efficiency...",
    "applicableCategories": ["GLAS"],
    "createdAt": "2024-02-16T12:00:00Z",
    "lastUpdated": "2024-02-16T12:00:00Z"
}
```

##### Update Tip

```http
PUT /api/recycling-tips/{id}
Content-Type: application/json
```

**Request Body:**
```json
{
    "title": "Updated Plastic Container Cleaning",
    "content": "Updated instructions for cleaning containers...",
    "applicableCategories": ["PLST", "GLAS"]
}
```

**Response** (200 OK):
```json
{
    "id": 1,
    "title": "Updated Plastic Container Cleaning",
    "content": "Updated instructions for cleaning containers...",
    "applicableCategories": ["PLST", "GLAS"],
    "lastUpdated": "2024-02-16T12:00:00Z"
}
```

##### Delete Tip

```http
DELETE /api/recycling-tips/{id}
```

**Response** (204 No Content)
