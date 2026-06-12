---
title: "how can I accomplish this (group permissions and such)"
date: 2013-04-22
forum: Server Platforms
---

### Post by andrewjs18 on 2013-04-22
hi gents,

I'm still getting back into the swing of things with ubuntu.  I'm trying to set up an FTP group for users that'll be FTPing into my web server for ease of user management, but I want them to be restricted to different directories within the server.  I'd like to pick your brains to see if this is doable, and if it is, if my way is the best way of accomplishing this.

1: create the group called FTP
2: create the user(s), and set their home directory to whatever directory I want them to be locked inside of when they use FTP

I think that'll work how I want it to work, but the problem I think I might have is that the directory that they'd be FTPing into is owned by a different user/group.  how should I work this in? 

basically what I'm trying to accomplish is what you'd be able to do with shared hosting that uses cpanel where you can creat an FTP user and then lock them into a directory.  I don't have cpanel installed so I'm trying to think of a good way to accomplish this without it.

let me give a few examples, to hopefully clarify myself.

I've got a directory /home/web/test.  the directory /home/web and everything within it is owned by 'web'.  I want a newly created user, who is put in the FTP group, to be able to do 777 actions in /home/web/test.  

hope that's a decent explanation of what I'm trying to accomplish.

---

### Post by sub1ime on 2013-04-22
What you want to do sounds specific to which FTP server program your using.

---

