---
title: "bug installing torrentflux"
date: 2007-04-09
forum: Server Platforms
---

### Post by jmvidalvia on 2007-04-09
While installing torrentflux, i get this message:
mysql said: ERROR 1049 (42000): Unknown database 'torrentflux'
It seems to be already reported as a bug [here]("https://launchpad.net/ubuntu/+source/torrentflux/+bug/93307").
Solution seems to create previously a torrentflux database, and try to install it again (¿?) but I have no idea of mysql.
I verified mysql is installed and running, and already created root paswords.
So, how should I create that torrentflux database?
Many thanks!

---

### Post by jmvidalvia on 2007-04-09
I solved it by using wget instead of apt-get.
But now everything is installed, I don't know how to go on.
Some sites say to open a browser, but I installed it in a server with no X, so...
I am supposed to be able to acces torrentflux from any pc in the lan, but I don't know how.
Thanks!

Solved: so easy!

[http://ip_of_my_server/torrentflux_2.3/html](http://ip_of_my_server/torrentflux_2.3/html)

:)

---

