---
title: "Qt"
date: 2006-10-14
forum: Repositories &amp; Backports
---

### Post by j0rg3 on 2006-10-14
Let me begin this message with a bloodcurdling scream.

](*,) 

I am pretty Linux ignorant.  I have tried to GOOGLE my problem, I've looked through the forums because I am sure that somebody has had this problem before but I can't find it.

My desire seemed pretty simple.  I wanted to compile "Hello World" in KDE C/C++ and consider myself a world-class programmer and Linux expert. :p 

Well, I was undaunted by my first problem(s) that you don't really need to hear about.  I am now (hours later) exasperated and this is the cause of my madness.

> 
qt3-apps-dev:
Depends: libqt3-mt-dev but it is not going to be installed


This problem is the apparent solution for this problem:

> checking for Qt... 
configure: error: Qt (>= Qt 3.2) (library qt-mt) not found. Please check your installation!
For more details about this problem, look at the end of config.log.
Make sure that you have compiled Qt with thread support!
*** Exited with status: 1 ***


I cannot find a workaround.  I am not familiar with apt-get and I know how to RTFM.  If I knew *which* was the right manual to read.

I've added repositories (for Backports) -- I have defaulted back to the list suggested in unbuntu_demon's [post]("http://www.ubuntuforums.org/showthread.php?t=185758").

I have pushed the only brain cell that I still had on the sane team over with the other two cells.

Somebody, please help?

Thanks,
j0rg3

P.S. All apologies if I have somehow put this message in the wrong place or  otherwise violated nettiquette.

---

### Post by kzutter on 2006-10-14
Looks like libqt3-mt-dev has an unmet dependancy.

Have you tried to install libqt3-mt-dev by itself?

Hopefully it will tell you what the problem is.

Good luck!

---

### Post by j0rg3 on 2006-10-15
I suppose that, in some cases, patience is required.  Today it installed without a hitch.

I have a whole new problem!:-# 

Hopefully I can solve this one without assistance!

Thanks!
j0rg3

---

