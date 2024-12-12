# iptv_app

**NetConnect-IPTV** is a cross-platform Flutter-based application for streaming IPTV (Internet Protocol Television) content. The app provides users with an easy-to-use interface for streaming live TV channels, managing user accounts, and exploring various IPTV content categories. It supports multiple platforms, including Android, iOS, Web, and Desktop (Windows, macOS, Linux).

This document provides detailed information about the project, its features, modules, API integrations, dependencies, and more.

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Getting Started](#getting-started)
3. [Project Structure](#project-structure)
4. [Modules](#modules)
   - [Authentication Module](#authentication-module)
   - [Home Screen](#home-screen)
   - [Video Player Module](#video-player-module)
5. [API Integration](#api-integration)
   - [User Authentication](#user-authentication)
   - [Channel List and Streaming](#channel-list-and-streaming)
6. [Dependencies](#dependencies)
7. [Testing](#testing)
8. [Contributing](#contributing)
9. [License](#license)

---

## Project Overview

**NetConnect-IPTV** is designed to provide users with seamless IPTV streaming and management through a native mobile or web app. The app allows users to:

- **Login and Register**: Secure user authentication and session management.
- **Browse IPTV Channels**: View and filter IPTV channels by categories such as news, sports, entertainment, and more.
- **Watch Live TV**: Stream live television directly on their devices.
- **Manage Profiles**: Edit personal information and manage preferences.

This app integrates with a backend API to handle user management, IPTV channel listings, and streaming functionalities.

---

## Getting Started

To run this project locally, follow the instructions below:

### 1. Clone the Repository

First, clone the repository to your local machine:

```bash
git clone https://github.com/sharmasanjana17/NetConnect-IPTV.git
cd NetConnect-IPTV

### 2. Install Dependencies

Install all necessary Flutter dependencies:

flutter pub get

### 3. Run the App

Once the dependencies are installed, you can run the app on an emulator or a physical device:

flutter run

---

## Project Structure

The project follows a clean architecture with modularization for easy maintenance and scalability. Below is an overview of the directory structure:

NetConnect-IPTV/
├── android/                # Android-specific code and configuration
├── ios/                    # iOS-specific code and configuration
├── lib/                    # Flutter app code
│   ├── authentication/     # User authentication (Login, Registration)
│   │   ├── login/          # Login-related code
│   │   ├── register_services/ # Registration services
│   │   └── login_services.dart # Login API integration
│   ├── features/           # Core features of the app
│   │   ├── home/           # Home screen, channel listings, categories
│   │   └── video_player_page/ # Video player for live streaming
│   ├── main.dart           # Main entry point for the app
├── pubspec.yaml            # Project dependencies and configuration
└── test/                   # Unit tests and widget tests

### Key Directories and Files:

- `lib/authentication/`: Contains files for login, registration, and authentication services.
- `lib/features/`: Contains the core features of the app, such as the home screen, channel browsing, and video player for IPTV content.
- `main.dart`: The main entry point of the Flutter application.
- `pubspec.yaml`: The project’s configuration file containing all dependencies.

---

## Modules

### Authentication Module (lib/authentication/)
The authentication module is responsible for user login, registration, and session management. It ensures that users can securely access the IPTV content.

#### 1. Login (`lib/authentication/login/login.dart`)

This file contains the UI for the login screen where users can enter their credentials (email and password) to log into the application.

- UI Components: Text fields for email and password, login button, error messages.
- Validation: Ensures that the email format is correct and that the password meets certain criteria (e.g., length).

#### 2. Registration (`lib/authentication/register_services/register.dart`)

This file handles user registration, allowing new users to create an account by providing their details such as name, email, and password.

- UI Components: Text fields for user information (email, password, name).
- API Call: Sends a request to the backend for creating a new user.
- Validation: Ensures that the email is unique and that password criteria are met.

#### 3. Login Services (`lib/authentication/login_services/login_services.dart`)

This file contains the logic for handling login requests. It makes HTTP requests to the backend API to authenticate users.

- API Integration: Sends a POST request to the /api/login endpoint with the user’s credentials.
- Token Management: Saves the session token locally using shared_preferences.

### Home Screen (lib/features/home/)

The home screen is the central hub of the app, displaying available IPTV channels and allowing users to filter channels by categories.

- Channel List: A list of IPTV channels fetched from the backend.
- Category Filter: Allows users to filter channels by categories like News, Sports, Entertainment, etc.
- Search Bar: Allows users to search for channels by name.

#### Key Files:
- `home.dart`: Displays the list of channels and allows interaction with category filters.
- `movies.dart`: Specific UI for browsing movies or video content.
- `drawer.dart`: Contains the side navigation bar with options like user profile, settings, and logout.

### Video Player Module (lib/features/video_player_page/)

The video player module allows users to stream IPTV content. When a user selects a channel, they are taken to the video player screen.

- Video Player UI: A simple UI to display the video stream with play/pause buttons, volume control, and fullscreen options.
- Stream URL: The app retrieves the stream URL for the selected channel and starts playing the live stream.

#### Key Files:
- `video_player_page.dart`: Contains the video player logic to play the IPTV stream.

---

## API Integration

### User Authentication

The app integrates with a backend API for user authentication and session management.

#### Login API

- Endpoint: /api/login
- Method: POST
- Parameters:
  - email: The user's email address.
  - password: The user's password.
- Response: 
  - Returns a session token and user details if authentication is successful.
  - Stores the session token for future use.

#### Registration API

- Endpoint: /api/register
- Method: POST
- Parameters:
  - email: The user's email address.
  - password: The user's password.
  - name: The user's full name.
- Response: 
  - A success message if registration is successful.
  - Error message if any field is invalid (e.g., email already exists).

### Channel and Stream API

The app fetches IPTV channels and stream URLs from a backend API.

#### Get Channels API

- Endpoint: /api/getChannels
- Method: GET
- Response: A list of channels, including:
  - id: Channel ID.
  - name: Channel name.
  - category: Category of the channel (e.g., News, Sports).
  - url: The URL for the live stream.

#### Get Stream URL API

- Endpoint: /api/getStreamUrl
- Method: GET
- Parameters:
  - channelId: The ID of the selected channel.
- Response: The direct URL of the IPTV stream for the selected channel.

---

## Dependencies

The project relies on several dependencies for state management, HTTP requests, and UI development. Below is a list of major dependencies used in the project:
- flutter: The core Flutter SDK for cross-platform app development.
- provider: State management library for managing the app's state.
- http: For making HTTP requests to the backend API.
- shared_preferences: To store session data locally.
- flutter_localizations: For handling internationalization and localization.
- video_player: Flutter plugin for integrating video playback functionality.
- dio: A powerful HTTP client for Dart.

You can find the complete list of dependencies in the pubspec.yaml file.

---

## Testing

To ensure the app's features work as expected, we have written unit and widget tests. To run the tests:

flutter test

This will execute all the tests in the test/ directory and provide feedback on the app's functionality.

---

## Contributing

We welcome contributions to improve this project. To contribute:

1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Make the necessary changes and commit them.
4. Push your changes to your forked repository.
5. Open a pull

 request explaining the changes you made.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more information.

---

## Acknowledgements

- Thanks to the Flutter community for providing such a fantastic framework.
- Special thanks to any third-party libraries used in the development of this project.

---

```

### Instructions to Update the README.md:

1. Copy the content above.
2. Go to your GitHub repository.
3. Click on `README.md` (or create a new one if it doesn't exist).
4. Paste the content.
5. Commit and push the changes.

---

This version of the README is much more detailed and offers a complete overview of the project. It breaks down the functionality of each module, the API integrations, dependencies, and testing guidelines. You can modify or extend the sections based on additional features or changes as the project evolves.

Let me know if you need further assistance!

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.
"# IPTV-" 
"# IPTV-" 
