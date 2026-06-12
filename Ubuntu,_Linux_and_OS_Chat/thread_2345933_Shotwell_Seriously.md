---
title: "Shotwell? Seriously?"
date: 2016-12-09
forum: Ubuntu, Linux and OS Chat
---

### Post by FerryGnu on 2016-12-09
Just started Shotwell for the first time. Got a nice little screen saying what it can do and clicked,"OK"

It was off and running gathering all the pics on my laptop including scanned checks and bank statements.

I never got a chance to define what folders **I** wanted pics gathered from.

Un-installed it fast. Now using gthumb. I am stunned Ubuntu has that Shotwell as the preferred default.

I like the idea of scanning folders with recursion but give me a chance to decide!

---

### Post by v-mark-5 on 2016-12-11
Does it upload them anywhere or does it just find all the ones on the local computer?

---

### Post by FerryGnu on 2016-12-11
Don't know, I killed the process as soon as it showed me what it was doing. Then rebooted and un-installed Shotwell, pronto.

---

### Post by mastablasta on 2016-12-12
is this the issue? 
link: [SIZE=2]https://wiki.gnome.org/Apps/Shotwell/FAQ[/SIZE]
> [h=3]I disabled startup scan but Shotwell still scans all my photos when I run it. Is this a bug?[/h]
No. What&#8217;s disabled in **Edit -> Preferences** is &#8220;Watch library directory for new photos&#8221;. When enabled, Shotwell will auto-import new photo and video files when they&#8217;re added to your Library directory. However, even if disabled, Shotwell will still scan your disk. Why? 
Shotwell scans your library to ensure that all your *existing* photos and videos are still in place. If they&#8217;ve been renamed or moved, Shotwell can detect this and update its internal library. If they&#8217;ve been deleted, Shotwell moves those items into &#8220;Missing Photos&#8221;. 
To skip scanning and monitoring existing items entirely, run Shotwell from the console: 
$ shotwell --no-runtime-monitoring
We&#8217;re considering making this option available in Preferences ([ticket #717149]("https://bugzilla.gnome.org/show_bug.cgi?id=717149")). 


it is probably scanning the photos folder by default?!

If you need Picture organising you can try DigiKam. 

If oyu need a viewere there are some very Light and good ones in the software cneter. I prefer those to default ones. faster to load and easier to manage.

---

### Post by FerryGnu on 2016-12-12
> **mastablasta said:**
> it is probably scanning the photos folder by default?!

Nope, I had the banking pics in their own Folder off Home.

As mention above I am using gthumb which is fine for what I need.

---

