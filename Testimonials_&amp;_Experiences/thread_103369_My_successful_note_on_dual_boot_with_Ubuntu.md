---
title: "My successful note on dual boot with Ubuntu"
date: 2005-12-14
forum: Testimonials &amp; Experiences
---

### Post by t_huankiat on 2005-12-14
After some weeks of puzzle about why my dual boot of windows and suse doesn't work with my IBM recovery partition (Now I realize it might not be the problem of SUSE), I decided to redo the whole process again. and when I did, I decided to change to ubuntu (and I'm glad I did).

OK, I'm not that experience enough to analyze which distro is better than another. So far the comparison probably were just the installation experience. Maybe SUSE is good and powerful or something, but it just takes too many CDs and the process is definitely longer than m process to install Ubuntu. Does this count? LOL!

And talk about Slackware, I'm not even capable of fixing the X window configuration to make it works with my display card, not to mention the wirelss setting @_@

So far my experience with Ubuntu has been great. and of course I like my "tri-boot" with XP, Ubuntu and the IBM Recovery partition, thanks to the help from reading the archives from this forum!

I had posted my dual booting steps in my blog:
[Success note 1]("http://huankiattang.blogspot.com/2005/12/success-notes-1-my-installation.html")
and 
[Success note 2]("http://huankiattang.blogspot.com/2005/12/success-notes-2-retraced-steps-to-dual.html")
but not sure if my steps are fully accurate. Any comment is appreciated!;)

---

### Post by saphil on 2005-12-14
Ubuntu has a very slick dual boot.

I teach Basic Linux at a college in Duluth GA USA and my students use removable hard drives, which they can configure however they want, so most dual boot Win server 2003 (for their windoze classes) and Fedora Core 4 (for their Linux courses).  Most of my students have absolutely no problem with the dual boot process.  I managed to triple-boot WinServer2003, Fedora Core and Breezy.  When I added Breezy, I did not put in a second /boot and swap file, and Breezy uses the /boot and swap files from Fedora Core.  I do not seem to be able to add any more OSes above that.  The Partitioning Tool in the Install packages refuses to make a 4th partition "Primary".  Oh well.

---

### Post by Stevenseb on 2006-02-26
I have had very good success dual booting Ubuntu 5.10 w/ Windoze XP. I am tryng to create a tri-boot introducing FC4 into the mix and I am having trouble with this one. First I installed FC4 after windows and the install went fine but after the reboot GRUB hangs up and no boot menu.

I just proceeded to install Ubuntu hoping that the Ubuntu boot menu setup would detect the presence of FC4 just like XP but no joy. Ubuntu only detected XP and upon reboot of Ubuntu to complete the installation the GRUB threw Error:18 which I have not found exactly what that is. I tried to re-install Ubuntu once again and same thing. 

So, I am now trying to re-install FC4 and this time I manually entered the Ubuntu partition in the FC4 boot setup screen and it is still installing so, I hope this will work. I thought maybe saphil could offer some advice on how this tri-boot process has succeeded in the past.

I am installing onto a 30gb drive in a Comaq m700 w/750mhz processor and each operating system has successfully installed seperately on this system I just would like to avoid the need for 2 seperate hard drives.

Any help is much, much appreciated!!!

---

