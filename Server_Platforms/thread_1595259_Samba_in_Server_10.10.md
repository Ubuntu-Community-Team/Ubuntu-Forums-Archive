---
title: "Samba in Server 10.10?"
date: 2010-10-13
forum: Server Platforms
---

### Post by Lucky. on 2010-10-13
I recently installed Server 10.10 64-bit.

After installation, I set up my config file (/etc/samba/smb.conf), and tried to restart Samba:

```

/etc/init.d/samba restart

```

There was nothing to restart though - the file /etc/init.d/samba wasn't there!

Purged the package, and re-installed.  Same issue.  Tried reformatting and adding Samba as a pre-installed package.  Same deal.  Trying to find the server guide for 10.10, but no dice.  Did something change for Samba in 10.10?

---

### Post by Lucky. on 2010-10-13
Never mind, guess this happened in Lucid:

[Previous post](http://ubuntuforums.org/showthread.php?t=1474829)

---

