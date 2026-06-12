---
title: "Intel 915GM Video Drivers and Utils for System76 Gazelle"
date: 2007-11-17
forum: System76 Support
---

### Post by rmemm on 2007-11-17
I have a System76 Gazelle 2300 that I purchased a couple of years ago.  I have a question about the Intel 915GM graphics adaptor support.

In particular -- I've always had problems mode switching between the VGA D-Sub port and the LCD screen.  The Fn+F2 key is suppose to cyle through the modes of LCD, VGA, and LCD+VGA.  Sometimes this works -- sometimes it doesnet.  Same for using the i810switch package functions.  Often I just have to reboot to get reasonable video back after using the Fn+F2 key.

How is this suppose to work?  Are here any updates or fixes I could apply that would make this work well?  I'm still using the Dapper that came on this.  Would a later Distribution be better?

Thoughts?

Rob

---

### Post by thomasaaron on 2007-11-19
**This comuter is using Dapper**

If I were a betting man, I'd bet that it works fine before suspend or hibernate, but does not work well after suspend or hibernate?

Hibernate sometimes does funky things to function key mapping. If this is the case, it would probably be best to file a bug report on it: [https://launchpad.net/system76](https://launchpad.net/system76)

---

### Post by rmemm on 2007-11-19
I tried after a fresh boot, I still have problems.  

*  If you don't have the monitor plugged in and you use Fn+F2 to switch modes your screen get's totally corrupted, and you can't get it back.  You have to use a reboot to do that.
*  If you plugin the monitor -- even after it's had the corrupted screen problem, you can use Fn+F2 to get back to cycling through modes, and that works.
*  The problem with the this cycling -- it looses the cursor on your LCD screen -- though it seems to be there at least sometimes in the CRT only mode.  You have to reboot to solve that problem.
*  I've tried to use i810switch too.  That seems to have some problems -- for one often the CRT video quality is not as good for some reason.

The only certain way to get a good video config seems to be to setup everything, then reboot then you get good dual screen support.  Switching seems to have issues.

My question I think is a general one -- are there better drivers/utilities availbe today than 2 or 3 years ago when this was configured.  If so -- then I might install and configure them.  Or if it's in a future OS release -- I'll just wait for Ubuntu 8 LTS.

This has always been a bit strange -- and especially it causes problems when one want's use the laptop for a presentation for example.

Rob

---

### Post by thomasaaron on 2007-11-19
I just looked back at your initial post and realized that you said you've always had this problem.

I don't know of any driver improvements that would have fixed that. Although it is possible that it now works in Gutsy.
A lot has been fixed since Dapper.

---

### Post by rmemm on 2007-11-19
OK thanks.  I think I'll wait for Ubuntu 8 LTS and see if things improve.  Then I may dig in myself and see what's going on if that does not work -- or post and issue on the ubuntu hardware database.

Before I did either of these -- I just wanted to know if there was a known/standard solution.

Rob

---

### Post by palintheus on 2007-11-19
Any reason you want to stick with LTS?

---

### Post by rmemm on 2007-11-19
My life it too busy to constantly be changing distros.  At work I have 3 systems, and home another 4.  If I was being cutting edge all the time -- my life would be constant upgrades.

Also -- I've never really looked into how easy it is to upgrade and what issues it causes -- meaning what do I have to fix.  Use to be for linux it was always best to do a clean install as the upgrade procedures never really worked.  If I have to do that -- it's a lot of work.

Rob

---

