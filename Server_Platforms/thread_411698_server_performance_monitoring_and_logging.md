---
title: "server performance monitoring and logging"
date: 2007-04-17
forum: Server Platforms
---

### Post by gregbrant on 2007-04-17
Hi,

i've got a web application (LAMP environment) running on an Ubuntu box and i need to benchmark the lifecycle of the app.

i need something that is going to monitor CPU / Memory / Disk usage over a period of hours and do something useful with the data like generate graphs and whatnot...

i've been googling for hours looking for linux performance monitor but i cant find anything that fits the bill.


any ideas please.

thanks alot

Greg

---

### Post by tone77 on 2007-04-17
Cacti is what you are looking for. It is in apt, so it is easy to install and also easy to config.
[http://cacti.net/](http://cacti.net/)  look here documentation.

---

### Post by greg_brant on 2007-04-17
now all i need is a way template to log the CPU 
(intel Ubuntu box)

---

### Post by tone77 on 2007-04-17
have you tried the "ucd/net - CPU Usage" template.  It can be found under 

devices -> <hostname> -> Create Graphs for this Host -> graph templates drop down

---

