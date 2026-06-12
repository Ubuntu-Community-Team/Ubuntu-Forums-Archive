---
title: "upgrade to precise causes squid to no longer start"
date: 2012-05-02
forum: Server Platforms
---

### Post by mistamidget on 2012-05-02
Just did an upgrade from oneiric to precise and squid now no longer autostarts.
The previous version was OK but now I have to login and do a "service squid3 start"
I have added this to rc.local and it's now running on reboot but this is obviously not the correct way to do it I'm guessing!

---

### Post by mistamidget on 2012-05-02
OMG was no-one else using squid in oneiric server :-(

---

### Post by sourchier on 2012-05-09
Squid has alot of problems on Precise.

Here is one solution:

[http://ubuntuforums.org/showthread.php?t=1975704&highlight=squid3+on+boot]("http://ubuntuforums.org/showthread.php?t=1975704&highlight=squid3+on+boot")

And a bug report:

[https://bugs.launchpad.net/ubuntu/+source/squid3/+bug/978356]("https://bugs.launchpad.net/ubuntu/+source/squid3/+bug/978356")

And potentially more problems:


[http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/]("http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/")


I just use the following in /etc/rc.local

/bin/sleep 10
#
/usr/sbin/squid3 restart

And squid works on boot.

---

