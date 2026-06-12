---
title: "MySql database authentication"
date: 2010-01-26
forum: Server Platforms
---

### Post by Sn3akyP3t3 on 2010-01-26
I've been working on a server-client project for over a year for video transcoding.  The purpose of the project is to capture video from the computer, upload it, transcode it to the desired format, email the user a link to the completed video, and provide for streaming the media.  The project is written mostly in Autoit on the client side.  There are three parts to the project capture, upload, and transcode.  The project uses CamStudio, FileZilla, Sqlite, FFMPEG, MySql, and Darwin Streaming Server to perform these tasks.  The client computer is Winblows and the server is Ubuntu.

My question is how to authenticate from the client computer to the server database securely.  The capture component does not communicate with the server in any way, but it does make entries into the local database on the computer via Sqlite.  The upload component makes connection with the local Sqlite database which needs to be passed to the server running MySql.  The user of the upload component does not know the username or password of the database.  The upload component does require login via FileZilla to SFTP the file to the server.

Is there a way to either:
1.) Securely store the username and password in a config file on the client computer or similar method.
2.) Alter the config of MySql to piggyback the use of the username and password of the user logged into the server to authenticate with the database.
3.) Any other suggested and approved method that I haven't been able to think of or come across.

I've never taken any cryptography class in college so some methods of hashing are a little foreign to me if that is the suggestion.  Even so, I'm willing to get my hands dirty.

---

### Post by Sn3akyP3t3 on 2010-02-01
Did I post in the wrong forum category or is this not possible?

---

### Post by cariboo on 2010-02-02
You may get an answer to your question in the server platform sub-forum. Moved

---

