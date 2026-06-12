---
title: "Server &quot;health&quot; displayed on console after boot"
date: 2011-03-14
forum: Server Platforms
---

### Post by NIT006.5 on 2011-03-14
Fairly simple bash script that I've developed on and off over the last year. Mostly suited to small/medium sized networks that use a single Ubuntu server to do multiple tasks, although the principle could be applicable in almost any situation. Most of my clients don't have their own in-house IT staff, so this was primarily developed to give the clients a simple on-screen display after boot, as well as to alert me to any obvious problems on their servers. Also handles switching of redundant links on routing boxes and quite a bit more.

This has been an entirely private project up to now, so there are likely to be many bugs if its applied to a scenario that I haven't considered (and I'm already aware of several bugs that I need to work on). Hoping for lots of feedback though, and all suggestions/criticisms welcome.

This obviously only applies to Ubuntu Server and is NOT designed to be run on systems with a GUI (yet). The script can be found here for anyone interested: 

[https://launchpad.net/kmon-health](https://launchpad.net/kmon-health)

---

