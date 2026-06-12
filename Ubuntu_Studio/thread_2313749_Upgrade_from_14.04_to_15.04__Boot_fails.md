---
title: "Upgrade from 14.04 to 15.04  Boot fails"
date: 2016-02-15
forum: Ubuntu Studio
---

### Post by peter233 on 2016-02-15
I am new to Linux. I have a Toughbook CF-30 with Ubuntu 14.04 which I tried to upgraded to 16.04.I did the upgrade thru Ubuntu's tools.
  But now Ubuntu will not boot correctly. When I start Linux get a light grey login screen once logged in I get an error occurred message.
 No matter what I choose I get the desktop but that's all. I have left the laptop on for hours and that's all I get.  I can get in to the grub but 
the kernel seems to be missing.  

  1 Is there a way to install or find the kernel version from the GRUB? I have been searching but all the suggestions don't seem to work.
  2 I have tried to boot from a USB with no luck. I have tried UUI and rufus, also tried different drives.
  3 How can I wipe out the system and start over?
  
Thanks in advance for any assistance

---

### Post by TheFu on 2016-02-15
Welcome to the forums.

Whoa!!! You are new to Linux and trying to run alpha software?!!!!?????
   Bad idea, dude.

"Newer" is NOT "better."  

People new to Linux should run LTS releases only.  That is 14.04 today.  After 16.04 is released in April, it would be smart to wait a few months for support to get in-place and a few huge, missed, bugs to get fixed. So plan to install 16.04 sometime in June.  That is my plan and I've been using Linux since 1993-ish.  Do not run non-LTS releases without a really, really, really, good reason.  BTW, 15.04 support ended last month.  Only LTS releases get 5 yrs of support. There is a support schedule for releases AND for the specific kernels inside each release, so be careful when switching to a newer kernel, because that will like reduce 5 yrs of support to 6-9 months only. 
[http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life) has a nice graphic explaining it. Be sure to scroll down to see the kernel release support too. THAT is a little harder to understand, but just as important.  14.04 LTS required the use of a 3.13.x kernel. 3.16.x and 3.19.x kernel support is months, not years.  Just be aware of this stuff.

Sure, you can start over.  Reinstall  using a DVD or flash drive and in the storage setup, tell it to format each of the partitions.  This may only be available in the "**do something else**" options - I only use that, so don't know what the other options actually do. Sorry.  
Some links that google found from "reputable" sources:
* [https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
* [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
* [http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html) - BTW, this guy wrote a great "Linux for Windows people" article. It is the first thing I tell folks to read to get an overview of how Linux is different from Windows and OSX. HIGHLY recommended.

Fixing grub isn't hard for intermediate Linux users, but may be extremely difficult for someone new to Linux. You can try installing and running "boot-repair" package from a liveCD boot and it usually fixes stuff, but somethings it doesn't.   
Another option: If you have a LUG, the folks there should be able to help with this in less than 5 minutes.  
OTOH, re-installing is an important skill to learn, so doing it 5-10 times would be good.  Practice makes perfect. There's lots of new stuff, unfamiliar stuff there, so seeing it a few times will be good.  Best to practice this stuff before the system is full of the critical cat photos and music files. ;)

I don't know what UUI is and have never used rufus.  I usually just **dd** an ISO onto a flash drive and boot that.  dd is very powerful, very simple, very dangerous and very stupid.  If you tell it to do something bad, it will.  For people running Windows, I usually have them use YUMI to make flash drives.  You can also use **mkusb** which is an Ubuntu tool. I don't recall if there is a package or not. Sorry.

Hope you don't mind the first few paragraphs, but if someone didn't tell you these things, how would you learn? Hopefully other people will chime in and provide their opinions about this stuff too.  It is good to get multiple options and opinions.

---

### Post by oldfred on 2016-02-16
May be video related?
Did you try a Intel video boot parameter. You add like nomodeset.

 # Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

 
Very much agree with ThFu comments on not upgrading too soon. I run 14.04LTS as main working system. Still have 12.04LTS on 10 year old laptop that will get retired soon. And only install 16.04 into another / (root) partition to see if it works on my system.

---

