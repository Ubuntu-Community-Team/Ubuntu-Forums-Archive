---
title: "Monitoring Ubuntu systems"
date: 2009-11-04
forum: Server Platforms
---

### Post by boondocks on 2009-11-04
We have a few 8.x and 9.x Ubuntu Desktop (GUI) and Server (CLI) systems.
They are located in different remote locations.
They all have access to the internet, but they are behind NAT/firewalls.
We want to be able to monitor each Ubuntu system.

We would like:
[LIST]
[*]To install some kind of a client component on each Ubuntu system.
[*]To have each client component periodically contact our server.  Web server, maybe?
[*]So we know that each Ubuntu system is alive and kicking.
[*]Most importantly, we would like to "see" these results via a GUI.  Because a few non-technical people will be keeping an eye on this.
[/LIST]

What kind of package/utility would you recommend?

---

### Post by cariboo on 2009-11-04
Have a look at [cacti]("http://www.cacti.net/"), it may be what you are looking for.

---

### Post by Xipher on 2009-11-04
[Zabbix]("www.zabbix.com") Might be a good choice.

---

### Post by GCoffee on 2009-11-06
[Webmin]("http://webmin.com/") May also do the trick (:

---

### Post by Thirtysixway on 2009-11-06
Not sure if it's in your budget, but using landscape from Canonical may be useful

---

