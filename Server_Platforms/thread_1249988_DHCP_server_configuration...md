---
title: "DHCP server configuration.."
date: 2009-08-26
forum: Server Platforms
---

### Post by karthick87 on 2009-08-26
I have installed dhcp3-server and i have configured it..After configuration while starting it i get the following error..

karthick@karthick-desktop:~$ sudo /etc/init.d/dhcp3-server start
 * Starting DHCP server dhcpd3                                                  
 * check syslog for diagnostics.

---

### Post by ExtremeCoolSha on 2009-08-26
Make sure /etc/dhcpd.lease file is created. It's needed to start the dhcpd deamon.Did u configure the /etc/dhcpd.conf file. Here in this file u have to set the domain-name. configure  DNS servers, default & maximum lease times etc. [http://linuxreviews.org/man/dhcpd.conf/](http://linuxreviews.org/man/dhcpd.conf/) is a good place to study about the this file.
And also make the server to start at boot time by changing appropriately in #system-config-services 
(Service configuration window).

---

### Post by karthick87 on 2009-08-26
I haven't created domain..So wat name should i give there.?

---

### Post by zetanuxi on 2009-08-26
Make sure all of the brackets { and } are there and in the right place.
Had the same thing go on. It just wouldn't initialize. Scanned the dhcpd.conf file and sure enough, I missed a bracket. :)

---

### Post by terazen on 2009-08-26
What was in the syslog?

---

### Post by karthick87 on 2009-08-26
How to view syslog?

---

### Post by terazen on 2009-08-26
Run ```
sudo /etc/init.d/dhcp3-server start
``` and then after you get the error that says to check syslog you can look with ```
tail /var/log/syslog
``` or ```
grep dhcpd /var/log/syslog
```

---

