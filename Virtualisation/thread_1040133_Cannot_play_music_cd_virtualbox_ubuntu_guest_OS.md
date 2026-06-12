---
title: "Cannot play music cd virtualbox ubuntu guest OS"
date: 2009-01-15
forum: Virtualisation
---

### Post by wah fun on 2009-01-15
Hey all,

I am a newcomer to ubuntu and before I installed it to my hd, I decided to run it in Virtualbox. Everything has worked perfectly except playing movie dvd's and music cd's. After searching for info, I installed VLC and that plays the movie dvd's quite well. But, as of yet, I have not been able to play music cd's. I have tried rythmbox and audacious and neither do the trick. I have setup VB according to the manual so, if anyone can offer a suggestion to resolve this problem I would appreciate it.

Thx

System: XP box running at 2 Ghz, 2 meg ram, VB 2.06 (tried 2.1 but it is far too buggy)

---

### Post by HotShotDJ on 2009-01-15
I'm not absolutely certain, but let's try something.  Open up VirtualBox and select, but don't start, your virtual machine.  Click on Settings and then choose CD/DVD ROM.  Check off "Mount CD/DVD Drive" and then select the proper Host Drive.  Underneath that, you should see the option to Enable Passthrough.  Check that off.  Finally, Click OK.  Start your VM and see if you can now play a music CD.

EDIT: I'm just curious... you say that VB 2.1 "is far too buggy."  What kind of problems have you had with it?  I run it on my system (Ubuntu 8.10 host, Windows Vista guest) with no problems at all.

---

### Post by wah fun on 2009-02-28
Thanks for your suggestion but that's the way VB is already setup.

---

### Post by hidannik on 2010-01-03
As of version 3.1.2, VirtualBox does not support audio CDs.  From section 5.7 of the user manual:
[INDENT]In any case, only data media is supported for CD/DVD drives. This means that all data CD formats and all DVD formats can be used in principle. Since host DVD drives refuse to read encrypted DVD video media, you cannot play such videos with the regular CD/DVD drive emulation. You may be able to get it working with the experimental passthrough support described in Section 5.8, &#8220;Writing CDs and DVDs using the host drive&#8221;. **Audio CD and video CD formats are not supported, which means you cannot play such media from a virtual machine.** [emphasis mine]
[/INDENT]I suggest using VMWare Server (1.0.x) instead, it has pretty good support for this stuff.  Unfortunately, its performance is slower, and Windows guests crash when USB 2.0 devices are plugged in, unless you turn off USB 2.0 support in your BIOS.

Hans Dannik

---

