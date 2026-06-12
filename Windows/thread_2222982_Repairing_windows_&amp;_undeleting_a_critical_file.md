---
title: "Repairing windows &amp; undeleting a critical file"
date: 2014-05-08
forum: Windows
---

### Post by vas2 on 2014-05-08
I am fairly experienced with computers, but made the mistake of trusting google and friends when I found a file called kbdcap.sys throwing out errors in my event log and googling for answers finding many many people saying it was kido worm and not a legit extremely important file.  I'm not 100% sure this is the issue but now that I seen a file saying it controls your input devices, I'm fairly possitive that is the file I need to restore.

Long story short, I deleted the file from C:\Windows\SysWOW64\drivers.  I also installed malwarebytes and did scans and found my system to be fairly clean, which is odd considering it takes 10 minutes to boot with selective boot enabled and many things turned off.  I guess that's just Windows for you eh?

I need some help getting this file back, either through means of un-delete, or download.  I am looking through my hard drive's temp files and firefox cache because I had uploaded it to a site to scan it, so I'm hoping a copy might still exist somewhere.  It is doubtful though.  :/

As per test, I was able to use cmd in windows recovery area to rename the install directory of Malwarebytes to something else, to prevent it from being allowed to boot anymore.  This did not fix the issue, which is the reason I think this .sys file is my only hope now.  System restores do not work, they are all corrupted or deleted, as it says each time.  Can anyone help me?

---

### Post by oldos2er on 2014-05-09
Doesn't appear to be an Ubuntu support question; moved to Other OS/Distro Support.

---

### Post by QIII on 2014-05-09
Although I'm sure someone here would be quite happy to help if they can, you might get an answer more quickly on a Windows forum.

---

### Post by vas2 on 2014-05-09
Well, the only way I can use the machine right now is through teamviewer or ubuntu.  Since teamviewer is laggy and takes a lot of connection even if you do it in the same house, I am using Ubuntu.  I wish I could get it to run off of a flash drive properly too.  :/

I'm about to give up and just have to assume I need to reinstall.  I mean my machine is not infected at all, it has no operating system issues in the slightest, other than the fact that I can watch 2 and a half episodes of Merlin by the time it finishes starting up.  (Exageration, it's about 10 min startup time)  I really don't want to reinstall a perfectly functional system that is 2 and a half years old now.

As an update, I've used ntfs undelete on Ubuntu and discovered files from 2 years aago can be undeleted, but for some reason the last deleted file I deleted, is gone and can't be recovered.  :/  Damn Windows for making the important one irricoverable and leaving stupid useless crap.

As a side note, I used the Ubuntu Live CD off of a 4GB flash drive to install Ubuntu to a 32GB flash drive.  I decided the first time I'd give 2GB swap and 30GB ext4 mount point /.  When I tried to boot from that flash drive, I just got a black screen and a white underscore dos cursor at the top.  It just kept sitting there doing nothing, twice in a row.  Any ideas?  I just installed it to the same drive again, mount point / same file system except this time no swap space, kinda useless with 8GB of ram and the fact that I'm never going to use that much RAM in Linux anyway.  Can't even use that much in Windows unless I play Space Engineers which takes up 6GB of memory.  I'll try to load the flash drive again here soon.  I wanted to be able to save my settings and stuff.

---

