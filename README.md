# 🧁 Self-Service Kiosk — Eid Cookies & Cakes Hub (C++)

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1_anMh4fu7-8xXQDu4_F9uSKHFr2s31bm?usp=sharing)

---

## 1️⃣ Project Overview
The **Eid Cookies and Cakes Hub** is a **self-service kiosk application** developed in **C++**, aimed at improving bakery management and customer experience during festive periods.  

The system streamlines sales operations, manages stock, and automates order handling — reducing staffing needs while maintaining efficiency.  
Built upon strong **Object-Oriented Programming (OOP)** principles, it integrates **file input/output**, **operator overloading**, and **data persistence** to ensure real-world functionality.

---

## 2️⃣ System Architecture and File Management

### 🏗️ Core Classes
The system is composed of multiple specialized classes that collectively simulate a real bakery workflow:

| Class | Role |
|:------|------|
| **Shop** | Acts as the central controller linking user interface and backend logic. |
| **User (Base Class)** | Defines shared attributes for `Staff` and `Customer` subclasses. |
| **Staff / Customer** | Role-specific functionality (inventory vs ordering). |
| **Inventory** | Handles pastry data storage, editing, and file synchronization. |
| **Pastry** | Represents each product item; supports operator overloading. |
| **Cart** | Manages customer selections and payment processing. |
| **View** | Provides display functions for menu navigation. |

---

### 💾 Data Persistence
The system uses multiple text files for **long-term data storage**:

| File | Purpose |
|------|----------|
| `staff.txt` | Stores staff usernames and passwords for authentication. |
| `customer.txt` | Stores customer accounts, including purchase counts for promotions. |
| `inventory.txt` | Contains all pastry details: type, flavour, quantity, weight, and prices. |

Data is automatically **loaded at program start** and **saved upon exit**, ensuring continuous synchronization between sessions.

---

### ⚙️ Key Technical Constraints
- ❌ No use of C++ standard library containers (`vector`, `list`, `queue`).  
- ❌ No global or public variables (except constants).  
- ✅ **Operator overloading** in the `Pastry` class:  
  - `-=` → reduce stock when an item is purchased.  
  - `+=` → restore stock when an item is removed from cart.  
  - `==` → compare pastries (for matching type and flavour).  

---

## 3️⃣ Core Program Scenarios and Features

The application operates from a main menu with **three user roles**:
> Exit | Staff | Customer

---

### 👤 1. User Authentication (Login / Sign-Up)
- Supports login and registration for **staff** and **customers**.  
- Credentials verified from the appropriate `.txt` file.  
- Prevents duplicate sign-ups using existing usernames.  
- Failed logins or duplicate sign-ups prompt clear feedback messages.

---

### 🧑‍🍳 2. Staff Functions — Inventory Management
Staff users have full control over the bakery’s stock:

| Function | Description |
|-----------|-------------|
| **View Inventory** | Displays all pastries with detailed info — flavour, type, stock, and price (RM/pc & RM/kg). |
| **Edit Inventory** | Allows updating of pastry attributes (Type, Flavour, Quantity, Price, etc.) with input validation (Type = “Cookie” or “Cake”). |
| **Add New Item** | Enables adding new pastry entries to `inventory.txt`. |

Data integrity is preserved through strict input checks before updates are saved.

---

### 🍰 3. Customer Functions — Ordering & Payment
Customer users interact via a dynamic, menu-driven interface:

| Feature | Description |
|----------|-------------|
| **View Menu** | Displays all available pastries. |
| **Order by Piece / Weight** | Customers can buy items per piece or per kilogram. |
| **Add to Cart** | Adding an item reduces the stock in the main inventory. |
| **View / Remove from Cart** | Customers can inspect or edit their cart; removing items automatically restores stock. |
| **Promotions & Discounts** | Applies discounts for first-time buyers or based on accumulated purchase counts. |
| **Payment Process** | Calculates total cost, applies discount, updates `customer.txt`, and clears the cart upon successful payment. |

---

## 4️⃣ Data Integrity and Validation

| Validation Type | Description |
|------------------|-------------|
| **Authentication Validation** | Prevents reuse of existing usernames and ensures correct login credentials. |
| **Input Validation** | Ensures pastry types, prices, and quantities are valid and within logical ranges. |
| **File Synchronization** | Automatically updates all text files after any change in inventory or purchase records. |

---

## 5️⃣ How to Compile and Run

### 📂 Required Files
- `main.cpp`  
- `shop.h`, `user.h`, `staff.h`, `customer.h`, `view.h`, `inventory.h`, `pastry.h`, `cart.h`  
- `staff.txt`, `customer.txt`, `inventory.txt`  

### ⚙️ Compilation Command
```bash
g++ *.cpp -o kiosk.exe
./kiosk.exe
