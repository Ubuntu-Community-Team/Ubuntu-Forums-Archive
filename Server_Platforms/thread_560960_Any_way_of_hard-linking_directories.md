---
title: "Any way of hard-linking directories?"
date: 2007-09-27
forum: Server Platforms
---

### Post by naxcitl on 2007-09-27
Hi, I'm wanting to get an ftp server up and running, and all users will be chrooted.  I do, however, want some directories to be shared between users.

I can't use symbolic links for this because they will not work pointing to directories outside the chroot jail.  I thought using hard links was to be the solution but Ubuntu does not appear to allow it.  I tried: ```
ln -d /path/to/directory
``` as the superuser but it still wouldn't let me.

Is there any way of enabling hard links to [COLOR="Red"]directories[/COLOR]?  If not, is there an alternative?

I'm using Ubuntu 6.06.1 (Dapper) Server Edition, with the ext3 filesystem.

---

### Post by TheDom on 2007-09-27
I did this by creating an appropriate directory in the user's home dirs and then "mount --bind /var/www/shared /home/user/shared". :)

---

### Post by steve.horsley on 2007-09-27
You could try:
**ln -d /path/to/directory linkname**
but **man ln** is discouraging. 

I really like the mount --bind idea. I didn't know that was possible.

---

### Post by naxcitl on 2007-09-28
Thanks for the replies, the **mount --bind** method did the job!

Although I can't help wondering if there is some setting somewhere in **/etc** which could be changed to allow hardlinking of directories...

---

