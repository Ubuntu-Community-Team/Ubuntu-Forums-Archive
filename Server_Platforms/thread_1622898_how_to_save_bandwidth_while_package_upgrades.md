---
title: "how to save bandwidth while package upgrades"
date: 2010-11-16
forum: Server Platforms
---

### Post by tapas_mishra on 2010-11-16
Here is a mail in /var/mail/root which I received in my server logs
[http://paste.ubuntu.com/532866/](http://paste.ubuntu.com/532866/)
I see same packages downloaded many times again and again.
The servers which are upgrading are total 5 (4 virtual machines and one host)
so is there a way I can save bandwidth on this sort of setup.

---

### Post by CharlesA on 2010-11-16
Use apt-cacher-ng. Most of the documentation I've found is old and outdated, but it might be worth looking into.

[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)

---

### Post by pricetech on 2010-11-16
Build a mirror:

[http://ubuntuforums.org/showthread.php?t=1512787](http://ubuntuforums.org/showthread.php?t=1512787)

---

### Post by ian dobson on 2010-11-16
Hi,

Install a squid http proxy? It'll only cache packages that are used, unlike apt-mirror that caches/mirrors all packages from the remote server.

It should be possible to configure apt-get to use a proxy see [http://ubuntuforums.org/showthread.php?t=96802](http://ubuntuforums.org/showthread.php?t=96802) or maybe [http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html](http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html)


Regards
Ian Dobson

---

