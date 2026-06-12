---
title: "Freeradius only responding in debug mode?"
date: 2009-01-27
forum: Server Platforms
---

### Post by shadoxity on 2009-01-27
Hello Everyone,

I am fairly new to linux and unbuntu and have been trying to setup coovachilli and freeradius with mysql.

Following this guide however having some problems with freeradius.

[https://help.ubuntu.com/community/WifiDocs/CoovaChilli#Install%20Radius%20server%20and%20Database](https://help.ubuntu.com/community/WifiDocs/CoovaChilli#Install%20Radius%20server%20and%20Database)

If i start freeradius with "sudo /etc/init.d/freeradius start" it says ok, but it will not respond to any requests.

If i stop it and then do "sudo freeradius -x" in debug mode it will respond to requests.

What am i not doing here to get it to work as the daemon or whatever you call it?

Cheers

---

### Post by shadoxity on 2009-01-28
Bump,

any ideas?

---

### Post by Yvan Seth on 2009-01-30
Howdy,

I experienced the same symptoms as you, though my problem is probably different since I cause it by mucking about with self-built packages.  Anyway....

I switched from an Ubuntu Intrepid FreeRadius, to a self-rolled package (to explore OTP support), and then back again.  After doing this I ended up with a problem with the same symptoms as yours.  The cause was a missing /var/run/freeradius directory.  Something must have gone wrong with the overall install layout because of my mucking around.

The error was adequately shown in /var/log/freeradius/radius.log (which took me a while to work out, as I was expecting something in /var/log/syslog|daemon.log|...etc.)  Check that log file if you haven't already.

-Yvan

---

### Post by shadoxity on 2009-02-01
> **Yvan Seth said:**
> Howdy,

I experienced the same symptoms as you, though my problem is probably different since I cause it by mucking about with self-built packages.  Anyway....

I switched from an Ubuntu Intrepid FreeRadius, to a self-rolled package (to explore OTP support), and then back again.  After doing this I ended up with a problem with the same symptoms as yours.  The cause was a missing /var/run/freeradius directory.  Something must have gone wrong with the overall install layout because of my mucking around.

The error was adequately shown in /var/log/freeradius/radius.log (which took me a while to work out, as I was expecting something in /var/log/syslog|daemon.log|...etc.)  Check that log file if you haven't already.

-Yvan

that was it!

THanks heaps. life saver :D

---

