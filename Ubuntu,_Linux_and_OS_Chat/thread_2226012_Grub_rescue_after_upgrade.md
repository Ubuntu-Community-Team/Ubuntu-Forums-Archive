---
title: "Grub rescue after upgrade"
date: 2014-05-24
forum: Ubuntu, Linux and OS Chat
---

### Post by jimfl on 2014-05-24
Yesterday I did what I thought would be a simple upgrade from 13.10 to 14.04. My system was completely uptodate before I started, using a six-month-old Lenovo. Everything was working perfectly. And this was not a dual boot--I have only Ubuntu on the machine.

The upgrade seemed to go smoothly and it reached the end where it said to reboot. Well, I rebooted only to be greeted by a black screen and the cryptic prompt:  grub rescue.

This meant nothing to me. I tried a few commands but nothing was recognized. Finally, I recalled having a grub issue after one other upgrade, as which time I had burned a copy of Boot Repair to a CD. I found that and--after quite a bit of _further trouble_--got Ubuntu to boot again.

Somebody really needs to find out why there are so many issues with upgrading. I can imagine someone new to Ubuntu and trying to upgrade for the first time. What a nightmare that would be!

---

### Post by LastDino on 2014-05-24
Most of these issues are caused by existence of third party packages on existing system, existence of sources not maintained by Ubuntu in update manager and driver compatibility issue due to kernel upgrade or manufacturer pulling his hands out. There is good reason as to why removing these before upgrade considered to be good move. Also, there exist good amount of people who haven't faced any problems with upgrading.

As you've no real unsolved issues you need any assistance on, maybe mark the thread solved or ask mod to move it to chat section?

---

### Post by Bucky Ball on 2014-06-17
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not a support request.

---

### Post by craig10x on 2014-06-17
And any ppas installed should be turned off (they will get knocked out anyway)...I never used the software updater method of upgrading like you did, i have done upgrading by using the iso installer's option to do it directly from the ubuntu iso disc and have found it is very reliable and works well...you choose the automatic option for it to upgrade to the new version and bring over your data and apps as best it can...
It's also much faster then a software updater upgrade...takes usually only a few more minutes then a clean install (depending on how large amount of data it is bringing over for you)...

It usually manages to bring over ALL the data and MOST of the apps...all personal settings are also brought over as well...usually ppas have to be re-installed...so it's a big time saver over a fresh install and having to put everything back on again...It also works best if you haven't done major modifications to your system...

And never had a boot problem or black screen like you did...so suggest you try that method the next time you want to upgrade...
(of course, always back up your important data on an external drive just in case...i use a usb flash drive for that)...

---

### Post by help_me2 on 2014-06-17
I had the same issue after a clean install. Oh well. Contact canonical or deal with it. Complaining in the forums won't fix anything. The developers don't come here to see what issues people are having.

---

