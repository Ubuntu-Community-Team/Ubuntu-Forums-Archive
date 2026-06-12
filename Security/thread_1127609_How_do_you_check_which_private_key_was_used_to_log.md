---
title: "How do you check which private key was used to login?"
date: 2009-04-16
forum: Security
---

### Post by svittal on 2009-04-16
Hi,

I'm trying to find our which provite key was used by the user to login to the system.

I have a ubuntu server which can be logged into as just one user 'admin' other than the 'root' user. We have 2 jr administrators who login to the server time-to-time to take care of software deployment.  These jr admins logs into the server using their own private key.

When I do a 'last' I get to know which user and IP last logged in. Since its just one user 'admin' I can differentiate it only by the IP.

Is there a way I can capture which private key was used to login also?

There is a requirement due to which we have only 2 users 'admin' and 'root'. If there is no way of knowing which private key was used to login to the server, I will have to end up creating 2 users 'admin1' and 'admin2' :( to know who did what.

---

### Post by lensman3 on 2009-04-16
Seems to me you should give the 2 jr. admins there own user ID that will only be used for software deployment.  But add then to the "root" group.  That way they have root privileges when they are logged in. 

I think you can set them up as regular users, but add them to the root group.  The /etc/passwd group field sets their default group, then when they need root group access have then do a "newgrp" command to change the group.  Take a look at the first few lines of /etc/group.  Just had your jr. admins login ID to their line.  

The group line will look like:

root:x:0:root,admin1,admin2                       (the smiley face is not part of the file.  Look at /etc/group)

Hope this helps (a little).

---

### Post by svittal on 2009-08-20
Thanks for the suggestion!

---

