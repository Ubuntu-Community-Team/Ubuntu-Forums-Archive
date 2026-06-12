---
title: "hpet1: lost rtc interrupts"
date: 2010-07-25
forum: Virtualisation
---

### Post by kextyn on 2010-07-25
I am running 9.04 Server x64 with VMWare Server 2.  I usually run Windows VMs but recently started using a Linux VM quite a bit and noticed some issues.  After it had been running overnight it was VERY sluggish the next day.  It was at the point where SSH over the LAN would take 10 seconds to show what I had typed.  A Windows XP VM which I never have issues with was also being incredibly sluggish.  When I looked at the syslog on the host machine I found a lot of this:

> __ratelimit: 46 callbacks suppressed
hpet1: lost 7 rtc interrupts
hpet1: lost 8 rtc interrupts
hpet1: lost 8 rtc interrupts
hpet1: lost 4 rtc interrupts
hpet1: lost 3 rtc interrupts
hpet1: lost 6 rtc interrupts
hpet1: lost 3 rtc interrupts
hpet1: lost 8 rtc interrupts
hpet1: lost 7 rtc interrupts
hpet1: lost 5 rtc interrupts


The Linux VM was running a LAMP stack and I noticed that anytime I did something on a website it was running (Jinzora) would cause those to pop up in the syslog.  Even powering on the VM would cause it to show up.  The VM was Ubuntu 9.10 Server, and I have since tried 9.04 Server with the same results.

I found a post on the VMWare site saying they were able to fix it by putting "hpet" in the menu.lst but that hasn't changed anything.

Any idea how I can fix this?

---

### Post by dcstar on 2010-07-25
> **kextyn said:**
> I am running 9.04 Server x64 with VMWare Server 2.  .........
Any idea how I can fix this?

Did you receive a kernel update and then recompile VMware server successfully?

---

### Post by pasbanrule on 2010-12-13
I also have a "you are no supposed to be here" redirection page for any directory that I don't want people have FTP-like HTTP access... once, I accidentally discovered a friend's resume/CV in one of his sub-directories. I think any directory without index.html or index.php automatically have get an FTP-like html interface (if you know what I'm talking about)... like /images/ directories, which I believe most websites will have. A bit of a side-question... is there a technically correct or easier way of preventing such "unauthorized" access to these directories? I can't quite figure out a way with permissions, since for most of those directories, you'll need to set it readable by public for them to access the contents (e.g. images, javascript, etc).

---

### Post by joedoe123 on 2011-03-23
I dont know of any other way of restricting access to the directories other than what you already mentioned setting FTP permissions.

---

