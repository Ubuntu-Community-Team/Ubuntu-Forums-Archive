---
title: "SERVER/Pro FTP directory share and Apache"
date: 2013-01-25
forum: Server Platforms
---

### Post by hobatter on 2013-01-25
Replaced my old server almost there but
 
Ok My old Compaq Xeon server (aka the Harrier because it is loud as a jet) has now been officially replaced. I have a Dual quad core xeon blade server with 3TB of HD space SAS 10K hardrives and 16 G of ram. I love it.
 
I installed Ubuntu 12.10 server
 
Have Plex media running off a Samba share and all my devices can stream phenomenally.
 
I have webmin installed. I use webmin to mount a partition which says it is active and in use. I also have it set to auto mount on startup. This goes the same the media server. both say active and in use.
 
Problem: I used proftpd and created the directory of the mounted partition which I mounted as /mnt. I can create the ftp directory and created a sub folder called /Security under /mnt . I set it as the default directory for all and restart the FTP server. I connect via LAN and it shows my entire directory and I can write to it. I open /mnt/Security and it says I do not have permissions. I have even tried sudo chmod -R 777 /mnt/Security but nada. What am I doing wrong? The share is strictly for a security camera file drop. I have also created a FTP user and added it to the directory access but still nothing. 
 
I originally tried to use zoneminder but unable to get my camera connected. I removed zoneminder and now my apache homepage is hosed. How do I get apache back to default? can I just remove and install again?
 
Thanks for all the support. I never really have to post because of so much documentation and activity on the forums. You all are great.

---

### Post by chrisguk on 2013-01-25
To remove apache completely you would use:

```
sudo apt-get --purge autoremove apache2 
```

---

### Post by hobatter on 2013-01-25
Thanks and I can dl the server again and it will be a fresh install/config?

---

### Post by chrisguk on 2013-01-25
Completely fresh as if it never existed

---

