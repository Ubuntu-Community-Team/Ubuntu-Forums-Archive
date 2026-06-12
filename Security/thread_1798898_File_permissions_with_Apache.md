---
title: "File permissions with Apache"
date: 2011-07-06
forum: Security
---

### Post by jcab on 2011-07-06
I know how to assign file permissions and other tasks like user to group, but I'm stuck with a situation in how I should set up my system.

So I have a LAMP server set up. I'm not the only developer so I created a group called "developers" for my other users "Mike," "Alex," and "Cindy," which are developers (I'm Mike by the way). I know that "www-data" is the user and group Apache uses.

So for my production site, the 
Owner is Mike which has read and write &
Group is www-data has only read.

This is good because only I have permission to update the production site, but for the dev site, it's a different story.
I need my group developers to read and write, while www-data only reads. How should I do this?

Thank you :D

---

### Post by cariboo on 2011-07-07
Set the www-data group to have read and write permissions. Typically you would set the permission to 775.

---

### Post by CharlesA on 2011-07-07
You could set it so that the owner is www-data and the group is developers.

Then set the permissions to 570. Might not be ideal, but it'll work.

---

### Post by jcab on 2011-07-07
I was reading about ACL (Access Control Lists), and it seems like the perfect solution, but I keep getting "operation not permitted," even after configuring /etc/fstab and remounting. :confused: 

Nonetheless, I think I'll use your idea Charles. I can't think of anything else.

---

