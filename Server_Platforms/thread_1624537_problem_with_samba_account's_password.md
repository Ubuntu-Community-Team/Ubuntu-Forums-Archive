---
title: "problem with samba account's password"
date: 2010-11-17
forum: Server Platforms
---

### Post by EarthCrash on 2010-11-17
I used to Ubuntu server 9.10. and try to set up the samba for just simple file sharing test.
So i modified smb.conf file like this:

   unix password sync = no
   pam password change = no

Because i don't wan't to sync my samba's password with system's password.

  Everything seemed to be good. File shared was worked very well. But problem was popup when i logout-and-relogin. My (ID's)samba's password changed to system's password.

  I can change my samba's password again and that is work BUT that's useless because samba's password sync again with system's one if do re-login.(Just logout is not invoke this sync problem)

  What i do next was delete the /etc/pam.d/samba(actually, backup to other space) and delete '**pam_smbpass.so**' parameter in '/etc/pam.d/common-password' file that used for login process because i doubt that this problem involved with PAM. But that's not effective.

What's the problem?

---

### Post by dtfinch on 2010-11-18
Maybe you installed the libpam-smbpass package by accident.

Before now I didn't even know it could do that. I've always set passwords manually with smbpasswd.

---

### Post by EarthCrash on 2010-11-18
thanks to dtfinch

removing the libpam-smbpass package is helpful for solve this problem. now, it's completely works. Maybe it's installed when i install the ubuntu.

But it's still mystery that why PAM make problem like that even set the 'unix password sync' and 'pam password change' parameter to 'no'.(and even delete '**pam_smbpass.so**' parameter in '/etc/pam.d/common-password')

---

