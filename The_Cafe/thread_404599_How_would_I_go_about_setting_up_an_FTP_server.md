---
title: "How would I go about setting up an FTP server??"
date: 2007-04-08
forum: The Cafe
---

### Post by billdotson on 2007-04-08
I have an old AMD Athlon K-something processor that runs at 333MHz and 64MB of PC100 RAM.  I have installed Puppy Linux on it and it rns pretty well.. but if I try to do something like start a download from say direct2drive.com (downloading a new game I have purchased for instance) puppy will freeze up.  Also, watching videos on google or youtube doesn't work too well.. the videos skip.  But puppy is apart from the point..

I would like to setup a home FTP server on it to make the old machine a bit more useful.  I saw that puppy has some FTP thing.

---

### Post by LookTJ on 2007-04-08
install proftpd and gproftpd

run gproftpd as root.

---

### Post by billdotson on 2007-04-08
I downloaded proftpd.tar.gz and gproftpd.tar.gz and used the PUPget package manager to install them.  I rebooted my computer and I cannot find them in the networks section of the programs. 
I have tried running proftpd and gproftpd in the terminal but that didn't start em.  By the way.. how am I supposed to act a user to the FTP server?? My internet doesn't have static IPs, and I think they change every day.  I am trying to first set it up to let it be an FTP server for Windows XP SP2, and then Ubuntu 6.10.

Thanks

---

### Post by TheWizzard on 2007-04-09
to check if proftp is installed, open a terminal and type: 
```
sudo updatedb
locate proftpd | grep bin
```
this should return /usr/sbin/proftpd

there's a lot of help on the internet on setting up an ftp-server with proftpd. just use google. 
check also this tread: 
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

---

