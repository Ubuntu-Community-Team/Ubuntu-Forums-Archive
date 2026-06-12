---
title: "How do I use this forum? Help setting up server, please"
date: 2008-01-16
forum: Server Platforms
---

### Post by bsc_boss on 2008-01-16
I am looking to setup a Linux box to replace my Windows DNS server.  I have already setup the server version of fapper drake and installed bind9.  I have about 20 domains that I am primary to, and also have the zone records from my seconday name server that uses some version of Linux.  I would like t know if there is someone out there will to help me get the file stucture in place and make it a caching server like my windows dns server?  Were do I start?

---

### Post by K.Mandla on 2008-01-16
Moved to Servers and Security. :)

---

### Post by r00tintheb0x on 2008-01-16
See [http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p4](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p4) section 9, "DNS Server". It is an EXCELLENT resource.

r00t

---

### Post by bsc_boss on 2008-01-17
i have used the perfect setup to get as far as i have.  my bind9 service is running.  i need to better understand the files and file structure to add all of my primary zones.  a listing of somebodies working dns files that are performing the same tasks as i need to perform would me most helpful.  I am an good copy cat.

---

### Post by koenn on 2008-01-17
have a look at this:
[http://users.telenet.be/mydotcom/howto/linuxsbs/intro.htm#dns](http://users.telenet.be/mydotcom/howto/linuxsbs/intro.htm#dns)
it nothing else, it tells you which files to look for, and what they should look like. If you understand the basics of DNS, you can probably work out the rest from there.

---

### Post by bsc_boss on 2008-01-18
when i open the file /etrc/bind/named.conf, it says to read the file /usr/share/doc/bind9/README.Debian.gz.  this file is displayed in RED, and when opened by cat, vi. nano, it is displayed in ascii characters.  What's up with that?

---

### Post by scorp123 on 2008-01-18
> **bsc_boss said:**
> /usr/share/doc/bind9/README.Debian.gz gz = GNU Zip archive. You should uncompress it first, or if you want to read it directly: ```
zcat /usr/share/doc/bind9/README.Debian.gz
``` That will transparently decompress the archive and display its content ... in this case the 'README' text file.

---

### Post by scorp123 on 2008-01-18
BTW, maybe you are interested to read this too?

" Ubuntu Server 7.10: OpenLDAP + SAMBA Domain Controller "
[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

---

