---
title: "WebDAV, User shares, AD and me"
date: 2007-05-22
forum: Server Platforms
---

### Post by warlockvix on 2007-05-22
Been playing with WebDAV on IIS and it just isn't doing what I want it to do. I have a 2K server that I want to migrate shares over and enable WebDAV on. Soooo, I have decided to take the Linux route. I have an Ubuntu server authenticating with AD. When a user maps to the server for the first time, a home directory is created for them and the proper access is assigned to the folder. 

What I want to do is enable WebDAV on the all the users home directories (about 100 after I transfer them over) and retain the permissions of the user (not apache) when they are connected to the WebDAV folder.

So far, I haven't found a way to automagically enable WebDAV on users home directories when they are created or found a way (once I do get WebDAV enabled) to retain permissions. Any Ideas?

I tried gnome-user-share but it seems to only work on a Linux box. All my users will be on XP. I can enable WebDAV manually but I would need to do it on every folder and make a new entry everytime I get a new user. Very admin instensive and a lot of room for errors.

---

