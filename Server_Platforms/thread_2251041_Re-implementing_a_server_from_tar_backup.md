---
title: "Re-implementing a server from tar backup"
date: 2014-11-01
forum: Server Platforms
---

### Post by David_Holt on 2014-11-01
I have a tar backup of all directories outside of /proc and /mnt for a web server that hosts FTP and Samba on my local network. Can I install Ubuntu on another physical machine and restore from that tar to get the same environment back?

---

### Post by slickymaster on 2014-11-01
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by volkswagner on 2014-11-01
Take a look at the comprehensive [backup via tar thread]("http://ubuntuforums.org/showthread.php?t=35087").

You will want some backups of machine specific files like /etc/fstab and what ever replace udev rules for ethernet, before overwriting
the fresh install.

---

