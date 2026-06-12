---
title: "Beginner question on www-data user and group"
date: 2007-06-24
forum: Server Platforms
---

### Post by RogerHaase on 2007-06-24
I am trying to create a web testing environment on a 7.04 Desktop Edition.  I have installed Apache and understand it will run under the user/group of www-data.  

I will also be running Webware For Python under a unique user/group ID and there is a directory that needs to share read/write permission between Webware and Apache.  Under Fedora Core 6, I managed to do this by making the Webware user a member of the Apache group and then setting permissions accordingly.

The System>Administration>Users And Groups tool does not appear to have a way to make a user a member of multiple groups and www-data is not listed as a user nor as a group.

How do I make my Webware user a member of the www-data group or is there a better way to achieve what I am trying to do?

Roger

---

### Post by Mr. C. on 2007-06-24
Edit the /etc/group file manually.  An example of adding user1 and user2 to the www-data-group:

```
www-data:x:99:user1,user2
```

Be sure to restart apache.

MrC

---

