---
title: "vsftpd on ubuntu web server"
date: 2008-10-01
forum: Server Platforms
---

### Post by y-aji on 2008-10-01
Hello all,

**I am unsure as to whether or not this is the correct place to add this item.  Please do not hesitate to let me know the proper place to put this and I will move it there.**

I am trying to get my very first linux based webserver all working (I have always used the lazy way.. xampp on windows.)  Everything is totally working, but, when I ftp into it, it starts me in the given user's home folder, "/home/username/".. 

I want it to start in /var/www/ for everyone.  I do not know if this is a permissions thing, or a vsftpd feature, but where can I change it?  I also noticed that while in the /home/username/ folder, i can back up to the root directory and see everything on my linux box! oh no! i dont want that.  Is there a way to force the user into /var/www/ and not let them back up any further?  If anyone can point me in the right direction, I would appreciate it.

---

### Post by alastair on 2008-10-01
You can learn a lot by playing. But do it safely, not connected to an untrustworthy network (e.g. the internet) and only connecting yourself for a while, to test. Security is important.

VSFTP is "very secure" but you can configure it, and Linux, to be wide-open if you want. Or if you are not careful.

Check the docs out first - then play, test and come back if problems :

[http://vsftpd.beasts.org/vsftpd_conf.html](http://vsftpd.beasts.org/vsftpd_conf.html)

Alastair

---

### Post by y-aji on 2008-10-01
So you are hinting it would probably be something with vsftpd, then.. Thank you much.  That at least leads me in an appropriate direction.

---

### Post by lykwydchykyn on 2008-10-01
What you want is called chroot (short for "change root"), a feature most ftp server support in some manner. This changes the root of the filesystem as it appears to the user to whatever file location you decide.

I could never figure out in vsftpd how to set up a chroot on anything other than the user's home directory, which is why I switched to using ProFTPD instead.  I'm not saying there isn't a way to do it with vsftpd, but I could not figure it out from reading the man page or searching the internet.  But with both proftpd and pure-ftpd it can be easily managed.

---

### Post by y-aji on 2008-10-01
Interesting.. I'll take a look at proftpd and pure-ftpd. Thank you.

---

