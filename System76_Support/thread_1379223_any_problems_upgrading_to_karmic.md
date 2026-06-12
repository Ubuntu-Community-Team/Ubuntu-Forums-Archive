---
title: "any problems upgrading to karmic?"
date: 2010-01-12
forum: System76 Support
---

### Post by black_ice=cream on 2010-01-12
[FONT=Verdana]I was just wondering, I'm a *little* sketchy upgrading to 9.10 after what happened about the wireless... And so I thought I'd ask you guys: Have you had **any** problems upgrading? If so, what, how u fixed it, etc... thanks :]

haha, sorry I forgot: Starling! lol.
[/FONT]

---

### Post by thomasaaron on 2010-01-12
From a tech support perspective, the upgrade to 9.10 has been fraught with problems pertaining to grub, audio, keyboard and mouse problems, etc...

Make sure you're well backed up before upgrading, just in case you end up having to do a fresh install.

If you have a Starling, follow the instructions on the first post of this thread...
[http://ubuntuforums.org/showthread.php?t=1330531](http://ubuntuforums.org/showthread.php?t=1330531)

If you have a different system, follow these instructions...
[http://knowledge76.com/index.php/KarmicUpgrade](http://knowledge76.com/index.php/KarmicUpgrade)

Regardless of what system you have, it is a good idea to run this command after upgrading (which will decrease the likelihood of many potential problems)...

sudo apt-get install grub-pc

...and then reboot.

---

### Post by black_ice=cream on 2010-01-12
I have a question. If GRUB fails, *how* do you do a fresh install?! Because you can't log in to download the ISO! [this DID NOT happen to me just wondering]

---

### Post by thomasaaron on 2010-01-12
You could create a bootable USB disk before upgrading, or you could use another computer to create one.

---

### Post by bruvverjak on 2010-01-15
I watched patiently and read all of the pertinent posts before upgrading my Starling to karmic.  I'm glad I waited until I got a good sense of what to expect before attempting the upgrade.  Having said all of that, everything went without a hitch. 

I really want to thank all of those who contributed.  If a noob like me can do this, anyone can.

---

