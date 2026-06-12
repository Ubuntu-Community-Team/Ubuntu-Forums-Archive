---
title: "Setting up client ftp. need help"
date: 2010-08-02
forum: Server Platforms
---

### Post by artheus on 2010-08-02
Hi all!

At my company we need to set up a client ftp. Where we will make a small script to add users to the ftp.

So what I want is for when I use the script to add a user, it will add a user. Create a custom, empty, home folder. And then the ftp will chroot this new user to it's home folder.

So what I am wondering about is: What would be the most appropriate way to solve this?

As of right now I've temporarily solved this by creating local users. But I want to change this ASAP to e.g virtual users.

Another thing is that all the users should be in the same group or something, so that the client ftp "super" user, which name is "clientftp" will be able to read and write to all files.

Thanks!
//Artheus

---

