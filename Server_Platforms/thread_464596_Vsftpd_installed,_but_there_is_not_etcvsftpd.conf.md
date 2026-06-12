---
title: "Vsftpd installed, but there is not /etc/vsftpd.conf"
date: 2007-06-04
forum: Server Platforms
---

### Post by junk2k06 on 2007-06-04
I am throughly puzzled in my current installation glitch with ftp. First , Ubuntu latest server edition installed Vsftpd by default. Config was too complicated, so I removed it via "apt-get remove". Later, manually removed the /etc/vsftpd.conf and /etc/init.d/vsftpd files as well. Now, everytime I install vsftpd (by apt-get or aptitude does not matter much), all I get is /usr/sbin/vsftpd with no trace of the config file as well as file that should be in /etc/init.d.
Any help is highly appreciated.
Thanks.

---

### Post by jiffyloose on 2007-06-08
same problem here....I remove and tried to reinstall...help no vsftpd.conf.

---

### Post by Bachstelze on 2007-06-08
Remove the package completely (i.e. with --purge) :

```
sudo apt-get remove --purge vsftpd
```

And then reinstall it :

```
sudo apt-get install vsftpd
```

---

### Post by jiffyloose on 2007-06-08
THANKS!!!!!!!!!!!  I always forget about the --purge.  It worked!

---

