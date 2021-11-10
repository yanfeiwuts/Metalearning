README
===

# MetaMusic 

## Table of Contents
1. [Overview](#Overview)
1. [Product Spec](#Product-Spec)
1. [Wireframes](#Wireframes)
2. [Schema](#Schema)

## Overview
### Description
This app wll have users connect, learn and share music.

### App Evaluation
[Evaluation of your app across the following attributes]
- **Category:** Entertainment, Networking
- **Mobile:** iOS, Android
- **Story:** Help people share and listen to music in a fun and easy way
- **Market:** Aimed toward students
- **Habit:** Could be used at any time
- **Scope:** Pairing students with similiar interests

## Product Spec

### 1. User Stories (Required and Optional)

**Required Must-have Stories**

* Users register to new account (Email, Facebook, Github)
* Users logs in to access account
* User picks the technology/language/etc they would like to learn
* Settings (Accessibility, Notification, General, etc.)

**Optional Nice-to-have Stories**

Log of past songs/people with album art covers matching
* Page of most use learning material (i.e. learning material that most users are connecting through)
* Listening/Encounter Queue


### 2. Screen Archetypes
* Login 
* Register - User signs up or logs into their account
   * Upon Download/Reopening of the application, the user is prompted to log in to gain access to their profile information to be properly matched with the learning Material and connect between group. 
   * ...
* Messaging Screen - Chat for users to communicate (direct 1-on-1)
   * Upon selecting subject of choice users matched and message screen opens
* Profile Screen 
   * Allows user to upload a photo and fill in information that is interesting to them and others
* Song Selection Screen.
   * Allows user to be able to choose their desired subject, class, genre of preference and begin learning and interacting with others.
* Settings Screen
   * Lets people change language, and app notification settings.

### 3. Navigation

**Tab Navigation** (Tab to Screen)

* Learning selection
* Profile
* Settings

Optional:
* Discover (Top Choices)

**Flow Navigation** (Screen to Screen)

* Forced Log-in -> Account creation if no log in is available
* Learning Selection (Or Queue if Optional) -> Jumps to Chat/ FAQ's
* Profile -> Text field to be modified. 
* Settings -> Toggle settings

## Wireframes
[Add picture of your hand sketched wireframes in this section]
<img src="http://g.recordit.co/uWXuIosXgV.gif" width=600>

### [BONUS] Digital Wireframes & Mockups

### [BONUS] Interactive Prototype

## Schema 

   | Property      | Type     | Description |
   | ------------- | -------- | ------------|
   | objectId      | String   | unique id for the user post (default field) |
   | author        | Pointer to User| image author |
   | image         | File     | image that user posts |
   | caption       | String   | image caption by author |
   | commentsCount | Number   | number of comments that has been posted to an image |
   | likesCount    | Number   | number of likes for the post |
   | createdAt     | DateTime | date when post is created (default field) |
   | updatedAt     | DateTime | date when post is last updated (default field) |
### Models
[Add table of models]
### Networking
- [Add list of network requests by screen ]
- Home Feed Screen
      - (Read/GET) Query all posts where user is author
         ```swift
         let query = PFQuery(className:"Post")
         query.whereKey("author", equalTo: currentUser)
         query.order(byDescending: "createdAt")
         query.findObjectsInBackground { (posts: [PFObject]?, error: Error?) in
            if let error = error { 
               print(error.localizedDescription)
            } else if let posts = posts {
               print("Successfully retrieved \(posts.count) posts.")
           // TODO: Do something with posts...
            }
         }
         ```
      - (Create/POST) Create a new like on a post
      - (Delete) Delete existing like
      - (Create/POST) Create a new comment on a post
      - (Delete) Delete existing comment
   - Create Post Screen
      - (Create/POST) Create a new post object
   - Profile Screen
      - (Read/GET) Query logged in user object
      - (Update/PUT) Update user profile image
- [Create basic snippets for each Parse network request]
- [OPTIONAL: List endpoints if using existing API such as Yelp]
