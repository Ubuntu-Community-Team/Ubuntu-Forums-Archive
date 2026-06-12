---
title: "Rhythmbox 0.9.1"
date: 2005-11-28
forum: Ubuntu Backports
---

### Post by Sykil on 2005-11-28
Just wondering---how do I go about getting DAAP to work in Rb 0.9.1? I'm guessing I would have to install Avahi or something, but I'm lost after that.

---

### Post by zygis on 2005-12-01
Note that Rhythmbox 0.9.2 is out and is in Dapper already. ;)

---

### Post by doclivingston on 2005-12-01
You will need to install avahi to use it, however I don't think that the packages are compiled with daap support. It's still marked as an "experimental" features because there are a number of potentially nasty issues that can occur - in particular the version of libsoup that ships with breezy can lead to Rhythmbox chewing up 100% of the cpu.

---

### Post by Sykil on 2005-12-02
Ah, I see.  Thanks for your replies!

zygis, I know, but it's not in backports now. Thanks for the heads up, though.  :)

---

### Post by flopsy on 2005-12-05
I put some daap-enabled builds of Rhythmbox here: [http://www.ubuntuforums.org/showthread.php?t=99058](http://www.ubuntuforums.org/showthread.php?t=99058)

Live doclivingston said, it is a bit crashy. daap-disabled builds are there too.

---

### Post by shenki on 2005-12-08
I've been using self-compiled versions of rhythmbox CVS for a while now, with audioscrobbler (which is now considered stable) and DAAP sharing turned on. Living at a residentail Uni college, people were hammering my shared music a fair bit, and it held up fine.

If you can find some builds that work for you, don't hold back :)

---

