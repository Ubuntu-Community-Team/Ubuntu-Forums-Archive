---
title: "root privilages"
date: 2007-10-06
forum: Server Platforms
---

### Post by samona on 2007-10-06
hi,
I have created a user on my linux box and when they use SSH to log into the server, they are able to access the root directory, and other users directory.  How can I give a user account access to ONLY his own home directory and whatever else files below that?

---

### Post by dfreer on 2007-10-07
You'll need to chroot jail the user to their home directory, I do believe. I did this once, takes a while to set it up. A better solution would probably be to determine your users needs, and then come up with a specific solution for that need instead of using ssh. For example:
User X needs to upload files to the server. Set up an FTP server, or perhaps a Samba share if it is on the LAN.

---

### Post by samona on 2007-10-07
Thanks!  But I need to have SSH available for all users. I got it so that the users cannot enter each other's home directory, however when a user types the command "cd /", they are able to access the root directory.  I want to take this permission away, but when I "chmod o-r /" users cannot even login.  The window opens and closes quickly.  Any help will be appreciated.

---

### Post by OmegaBLK on 2007-10-07
> **samona said:**
>  I want to take this permission away, but when I "chmod o-r /" users cannot even login.  The window opens and closes quickly.  Any help will be appreciated.

Yea / needs to be world(o) readable(r) and executable(x) as you have found out already.  Try taking a look at scponly and a couple of other links here:

[http://sublimation.org/scponly/wiki/index.php/Main_Page](http://sublimation.org/scponly/wiki/index.php/Main_Page)
[http://singe.za.net/blog/archives/378-Linux-SSH-Jail-with-pam_chroot.html](http://singe.za.net/blog/archives/378-Linux-SSH-Jail-with-pam_chroot.html)
[http://olivier.sessink.nl/jailkit/](http://olivier.sessink.nl/jailkit/)

---

