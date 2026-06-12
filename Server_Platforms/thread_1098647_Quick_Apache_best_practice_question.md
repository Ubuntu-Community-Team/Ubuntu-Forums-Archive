---
title: "Quick Apache best practice question"
date: 2009-03-17
forum: Server Platforms
---

### Post by moonpup on 2009-03-17
Hi all,

I need to setup a web server for the web development team. All of the people in this group will need write permissions to publish content to the web server. What is the best way to accomplish this?

I was just going to create a new group and add all the users to it, then change the group owner on the document root along with the permissions for the group and finally set the group sticky bit.

Am I going about this incorrectly? Is there a better way to do this? Thanks!

---

### Post by Dr Small on 2009-03-17
I would enable the userdir module for user accounts and either give them their own directory on the server, or make one central directory where all the development will take place, set group permissions on it, put all development users in this group, and create a symlink in their $HOME to the directory.

---

### Post by moonpup on 2009-03-17
Thanks Dr. Small, but they all need to publish to the apache document root. So I guess I will create a group, add them all to it and set the permissions, group owner and sticky bit.

Would it be a bad idea to simply add them to the existing www-data group with write permissions on the document root?

---

### Post by moonpup on 2009-03-18
Bump... any opinions as to if this is a good or bad solution?

---

