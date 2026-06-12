---
title: "ISPConfig - ever used it?  love it?  hate it?  (and please HELP!)"
date: 2006-01-09
forum: Server Platforms
---

### Post by heftigrat on 2006-01-09
This post is a 2-parter:

1.  Have you ever used [ISPConfig]("http://www.ispconfig.org/index.htm")?  If so, please rate it on a scale of 1 to 10 *, 1 being the lowest, as in it should never be used, ever, as it is terribly difficult to install, configure, and maintain, your system will get h4x0r3d in a minute, and it is the spawn of satan to boot, AND ON THE FLIPSIDE 10 being the highest, as in it is the best thing since winning the lottery, is a breeze to install, configure, and maintain, is secure as h311, and is a godsend to boot.

* OK, nevermind the 1 to 10, I suck at posting polls.

2.  I must admit I am having some ISPConfig woes.  I followed the [How-To]("http://www.howtoforge.com/perfect_setup_ubuntu_5.10") at [HowToForge.com]("http://www.howtoforge.com/") word for word, finally got the [ISPConfig Install]("http://voxel.dl.sourceforge.net/sourceforge/ispconfig/ISPConfig-2.1.2.tar.gz") to work properly (so it said), and I'm still getting this error (attached).  I have, of course, posted in the [HowToForge Forums]("http://www.howtoforge.com/forums/showthread.php?t=1978"), but if anyone here has any Ubuntu-specific advice I would appreciate it.  I'm guessing it has to do with the certificate being invalid or corrupt as the attachment says (duh), but I have no idea how to fix that.  All I can say at this point is "[WTF, mate]("http://www.media.ebaumsworld.com/endofworld.swf")!?"

---

### Post by bluefrog on 2006-01-10
ISP config works fine. make sure your certificates are created correctly. from the kind of message you have it seems that you missed that step

james

---

### Post by heftigrat on 2006-01-10
[QUOTE=bluefrog]...it seems that you missed that step[/QUOTE]

Nope, not at all.  Followed the How-To exactly, as stated above.  Thanks for the input though.  I will attempt to recreate the certificate.

Glad to know it's working for you, thanks for posting.  You get a gold star.  :KS  (<--- I hope that shows up as a gold star, I don't know what this "KS" nonsense is.)

---

### Post by spade_shark on 2006-01-12
Same here, works like a champ...although it was a blister the first several times through the config.](*,)   I guess my typing skills were off?  :D  Don't pull the plug just yet.  Yes to bluefrog's idea.

I think it rocks!  esp on Ubuntu! 8+

---

### Post by heftigrat on 2006-01-12
[QUOTE=spade_shark]Same here, works like a champ...although it was a blister the first several times through the config.](*,)   I guess my typing skills were off?  :D  Don't pull the plug just yet.  Yes to bluefrog's idea.

I think it rocks!  esp on Ubuntu! 8+[/QUOTE]

I have to agree at this point.  All I had to do was [create a new SSL certificate]("http://www.howtoforge.com/forums/showthread.php?t=121"), works great now.  I would have to say it's an awesome package those guys put together.  I can't wait for ver 3!!!

---

