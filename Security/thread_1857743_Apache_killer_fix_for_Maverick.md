---
title: "Apache killer fix for Maverick?"
date: 2011-10-10
forum: Security
---

### Post by Entheogen on 2011-10-10
Hello I'm using Ubuntu Maverick on my VPS and I have Apache 2.2.16-ubuntu3.3 installed which is vulnerable to apachekiller exploit.. I just updated latest apache2 packages from repos but apache is still vulnerable. How can I upgrade apache wihtout upgrading whole system? Is there some backport package?

---

### Post by Dangertux on 2011-10-10
You can update via PPA. Or you can use mod_headers or mod_qos to mitigate the effects.

You can use this procedure just in your sources change lucid to maverick : [http://dangertux.wordpress.com/2011/10/05/updating-to-apache-2-2-20-ubuntu-10-04-lts/](http://dangertux.wordpress.com/2011/10/05/updating-to-apache-2-2-20-ubuntu-10-04-lts/)

---

### Post by Entheogen on 2011-10-10
There is no Maverick folder on that PPA.

---

### Post by Dangertux on 2011-10-10
You should just be able to use that PPA for Maverick 

Source : [http://ubuntuforums.org/showthread.php?t=1836110](http://ubuntuforums.org/showthread.php?t=1836110)

---

### Post by Entheogen on 2011-10-10
See for yourself: [http://ppa.launchpad.net/ptn107/testing/ubuntu/dists/](http://ppa.launchpad.net/ptn107/testing/ubuntu/dists/)
apt-get reported errors when trying to update.

---

### Post by Dangertux on 2011-10-10
Hmm.. So it would appear.

This may not work and apt-get may still report an error but try keeping it lucid main instead of changing it to Maverick.

That should upgrade you.

---

### Post by Entheogen on 2011-10-10
> root@bt:~/Desktop# perl apachekiller2.pl [www.server.org](www.server.org)
Host does not seem vulnerable
Yes it works! Thank you!

---

### Post by Dangertux on 2011-10-10
Great glad it worked out :-)

---

