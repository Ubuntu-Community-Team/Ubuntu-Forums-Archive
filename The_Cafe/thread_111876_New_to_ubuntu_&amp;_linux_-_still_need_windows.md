---
title: "New to ubuntu &amp; linux - still need windows"
date: 2006-01-03
forum: The Cafe
---

### Post by semaj on 2006-01-03
Hello, this is my first post (to any internet forum).

I have setup a dual boot computer with ubuntu and windows 98 SE.  Getting Ubuntu to work was easy - thanks to Ubuntu team!  

Have trawled the various sites re ubuntu and windows emulation, and looks like I should get Wine (mainly to run a CAD program called Datacad LT11).  Unless someone can tell me a better way.

In the synaptic package manager there is a package called winesetuptk - am I supposed to do something with this to install wine?  

Also, my dual-boot computer is really 2 hard drives - one with windows and one with Ubuntu.  How do I get to see the windows hard-drive from Ubuntu and vice versa?

---

### Post by xmastree on 2006-01-03
[QUOTE=semaj]How do I get to see the windows hard-drive from Ubuntu and vice versa?[/QUOTE]Well, to get ubuntu to see your Windows disk, look [**here**]("http://www.ubuntuguide.org/#automountfat").

Getting Windows to see your linux disk... I'm not sure if that's possible. :confused: 
My advice wound be to create a FAT32 partition on it for data to be shared with Windows.

---

### Post by semaj on 2006-01-03
Thankyou for pointing me in the the right direction on how to 'mount' the windows hard drive - it worked.  I'm still getting used to linux terms, and where to find answers to questions.  I will bookmark the unofficial guide to Ubuntu.

---

### Post by Lord Illidan on 2006-01-03
From Windows you can view ext2 and ext3 type Linux partitions. Check around on the net. ReiserFS, I am not so sure about, though.

---

### Post by bonzodog on 2006-01-03
It's also worth pointing out that there is some VERY good software for CAD in linux.
The client you use is not available for linux, but there are some good ones listed here: [http://www.linuxlinks.com/Software/Graphics/CAD/index.shtml](http://www.linuxlinks.com/Software/Graphics/CAD/index.shtml)

---

### Post by TimelessRogue on 2006-01-03
There is a program that will allow you to explore linux file systems called, of all things, "explore2fs.exe" ... haven't got the reference handy, but do a quick search of the internet for that file name and you will find any number of sources.

---

