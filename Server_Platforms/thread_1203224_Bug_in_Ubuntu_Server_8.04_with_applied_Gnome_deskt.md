---
title: "Bug in Ubuntu Server 8.04 with applied Gnome desktop"
date: 2009-07-03
forum: Server Platforms
---

### Post by dragos2 on 2009-07-03
This is most probably a Gnome bug ?

There are 8 processors (2 x Quad Xeon = 2 CPU with 4 cores each = 8 core ~ 8 processors) and system monitor reports this incorrectly between tabs. As you can see
the firs picture correctly reports the number of CPU's and the second not.

Where should be further reported?

Ps: Other tools and the kernel correctly detects the number of processors.

[IMG]http://i43.tinypic.com/291gius.png[/IMG]

[IMG]http://i39.tinypic.com/10wv1ig.png[/IMG]

Sorry for high resolution.

---

### Post by windependence on 2009-07-03
Run top in a terminal and then press the number '1' key while it's running to show all processors. What does it show?

On a secondary note, why run a nasty heavy GUI on a box you are clearly running headless? There are far less intrusive monitoring tools that have a web interface you can use if you want fancy graphs and charts. I mostly use top, ntop, and htop for monitoring, but there are also packages like Zabbix, and Nagios that don't require a heavy GUI to be installed. There is a reason Ubuntu doesn't install a GUI on the server version.

-Tim

---

