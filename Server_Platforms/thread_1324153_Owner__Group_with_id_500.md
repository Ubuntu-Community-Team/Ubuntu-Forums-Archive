---
title: "Owner / Group with id 500"
date: 2009-11-12
forum: Server Platforms
---

### Post by Livios on 2009-11-12
Hi,

I installed an Ubuntu 8.04 LAMP server with Drupal 6.x. The permissions of files and directories inside /var/www look like this:

# ls -l
total 228
-rw-rw-r--  1 500 500 43058 2009-10-22 21:50 CHANGELOG.txt
-rw-rw-r--  1 500 500  1199 2009-10-22 21:50 COPYRIGHT.txt

I would like to know which user/group has permissions in /var/www but there is no existing user or group with id 500. Is 500 a special group/user or does it have a special meaning ?


Thx
Robby

---

### Post by Lars Noodén on 2009-11-12
These were left with the wrong settings by the package.

User names and groups map to numbers.  See the utility **id** for ways to nose around your own system.  Run with no parameters, it will give info about your account.  

On the system that the package was made, there was a user and a group each with the number 500.  It is an oversight and probably could be reported as a bug, albeit a minor one.

---

### Post by lykwydchykyn on 2009-11-12
If I'm not mistaken, archive files retain ownership and group information. This is always stored as a UID number, not as an actual owner/group name.  So UID/Group 500 was a user and group on whatever machine the drupal archive was packed on.  Since there is no corresponding account or group on your machine, the ownership shows up as a UID number (there's no name to map that number to).

You can (and probably should) just change the owner and group to whatever is appropriate for your system.

---

### Post by Livios on 2009-11-16
I changed the owner and group to an existing user/group.
Thanks for the help !

---

