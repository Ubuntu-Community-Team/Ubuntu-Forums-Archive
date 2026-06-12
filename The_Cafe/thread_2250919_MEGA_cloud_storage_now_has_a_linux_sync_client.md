---
title: "MEGA cloud storage now has a linux sync client"
date: 2014-10-31
forum: The Cafe
---

### Post by Paulgirardin on 2014-10-31
MEGA offer 50Gb free.The new sync client looks nice too.

[https://mega.co.nz/#sync](https://mega.co.nz/#sync)

---

### Post by sffvba[e0rt on 2014-11-01
Nice.  Patiently awaiting there much hyped e-mail and chat clients but I suspect that will still take a lot of time (especially to reach linux).

---

### Post by Bucky Ball on 2014-11-01
I like it and I like their ethos. Never used a cloud before, now could be the time.

Just curious, though. What are DL/UL speeds?

---

### Post by Jonor on 2014-11-01
Free account, UK location here, averaging two tests, a 4mb mp3, UL around 80kb/s - about 100 seconds, DL was faster, about 30 seconds.

---

### Post by Bucky Ball on 2014-11-01
I created an account and tried it myself, actually, Downloads were definitely faster than uploads. Bareable. I don't think I'd use it often, though, and will probably stick to the external drive for most backups. eSATA with a 7200rpm HDD as fast as an internal drive. Maybe I'm too used to that.

---

### Post by bapoumba on 2014-11-01
No joy with lubuntu 14.10 here..

---

### Post by sffvba[e0rt on 2014-11-01
Working like a charm in Ubuntu Gnome 14.10...

---

### Post by ibjsb4 on 2014-11-01
> **bapoumba said:**
> No joy with lubuntu 14.10 here..
Same here on a lxde/gnome mix (14o4), but gdebi did.
```
sudo gdebi megasync-xUbuntu_14.04_amd64.deb
```

---

### Post by pqwoerituytrueiwoq on 2014-11-01
id use this but i have owncloud setup already on my rPi, i don't have 50gb available on my 16gb sd card, but i am not using that much

---

### Post by Tar_Ni on 2014-11-01
Mega is a great cloud service. Probably the most privacy-oriented cloud out there. And geez 50GB of storage for free, that makes the Dropbox(2GB) and even Google Drive (15GB) look bad.

---

### Post by bapoumba on 2014-11-01
> **ibjsb4 said:**
> Same here on a lxde/gnome mix (14o4), but gdebi did.
```
sudo gdebi megasync-xUbuntu_14.04_amd64.deb
```
I just had a closer look (i386 package here). I was missing a few libs that were specified as dependencies. Syncing right now :)
I used the 14.04 package on 14.10, it worked.
I was missing libc-ares2, libcrypto++9 and libqt4-dbus.

Thanks :)

---

