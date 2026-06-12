---
title: "Server help"
date: 2008-09-13
forum: Server Platforms
---

### Post by fedex1993 on 2008-09-13
Okay i am trying to have multipule users use this server at one time. Well i am using ssh and i want someone to login as nathan@HOSTNAME and it will automatically put him in /home/nathan and have it where he can only rw in /home/nathan but not any other folder. But also inside of /home/nathan/www there they will be able to put in php files for a webage that will be in /var/www/nathan. But have the same files in /home/nathan/www be in /var/www/nathan so that someone can access them. Is this possible that someone could help me with?

---

### Post by Sef on 2008-09-13
moved to server platforms.

---

### Post by windependence on 2008-09-13
> **fedex1993 said:**
> Okay i am trying to have multipule users use this server at one time. Well i am using ssh and i want someone to login as nathan@HOSTNAME and it will automatically put him in /home/nathan and have it where he can only rw in /home/nathan but not any other folder. But also inside of /home/nathan/www there they will be able to put in php files for a webage that will be in /var/www/nathan. But have the same files in /home/nathan/www be in /var/www/nathan so that someone can access them. Is this possible that someone could help me with?

Possible, but not easy. Keeping them in their homes is easy enough, you can just chroot them in their home directories, but working out all the web stuff in this environment is gonna be hell.

Are you trying to give them each their own web site that they can modify? If so, you probably want something like a hosting control panel. ISPconfig is an open source one, but many people use Cpanel, Plesk, ect.

-Tim

---

