---
title: "Why is One eating up my disk space?"
date: 2012-01-05
forum: Ubuntu One (CLOSED)
---

### Post by PaulHuffman on 2012-01-05
I have a fairly new installation of 11.04. I thought I'd try Ubuntu One again. Testing to see if One will sync files from samba mounts. Yesterday I started to get desk full warnings on my desktop.  Ubuntu One Control Panel says using 3.6 GB of 5.0 GB, File Synch in progress. But df shows my one disk 100% full and du shows a huge directory in my home directory:
```
paul@pauleseries:~$ pwd
/home/paul
paul@pauleseries:~$ sudo du -sk *|sort -n
du: cannot access `avdata': Permission denied
du: cannot access `elevation': Permission denied
du: cannot access `pauldocs': Permission denied
4	Desktop
4	Documents
4	Downloads
4	examples.desktop
4	Music
4	Pictures
4	Public
4	Templates
4	Videos
1748	Dropbox
61671364	Ubuntu One
```

where the permission denied directories are the samba mounts.  Is One ever going to turn this disk space loose?

---

