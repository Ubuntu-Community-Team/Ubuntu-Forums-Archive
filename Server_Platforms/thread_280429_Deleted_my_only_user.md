---
title: "Deleted my only user"
date: 2006-10-19
forum: Server Platforms
---

### Post by mamurad_mtl on 2006-10-19
Hi everyone.

I'm very new to Linux... I just installed it today...

After I installed it, and logon... the system asked me for my username and password... so I enetereid them... but I got used to Windows XP, and I didn't want to be asked that everytime I boot the Linux... so I thought things work like Win XP... so I went to users and I deleted the only user which I used for installation...

Now I lost my access permissions... 

I have no idea what to do... how can give myself back my access privilages?


Best regards.
mamurad_mtl

---

### Post by mamurad_mtl on 2006-10-19
I forgot to mention... I still can login... but I can;t access Administration in System menu...

---

### Post by anortrup on 2006-10-19
You can use a live CD to edit the /etc/passwd file (on your hard disk) to add a line as follows:

rescueme::0:0::/root:/bin/bash

This will create a new root user with no password.  You can then reboot and login with "rescueme" and no password. Then go to System > Administraiton > Users and Groups and create a new user.  Be sure to check the "Execute System Administration Tasks" box on the advanced tab so that you will have sudo access.

Next you ABSOLUTELY MUST remove the resecume user from the password file.  

At that point you should be all set.

---

