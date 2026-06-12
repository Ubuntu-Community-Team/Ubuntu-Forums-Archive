---
title: "Get rid of Plymouth!!!"
date: 2010-07-16
forum: Testimonials &amp; Experiences
---

### Post by chaanakya_chiraag on 2010-07-16
I had just installed Lucid a few days ago and I went to boot up my laptop.  After quite a few lines, it froze before the usual message "Plymouth killed error 2" or something like that.  Every time it booted, either it would freeze or give me that error.  Since the boot froze before the message, I correctly determined that Plymouth was the problem.  I completely disabled Plymouth by moving the plymouth* files in /etc/init.d and /etc/init and running ```
sudo update-rc.d ... remove
``` for everything containing Plymouth and presto!...Ubuntu now boots like it used to in Karmic except WAY faster!

---

### Post by armandh on 2010-07-16
the problem may not have been the [whatever]

when one has a unique problem i suspect bad disk read on install
assuming the disk has worked well on other installs.

---

### Post by chaanakya_chiraag on 2010-07-16
It's now started working perfectly and the only change I made was to deactivate Plymouth. By the way, Plymouth is the boot-up splash screen.

---

### Post by armandh on 2010-07-17
hardware again suspect
I have 8.04 on 2 old desktops with inadequate video for compiz
I hnow because if one deletes compiz from later ver. they work too
or software
the splash screen may be corrupt

---

### Post by chaanakya_chiraag on 2010-07-20
Software - maybe. Hardware - no way. This was on a brand new laptop that was customized for Linux - specifically, Ubuntu. Also, the above-mentioned fact refutes the idea of a hardware malfunction.

---

### Post by j7%&lt;RmUg on 2010-07-23
Heh, plymouth is fast for me.

Must be your hardware.

---

### Post by eveningsky339 on 2010-07-24
Karmic and Lucid boot times are nearly identical for me, maybe a bit faster in Lucid.  Both are fairly fast anyway.

---

### Post by JustinR on 2010-07-27
> **nisshh said:**
> Heh, plymouth is fast for me.

Must be your hardware.

+1

I've never had problems with Plymouth - it looks beautiful to me, but I think that Ubuntu shouldn't have hard dependency's on Plymouth so users can uninstall it if wanted.

---

### Post by chaanakya_chiraag on 2010-07-27
Would Plymouth hang if you were to remove all the themes?

---

### Post by JustinR on 2010-07-28
> **chaanakya_chiraag said:**
> Would Plymouth hang if you were to remove all the themes?

I'm not sure but it you want you can disable it.

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

Go to method 2 if you want to disable it.

---

### Post by migel_wimtore on 2010-08-06
Nice one chaanakya_chiraag!!!

I had changed the plymouth theme to spinfinity as i thought the default totally ugly but after changing it x would completely freeze after one loop of the splash animation. 

Your tip sorted it for me.

And boot does indeed appear faster, bonus!

Seems a software issue to me, plymouth had been working up till that point on the same dell inspiron 1300 with celeron m.

---

### Post by mutantstargoat on 2010-08-08
So the second method is to use startup manager.  And I get to add even more stuff that I don't want in order to do so.  Great.  How about just having an option for people who don't want a "graphical boot animation while the boot process happens in the background".  You know, like we've had up until the point this damned thing was made unremovable.

:-\"

---

### Post by JustinR on 2010-08-08
> **mutantstargoat said:**
> So the second method is to use startup manager.  And I get to add even more stuff that I don't want in order to do so.  Great.  How about just having an option for people who don't want a "graphical boot animation while the boot process happens in the background".  You know, like we've had up until the point this damned thing was made unremovable.

:-\"

If you're so unhappy about, customize Ubuntu the hard way - figure out how startup manager disables Plymouth and do it yourself. There's your option for people who don't want a graphical boot animation.

---

### Post by mutantstargoat on 2010-08-08
That's certainly a much better idea than the old way.

---

### Post by JustinR on 2010-08-08
> **mutantstargoat said:**
> That's certainly a much better idea than the old way.

[http://ubuntuforums.org/showthread.php?t=1457388&page=2](http://ubuntuforums.org/showthread.php?t=1457388&page=2)

---

### Post by chaanakya_chiraag on 2010-09-17
I'm just wondering...what did people do **before** the GUI was invented when fsck or mountall needed to give you a prompt?  It would prompt you on the command prompt, right?  Why can't the same thing be the case now?  That is, why can't it detect that Plymouth is not installed/running and it should ask you on the tty itself?  I feel like that's the solution to the problem of what happens when Plymouth isn't running.

---

### Post by chaanakya_chiraag on 2010-09-28
Shouldn't that work?  I mean, that SHOULD be what happened before Xorg came along and created the whole GUI thing on Linux, right?  Just a thought...

---

