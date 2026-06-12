---
title: "Ghost for linux ??"
date: 2005-11-14
forum: Server Platforms
---

### Post by dbee on 2005-11-14
Is there a special program I can use to copy one linux installation exactly on to another computer, and maybe even expand the partitions ??

I've heard about ghost from symantec, but is there a linux OS equivalent ?

---

### Post by frodon on 2005-11-14
If the 2 computers have differents hardware it will never work.
However if the 2 computer are the same or compatible you can do that using [mondo]("http://www.mondorescue.org/about/about.html"), norton ghost or simple scripts : [http://www.ubuntuforums.org/showthread.php?t=81311&highlight=backup](http://www.ubuntuforums.org/showthread.php?t=81311&highlight=backup)

---

### Post by blu.gecko on 2005-11-14
I looked up this application for a windows enviornment called bart pe, the site says it is completely legal, I found a bartpe with norton ghost built into bart pe, this tool may come in handy for you. I found it on another site, the file was re-labeled and zipped so the host site would not delete it, they delete iso images for some reason I am not sure of.

[http://www.megaupload.com/?d=0TFG2XQR](http://www.megaupload.com/?d=0TFG2XQR)

hope it helps.

---

### Post by ngms27 on 2005-11-14
I think the Knoppix CD comes with a tool to do this as does a Linux utility CD I downloaded and now cannot locate!

Ghost will also do this.

JonnyT

---

### Post by coach-x on 2005-11-14
I have used ghost for Unix for several years without any problems.  You can then use a program like parted to expand your partitions.

[http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)

---

### Post by john_c on 2005-11-14
Partimage is on the system rescue cd and on others.  It works well with most any file system.

[http://www.sysresccd.org/](http://www.sysresccd.org/)

John_c

---

### Post by jdong on 2005-11-14
Yes, do an rsync over ssh of the entire /, while the other system is booted on a LiveCD.

I've had **excellent success** doing this on completely different hardware, given a bit of effort (installing a 386 common-denominator kernel beforewards, re-running **dpkg-reconfigure xorg-xserver** afterwards to reconfigure X11).

---

### Post by frodon on 2005-11-14
Really !

could you explain a little bit more how to do that, i'm interested.

---

### Post by jdong on 2005-11-14
Sure. Give me a day or two or three to get it all typed up; it's an involved process to explain.

---

