# API Documentation - User & Role Management

## Base URL
`http://localhost:3000/api/v1`

---

## User Endpoints

### 1. GET /users
**Lấy danh sách tất cả users**

```bash
curl -X GET http://localhost:3000/api/v1/users
```

**Response (200 OK):**
```json
{
  "status": "success",
  "data": [
    {
      "_id": 1,
      "username": "admin",
      "password": "admin123",
      "email": "admin@example.com",
      "fullName": "Administrator",
      "avatarUrl": "https://i.sstatic.net/l60Hf.png",
      "status": true,
      "role": 1,
      "loginCount": 5,
      "isDeleted": false,
      "timestamp": "2026-03-06T06:37:17.391Z"
    }
  ],
  "message": "Get all users successfully"
}
```

---

### 2. GET /users/:id
**Lấy thông tin user theo ID**

```bash
curl -X GET http://localhost:3000/api/v1/users/1
```

**Response (200 OK):**
```json
{
  "status": "success",
  "data": {
    "_id": 1,
    "username": "admin",
    "email": "admin@example.com",
    "fullName": "Administrator",
    "avatarUrl": "https://i.sstatic.net/l60Hf.png",
    "status": true,
    "role": 1,
    "loginCount": 5,
    "timestamp": "2026-03-06T06:37:17.391Z"
  },
  "message": "Get user successfully"
}
```

---

### 3. POST /users
**Tạo user mới**

**Request Body:**
```json
{
  "username": "john",
  "password": "john123",
  "email": "john@example.com",
  "fullName": "John Doe",
  "avatarUrl": "https://example.com/avatar.jpg",
  "role": 2,
  "status": false
}
```

**Response (201 Created):**
```json
{
  "status": "success",
  "data": {
    "_id": 2,
    "username": "john",
    "password": "john123",
    "email": "john@example.com",
    "fullName": "John Doe",
    "avatarUrl": "https://i.sstatic.net/l60Hf.png",
    "status": false,
    "role": 2,
    "loginCount": 0,
    "timestamp": "2026-03-06T06:37:32.693Z"
  },
  "message": "User created successfully"
}
```

---

### 4. PUT /users/:id
**Cập nhật thông tin user**

**Request Body:**
```json
{
  "fullName": "John Updated",
  "loginCount": 10
}
```

**Response (200 OK):**
```json
{
  "status": "success",
  "data": {
    "_id": 2,
    "username": "john",
    "email": "john@example.com",
    "fullName": "John Updated",
    "loginCount": 10,
    "timestamp": "2026-03-06T06:37:32.693Z"
  },
  "message": "User updated successfully"
}
```

---

### 5. DELETE /users/:id
**Xoá user (soft delete)**

```bash
curl -X DELETE http://localhost:3000/api/v1/users/2
```

**Response (200 OK):**
```json
{
  "status": "success",
  "message": "User deleted successfully"
}
```

---

### 6. POST /users/enable
**Kích hoạt user (set status = true)**

**Request Body:**
```json
{
  "username": "john",
  "email": "john@example.com"
}
```

**Response (200 OK):**
```json
{
  "status": "success",
  "data": {
    "_id": 2,
    "username": "john",
    "email": "john@example.com",
    "status": true,
    "timestamp": "2026-03-06T06:37:32.705Z"
  },
  "message": "User enabled successfully"
}
```

---

### 7. POST /users/disable
**Vô hiệu hoá user (set status = false)**

**Request Body:**
```json
{
  "username": "john",
  "email": "john@example.com"
}
```

**Response (200 OK):**
```json
{
  "status": "success",
  "data": {
    "_id": 2,
    "username": "john",
    "email": "john@example.com",
    "status": false,
    "timestamp": "2026-03-06T06:37:32.705Z"
  },
  "message": "User disabled successfully"
}
```

---

## Role Endpoints

### 8. GET /roles
**Lấy danh sách tất cả roles**

```bash
curl -X GET http://localhost:3000/api/v1/roles
```

**Response (200 OK):**
```json
{
  "status": "success",
  "data": [
    {
      "_id": 1,
      "name": "Admin",
      "description": "Administrator role",
      "timestamp": "2026-03-06T06:37:17.391Z"
    },
    {
      "_id": 2,
      "name": "User",
      "description": "Regular user role",
      "timestamp": "2026-03-06T06:37:17.391Z"
    }
  ],
  "message": "Get all roles successfully"
}
```

---

### 9. GET /roles/:id
**Lấy thông tin role theo ID**

```bash
curl -X GET http://localhost:3000/api/v1/roles/1
```

**Response (200 OK):**
```json
{
  "status": "success",
  "data": {
    "_id": 1,
    "name": "Admin",
    "description": "Administrator role",
    "timestamp": "2026-03-06T06:37:17.391Z"
  },
  "message": "Get role successfully"
}
```

---

### 10. POST /roles
**Tạo role mới**

**Request Body:**
```json
{
  "name": "Moderator",
  "description": "Moderator role"
}
```

**Response (201 Created):**
```json
{
  "status": "success",
  "data": {
    "_id": 3,
    "name": "Moderator",
    "description": "Moderator role",
    "timestamp": "2026-03-06T06:37:32.712Z"
  },
  "message": "Role created successfully"
}
```

---

### 11. PUT /roles/:id
**Cập nhật thông tin role**

**Request Body:**
```json
{
  "description": "Updated moderator description"
}
```

**Response (200 OK):**
```json
{
  "status": "success",
  "data": {
    "_id": 3,
    "name": "Moderator",
    "description": "Updated moderator description",
    "timestamp": "2026-03-06T06:37:32.712Z"
  },
  "message": "Role updated successfully"
}
```

---

### 12. DELETE /roles/:id
**Xoá role (soft delete)**

```bash
curl -X DELETE http://localhost:3000/api/v1/roles/3
```

**Response (200 OK):**
```json
{
  "status": "success",
  "message": "Role deleted successfully"
}
```

---

## Cấu trúc User Object

| Field | Type | Yêu cầu | Mô tả |
|-------|------|--------|-------|
| `_id` | Number | Auto | ID duy nhất |
| `username` | String | Yes, Unique | Tên đăng nhập |
| `password` | String | Yes | Mật khẩu |
| `email` | String | Yes, Unique | Email |
| `fullName` | String | No | Tên đầy đủ |
| `avatarUrl` | String | No | URL avatar |
| `status` | Boolean | No | Trạng thái kích hoạt |
| `role` | Number | No | ID của role |
| `loginCount` | Number | No | Số lần đăng nhập |
| `isDeleted` | Boolean | Auto | Đã xoá (soft delete) |
| `timestamp` | Date | Auto | Thời gian tạo/cập nhật |

---

## Cấu trúc Role Object

| Field | Type | Yêu cầu | Mô tả |
|-------|------|--------|-------|
| `_id` | Number | Auto | ID duy nhất |
| `name` | String | Yes, Unique | Tên role |
| `description` | String | No | Mô tả role |
| `isDeleted` | Boolean | Auto | Đã xoá (soft delete) |
| `timestamp` | Date | Auto | Thời gian tạo/cập nhật |

---

## Thông tin thêm

- **Soft Delete**: User và Role không bị xoá vật lý, chỉ đánh dấu `isDeleted = true`
- **Validation**: Username và email phải là duy nhất
- **Enable/Disable**: Chỉ cần username và email khớp để enable/disable user
- **Default Values**:
  - `fullName`: ""
  - `avatarUrl`: "https://i.sstatic.net/l60Hf.png"
  - `status`: false
  - `loginCount`: 0
  - `description`: ""
