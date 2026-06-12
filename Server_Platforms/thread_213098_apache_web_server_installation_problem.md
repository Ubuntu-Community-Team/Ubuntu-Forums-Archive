---
title: "apache web server installation problem"
date: 2006-07-10
forum: Server Platforms
---

### Post by tiger99 on 2006-07-10
Hi All
I am trying to set up apache2 web server. I followed the server guide and typed 
sudo apt-get install apache2
for installation.

However, I am getting the following error message:

Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  apache2-common apache2-mpm-worker apache2-utils libapr0 ssl-cert
Suggested packages:
  apache2-doc lynx www-browser
The following NEW packages will be installed:
  apache2 apache2-common apache2-mpm-worker apache2-utils libapr0 ssl-cert
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory


Can someone help me resolve this problem?

Thanks

---

### Post by scxtt on 2006-07-10
do you have anything else 'apt' related running - seems apt-get can't get a lock on its archive cache folder ... doesn't seem apache related, just apt related ...

---

### Post by venzen on 2006-07-10
erm, do you perhaps have Synaptic package manager open?

if yes then first close it before using apt-get from the command line.

If there is no other apt related process running (as suggested in the post above) the at the command line type:

```
sudo rm /var/cache/apt/archives/lock
```

to manually remove the stale lockfile.

hope this helps

---

