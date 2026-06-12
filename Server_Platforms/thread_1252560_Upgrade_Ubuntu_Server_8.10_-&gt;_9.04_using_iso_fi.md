---
title: "Upgrade Ubuntu Server 8.10 -&gt; 9.04 using iso file"
date: 2009-08-29
forum: Server Platforms
---

### Post by ugm6hr on 2009-08-29
Is this possible?

I have the Ubuntu Server 9.04 iso file, and was wondering if it is possible to mount the iso and use it to upgrade my Ubuntu 8.10 server like you can a desktop with the Alternate CD.

---

### Post by Iowan on 2009-08-29
Short answer - dunno.
Will the server be connecting to internet to get updates? (If so, is there an advantage - other than download time - to using the iso first?)

---

### Post by ugm6hr on 2009-08-30
Bandwidth (rather than time) is a good reason.

Does anyone know?

---

### Post by ugm6hr on 2009-08-31
Found this:
[http://ubuntuforums.org/showthread.php?t=35807](http://ubuntuforums.org/showthread.php?t=35807)

Mounted the iso for Jaunty as described, and added the iso as the only repository.

Then uninstalled all non-standard applications (i.e. those not on the CD), followed by apt-get autoremove.

Then:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Worked just fine, and preserved all files etc.

Then reinstalled my wiki (all data had been preserved).

---

