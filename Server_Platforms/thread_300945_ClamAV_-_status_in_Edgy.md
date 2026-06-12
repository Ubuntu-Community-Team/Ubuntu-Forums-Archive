---
title: "ClamAV - status in Edgy?"
date: 2006-11-16
forum: Server Platforms
---

### Post by randysparks on 2006-11-16
Does anybody know the status of ClamAV in Edgy? It's in universe but when I tried to install it via Synaptic I got all kinds of package dependency errors. Additionally, ClamTk complained the virus definition database was over 100 days out of date. 

Should I subscribe to the Debian volatile repo, as described on the ClamAV home page? [http://www.clamav.net/binary.html#pagestart](http://www.clamav.net/binary.html#pagestart)

---

### Post by randysparks on 2006-11-16
Sounds like ClamAV is broken:

[http://ubuntuforums.org/showthread.php?t=279652](http://ubuntuforums.org/showthread.php?t=279652)

Does anybody know if it's broken in Dapper too? ](*,)

---

### Post by randysparks on 2006-11-16
The cure appears to be to apt-get install clamav twice. The second time around it appears to fix the dependency issues. 

The problem has been reported as a bug:

[https://launchpad.net/distros/ubuntu/+source/clamav/+bug/66636](https://launchpad.net/distros/ubuntu/+source/clamav/+bug/66636)

---

### Post by iPirates on 2006-12-28
Yea I had a similar problem trying to run ClamAV in edgy...

---

