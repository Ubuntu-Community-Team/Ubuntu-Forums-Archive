---
title: "Using raidmon to monitor raid arrays"
date: 2012-02-14
forum: Server Platforms
---

### Post by Sab3r on 2012-02-14
Hello. Yet another Linux file structure/software management noob here. 

I'm trying to set up [COLOR=blue]_[raidmon]("http://freecode.com/projects/raidmon")_[/COLOR] to monitor my raid array (& beep when there's something wrong). raidmon is only available as an .rpm source. I used [color=blue][_alien]("http://en.wikipedia.org/wiki/Alien_%28software%29")_[/color] to make a .deb out of the .rpm and then used [color=blue]_[dpkg]("http://en.wikipedia.org/wiki/Dpkg")_[/color] to install the .deb package. dpkg reports no errors, but it seems to install it straight to the root and raidmon doesn't work. 

What am I doing wrong?

---

### Post by rubylaser on 2012-02-15
mdadm's monitor function does this out of the box (other than the beeping when a drive fails). If email is setup properly, it will immediately send you an alert via email, and the error will show up in dmesg. I don't see the point of the beeping (other than being annoying) if you get an email immediately after a disk falls out of the array.

---

### Post by Sab3r on 2012-02-16
I don't see the point of setting up a e-mail server, just for mdadm alerts, and as I check my e-mail maybe once a week, it isn't a viable solution for me. It's a headless server, I want it to beep when it's done doing something or when there's a problem. 

For instance, I've got it setup to beep two very short beeps when a torrent is finished downloading. 

Is it impossible to compile raidmon for Ubuntu?

---

### Post by rubylaser on 2012-02-16
Maybe someone else will respond, but this is a very old package, and most people with mdadm use email alerts because email is part of daily life for most people, so the alert is basically instant.

---

