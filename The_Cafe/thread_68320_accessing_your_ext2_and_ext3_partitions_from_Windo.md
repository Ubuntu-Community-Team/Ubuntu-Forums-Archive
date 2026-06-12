---
title: "accessing your ext2 and ext3 partitions from Windows (with write permission aswell)"
date: 2005-09-22
forum: The Cafe
---

### Post by fig_jam_uk on 2005-09-22
Hi gus just to let you all know i found this handy app that works realy well in windows to access your linux partitions, its real easy to install and uses a GUI for you to decide which drive letters to assign etc...

hope it helps somebody out... 

[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

---

### Post by Goober on 2005-09-22
While I was in Windoze for about 5 minutes todsy (I haven't gone to the dark side, just needed to look at a site which needed some Java Environment Runtime crap that Linux apparently doesn't have installed), I DLed this, and it might be useful to save all my important files onto my Windows HD, then wipe my 5.04, and install 5.10 onto, then hopefully put everything important back onto 5.10.  Thanks!

Provided I get it working . . .

---

### Post by BWF89 on 2005-09-22
Actually it's spelled "Windows".

---

### Post by Goober on 2005-09-22
[QUOTE=BWF89]Actually it's spelled "Windows".[/QUOTE]
 Quite aware of that, thanks, but whenever I go into Windows, I can't help but notice how much slower things run there.  OpenOffice takes longer to open in Windoze then in Ubuntu, same with Firefox, etc.  Therefore, Windows is slower then Ubuntu, so it earns the name Windoze.

I am not intentionally bashing Windoze or M$ here, i am just stating that Windoze runs slower for me then Ubuntu, thus the name.  I didn't mean any offense, of course :)

---

### Post by fig_jam_uk on 2005-09-22
[QUOTE=BWF89]Actually it's spelled "Windows".[/QUOTE]

i think theres an enemy in our midst  :grin:

---

### Post by 23meg on 2005-09-22
[QUOTE=fig_jam_uk]i think theres an enemy in our midst  :grin:[/QUOTE]
 i think it's just the latest "let's not bash windows" trend in effect ;)

no offense; i endorse it as well.

---

### Post by darkoptix on 2005-09-22
This is great if it works like it says, I need for music and video transfering to windows. Sony sucks at making software, so this is a great step in making linux a bigger part of my life.

---

### Post by drizek on 2005-09-22
if anyone needs reiserfs read support, you can use rfstool together with yareg.

---

### Post by benplaut on 2005-09-23
[QUOTE=Goober]I am not intentionally bashing Windoze or M$ here[/QUOTE]

saying that is  :roll: 

not to flame or anything, but it's generally not cool to bash any OS, except maybe those >1kb punchcard OS's  :wink:

---

### Post by XQC on 2005-09-23
Now I need something that can read XFS partitions as well... but didn't find anything so far.

---

### Post by zenwhen on 2005-09-23
[QUOTE=Goober]Quite aware of that, thanks, but whenever I go into Windows, I can't help but notice how much slower things run there.  OpenOffice takes longer to open in Windoze then in Ubuntu, same with Firefox, etc.  Therefore, Windows is slower then Ubuntu, so it earns the name Windoze.

I am not intentionally bashing Windoze or M$ here, i am just stating that Windoze runs slower for me then Ubuntu, thus the name.  I didn't mean any offense, of course :)[/QUOTE]

Having cute little names for other OS's is one of the things that makes the Linux community look bad. It is immature and pointless. This isn't Slashdot. This doesn't fly here. Linux can stand on its own merit.

---

### Post by gw90se on 2005-09-23
> Having cute little names for other OS's is one of the things that makes the Linux community look bad. It is immature and pointless. This isn't Slashdot. This doesn't fly here. Linux can stand on its own merit. 

Well said. While I am not a fan of Bill Gates nor Microsoft and even thought in the beginning I fell into the name habit, I have tried to change the way I refer to them. After reading a lot of articles across the net, I found myself wondering how old the author was with all of the name calling.

BTW, thanks for the link. I still have to use Windows at work, but now I can access my ext partitions. Great!

---

### Post by Posterus on 2007-07-24
> **fig_jam_uk said:**
> Hi gus just to let you all know i found this handy app that works realy well in windows to access your linux partitions, its real easy to install and uses a GUI for you to decide which drive letters to assign etc...

hope it helps somebody out... 

[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

thanks i really needed this, i have a dual boot running Ubuntu 7.04 and Windoze XP and go on xp alot because i make beats with a program on there but often dont want to restart and go into Ubuntu just to get a file...also if i may ask (sorry for the lazyness i dont feel like searching through the forums for this) is there a way to run doze programs on linux?

---

### Post by Nekiruhs on 2007-07-24
> **Posterus said:**
> thanks i really needed this, i have a dual boot running Ubuntu 7.04 and Windoze XP and go on xp alot because i make beats with a program on there but often dont want to restart and go into Ubuntu just to get a file...also if i may ask (sorry for the lazyness i dont feel like searching through the forums for this) is there a way to run doze programs on linux?
You do realize that this thread is 2 years old?

---

### Post by forrestcupp on 2007-07-24
> **Posterus said:**
> thanks i really needed this, i have a dual boot running Ubuntu 7.04 and Windoze XP and go on xp alot because i make beats with a program on there but often dont want to restart and go into Ubuntu just to get a file...also if i may ask (sorry for the lazyness i dont feel like searching through the forums for this) is there a way to run doze programs on linux?

Try Hydrogen for making beats.

It seems like I tried this once and it didn't work well with ext3.  Can anyone verify that it does work well with ext3?

---

### Post by marco123 on 2007-07-24
I think it does work with ext3.  It won't work in Vista though.

---

### Post by init1 on 2007-07-24
> **Posterus said:**
> thanks i really needed this, i have a dual boot running Ubuntu 7.04 and Windoze XP and go on xp alot because i make beats with a program on there but often dont want to restart and go into Ubuntu just to get a file...also if i may ask (sorry for the lazyness i dont feel like searching through the forums for this) is there a way to run doze programs on linux?
Wine runs win apps. It won't work for all.
```
sudo apt-get install wine
wine thewindowsappthatyouwanttorun.exe
```
If you really need to, you can get Crossover Office. It runs apps better then wine, apparently. But you have to pay for it. 
[http://www.codeweavers.com/](http://www.codeweavers.com/)

---

