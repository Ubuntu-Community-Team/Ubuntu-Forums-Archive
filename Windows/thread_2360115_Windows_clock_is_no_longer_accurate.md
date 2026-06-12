---
title: "Windows clock is no longer accurate"
date: 2017-05-02
forum: Windows
---

### Post by vineyridge on 2017-05-02
I installed for Ubuntu to dual boot with Windows XP, SP3 about a week ago.  The Ubuntu clock is accurate with my local time on boot, but the Windows time is wrong at each boot.

I went to search and found a thread where Ubuntu forced the Windows clock to Greenwich Mean Time and the answers gave a terminal string for forcing the whole computer on local time.  It didn't work for me.   It took me about five tries to type the command correctly; but the final one seemed to be accepted, and I got a blinking cursor with nothing else.  A couple of hours later, I booted to XP and it was five hours off.  It always seems to be five hours off.  Where I personally am is usually 6 hours off Greenwich Mean Time--at least I think I am.  I'm CDT at the moment, so maybe there is only a 5 hour difference.

Any thoughts on how to fix this?  I'd appreciate it.

---

### Post by LastDino on 2017-05-02
You "really" shouldn't be using XP SP3 as it is now absolute (since 2014 I think). Also, Ubuntu doesn't "force" the time change, actually system retrieves and keeps track of system up and down time and whenever you boot it is used to set your time accordingly.

After quick googling I found this, it may work for you, though please no XP..
[https://askubuntu.com/questions/169376/clock-time-is-off-on-dual-boot](https://askubuntu.com/questions/169376/clock-time-is-off-on-dual-boot)

---

### Post by Bashing-om on 2017-05-02
vineyridge; Hello;

What release are you running ? As, upstart/systemd makes a difference .

[INDENT][INDENT]not to confuse the issue
[/INDENT][/INDENT]

---

### Post by Perfect Storm on 2017-05-02
Moved to Windows forum

---

### Post by Frogs Hair on 2017-05-02
Easier to fix from the Ubuntu side.

[http://www.webupd8.org/2014/09/dual-boot-fix-time-differences-between.html](http://www.webupd8.org/2014/09/dual-boot-fix-time-differences-between.html)

---

