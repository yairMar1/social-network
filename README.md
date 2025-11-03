# Social Network Simulation - A Design Patterns Showcase

A Python-based simulation of a social network, built from the ground up to demonstrate the practical application of core software design patterns like **Singleton** and **Observer**.
This project models the fundamental interactions of a social platform: users, posts, followers, and notifications.

> This project is less about building a functional social network and more about architecting a clean, scalable, and maintainable system using software engineering principles.

## Key Features

- **User Management:** Create unique users and manage their profiles within the network.
- **Follow/Unfollow System:** Users can dynamically follow and unfollow other users.
- **Polymorphic Content Posting:** Supports different types of posts (Text, Image, Sale), each with its own specific behavior.
- **Real-Time Notification System:** Users automatically receive notifications when a user they follow posts new content, showcasing a decoupled notification mechanism.

## Technical Highlights & Capabilities Demonstrated

This project is a deep dive into software architecture.
The core logic is built upon two fundamental design patterns that solve common problems in large-scale applications.

### 1. Singleton Pattern for Global State Management

The `SocialNetwork` class is implemented as a **Singleton**. This ensures that only one instance of the social network can exist throughout the application's lifecycle.

- **How it works:** A static method controls the instance creation, ensuring that the first call creates a new instance, while all subsequent calls return the same, existing instance.
- **Why it matters:** This pattern is crucial for managing a single, authoritative global state. It prevents state conflicts (e.g., multiple disconnected networks) and provides a centralized, globally accessible point for managing all users and interactions, mimicking how a real-world server would operate.

### 2. Observer Pattern for Real-Time Notifications

The notification system is a classic implementation of the **Observer** pattern.

- **How it works:**
    - A `User` acts as the **Subject** (or Publisher).
    - Their followers are the **Observers** (or Subscribers).
    - When a user (Subject) creates a post, they trigger a `notify()` method. This method iterates through their list of followers (Observers) and calls their `update()` method, delivering the notification.
- **Why it matters:** This creates a highly **decoupled system**. The user posting content doesn't need to know *who* their followers are or *how* to contact them. They only need to announce that they've posted. This makes the system scalable and maintainable new types of notifications or followers can be added without changing the user's code.

### 3. Polymorphism for Diverse Content Types

The system handles different types of posts elegantly using polymorphism.

- **How it works:** A base `Post` class (or interface) defines a common structure and behavior for all posts. Concrete classes like `TextPost`, `ImagePost`, and `SalePost` inherit from this base class and provide their own specific implementations.
- **Why it matters:** This allows the rest of the system like the notification service or a news feed to handle any type of post through a single, unified interface, without needing to know the specific details of each type.