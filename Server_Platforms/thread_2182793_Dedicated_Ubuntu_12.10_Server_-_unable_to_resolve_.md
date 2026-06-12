---
title: "Dedicated Ubuntu 12.10 Server - unable to resolve host &amp; apt-get updates."
date: 2013-10-22
forum: Server Platforms
---

### Post by fe37Mkt on 2013-10-22
I have some experience managing servers.
 
I just ordered a server which came with Ubuntu 12.10 on it. Any attempts at installing packages, updates, or pings all fail. Seems this could all be resolved with a simple name server entry - unfortunately I haven't been able to figure out how to enter nameservers 

ping google.com : UNKNOWN HOST
ping 8.8.8.8 : 0% packet loss (I'm able to ping ip addresses but not resolve URLs)
ping 74.125.224.72 (Google.com's IP) 0% packet loss
ping yahoo.com : UNKNOWN HOST
sudo apt-get update:   Temporary failure resolving 'us.archive.ubuntu.com' (repeats for several other addresses)
sudo apt-get update: W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/InRelease)  (repeats several other URLs)


updating /etc/hosts FAIL
updating /etc/resolv.conf no longer possible; workaround: resolvconf/resolv.conf.d/tail: FAIL
updating  /etc/network/interfaces: FAIL

after updating each of these conf files I restarted networking services. Was I supposed to restart a different service?


Most of the fixes for this are for desktops and not remote administration.

EDIT: SOLVED (which is best practice?)

a. edited  /etc/resolvconf/resolv.conf.d/head 
b. resolvconf -u
c. verify /etc/resolv.conf - WIN

both my **resolv.conf.d/head** and **interfaces *"****nameserver *entries are now displayed in resolv.conf - which of the two is best practice? Is there a better way of solving this?

---

### Post by sandyd on 2013-10-22
> **fe37Mkt said:**
> I have some experience managing servers.
 
I just ordered a server which came with Ubuntu 12.10 on it. Any attempts at installing packages, updates, or pings all fail. Seems this could all be resolved with a simple name server entry - unfortunately I haven't been able to figure out how to enter nameservers 

ping google.com : UNKNOWN HOST
ping 8.8.8.8 : 0% packet loss (I'm able to ping ip addresses but not resolve URLs)
ping 74.125.224.72 (Google.com's IP) 0% packet loss
ping yahoo.com : UNKNOWN HOST
sudo apt-get update:   Temporary failure resolving 'us.archive.ubuntu.com' (repeats for several other addresses)
sudo apt-get update: W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/InRelease)  (repeats several other URLs)


updating /etc/hosts FAIL
updating /etc/resolv.conf no longer possible; workaround: resolvconf/resolv.conf.d/tail: FAIL
updating  /etc/network/interfaces: FAIL

after updating each of these conf files I restarted networking services. Was I supposed to restart a different service?


Most of the fixes for this are for desktops and not remote administration.

```

sudo nano /etc/resolvconf/tail
sudo service resolvconf restart
```

---

### Post by houstonbofh on 2013-10-22
Also, post your /etc/network/interfaces file.

---

### Post by steeldriver on 2013-10-23
AFAIK best practice is to add a 

```
dns-nameservers xxx.xxx.xxx.xxx yyy.yyy.yyy.yyy
```

entry in the appropriate interface stanza of /etc/network/interfaces - and leave the resolvconf configuration files alone

---

