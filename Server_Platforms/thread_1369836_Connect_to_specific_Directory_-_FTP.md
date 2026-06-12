---
title: "Connect to specific Directory - FTP"
date: 2010-01-01
forum: Server Platforms
---

### Post by IZWicky on 2010-01-01
Hello all, newbie here:

I'm using VSFTP in my ubuntu server and I want FTP to show me only the */var/www* directory and its files/sub-directories. How can I do this? This has to do with *vsftp.conf*?

Also I've read is recommended to make a user only for FTP, thus limiting its access to the desired directory. How can I do such thing?

Help is appreciated! :)

---

### Post by lightsabersetc on 2010-01-02
Open vsftpd configuration file - /etc/vsftpd/vsftpd.conf
# vi /etc/vsftpd/vsftpd.conf

Make sure line exists (and uncommented):
chroot_local_user=YES

Save and close the file. Restart vsftpd.
# /etc/init.d/vsftpd restart

Chroot locks all users into their home directory, so then create your FTP users - unrestricted dir = home (or create a dir of symbolic links to other dirs if multiple unrestricted).

---

