---
title: "apt-mirror 404 error"
date: 2009-11-05
forum: Server Platforms
---

### Post by silence444 on 2009-11-05
Morning all
I have created a mirror for our company for 8.10 and 9.10 and it downloaded the repositories fine. but when i set it as the update server for the another pc's and type 'apt-get update', those pc's give an error like "Failed to fetch [http://192.168.0.95/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz](http://192.168.0.95/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz)  403 Forbidden" 

I have googled and searched the forums but everyone says that you should just change mirror on the client side, but that would defeat the purpose.

PLease help.

TYIA

adrian

---

### Post by silence444 on 2009-11-05
Ok i fixed the 404 error (sym link was messed) but now when i "apt-get update" on the clients it is giving me "W: Failed to fetch [http://192.168.0.95/ubuntu/dists/intrepid-security/universe/source/Sources.bz2](http://192.168.0.95/ubuntu/dists/intrepid-security/universe/source/Sources.bz2)  Hash Sum mismatch"

This is really frustrating.
Thanks again

Adrian

---

### Post by silence444 on 2009-11-06
OK sorted it out. I re-downloaded the files under "dists" from the archive.ubuntu.com and re ran apt-get update on client machines and all is fixed now.

hope this helps someone else oneday
Adrian

---

