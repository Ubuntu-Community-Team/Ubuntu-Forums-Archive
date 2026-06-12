---
title: "FAILED upgrade 12.04 - 14.04"
date: 2016-02-09
forum: Ubuntu, Linux and OS Chat
---

### Post by shawnblanchette on 2016-02-09
I am not really looking for help of any kind... I figured out a way through this failed upgrade. But first, before I vent a bit and complain, I DO want to THANK ALL THE THOUSANDS OF VOLUNTEERS that make UBUNTU & other LINUX distros POSSIBLE!!!  I don't (no one does) have the right to complain since Ubuntu is (and likely will) always be free, although Ubuntu (organization) and Canonical (I love that name) may have paid and subscription services, which is vital to the survival of any organization.  I also don't think I have the right to complain about the best operating system, and, in my opinion, the best distro in existence!  I've been an Ubuntu user (and Linux) since the early 2000's, although I've used Linux from time to time in the 90's.  Let me tell you, I don't get frustrated with my Linux systems anywhere near as much as any Winblows PCs I've had, and still have.  The business I am starting will ban the use of Windows for every day tasks.  I was willing to use Windows on VM for those rare times when Windows is required.


Now for my gripe and complaint.  I have installed 14.04 on other systems without a problem.  This PC (older) I ran 12.04 for the last three years or so, mostly without problem.  I've been able to keep Linux systems running for months without a restart.  Start it and forget it.  I decided to do an upgrade because suddenly my panels (classic mode) disappeared when switching workspaces (TTYs, really).  That started on Sunday night.  Reboots didn't help.  Updates didn't help.  Reinstalling the desktop didn't help.  So, I decided to upgrade the distro.  That has fixed problems in the past.  Well... This time it didn't... and it caused me roughly four hours of work... Fortunately with Linux, there's always things that can be done so you don't lose personal settings and files.  With Windows, there's not much you can do when there's a failed install or upgrade.  You just have to format again.  Formatting is not possible for me right now...  I am 2 TB short in HDD space to move my files in order to save them.  I have around 1 TB free, but need 3 - 3.5 TB.  


After the upgrade my PC wouldn't boot.  Not at all.  It booted to the splash screen and that's it.  I had to purge most DEs (okay, I had a few), remove XORG and X11 on top of all DEs (literally right down to terminal).  Then manually reinstall X11, XORG, gnome, and ubuntu-desktop (which installed Unity, which I don't like).

---

### Post by Bucky Ball on 2016-02-09
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by grahammechanical on 2016-02-09
I will agree that a fresh install will fix problems. I have used that method myself. I am not so sure if upgrading to a newer version is the way to fix problems. I certainly would not recommend that as a sure method of fixing problems. 

I have seen a few forums posts where the user has not solved the problem or ended up with different problems by upgrading. And I have seen many posts where the user starts off by saying that the upgrade failed in some way.

On the other hand I have tested upgrades. If I remember correctly I tested upgrading from 12.04 to 14.04. Or was it 10.04 to 12.04? It does not matter as I was testing upgrading a default install. Upgrading from one default install to another is the safest upgrade. Linux is too easily customisable to make anything other than upgrading a default install risk free. In my opinion.

Regards.

---

### Post by mastablasta on 2016-02-11
There are a  few errors made here. And a few misunderstandings.

> **shawnblanchette said:**
> 
 This PC (older) I ran 12.04 for the last three years or so, mostly without problem.  I've been able to keep Linux systems running for months without a restart.
I am curious how can you successfully update a desktop system without a restart?! thss suggest unpatched kernels as well as other desktop things that need to be restarted in order to be updated.

> 
  Start it and forget it.  I decided to do an upgrade because suddenly my panels (classic mode) disappeared when switching workspaces (TTYs, really).  That started on Sunday night.  Reboots didn't help.  Updates didn't help.  Reinstalling the desktop didn't help.  So, I decided to upgrade the distro.  That has fixed problems in the past.  
a botched non working desktop  might or might NOT be fixed with updated. things are more likely to go wrong. especially since old configuration files that might have been previously corrupted are then used after the upgrade.

> 
After the upgrade my PC wouldn't boot.  Not at all.  It booted to the splash screen and that's it.  I had to purge most DEs (okay, I had a few), remove XORG and X11 on top of all DEs (literally right down to terminal).  Then manually reinstall X11, XORG, gnome, and ubuntu-desktop (which installed Unity, which I don't like).
it might need only a boot parameter ([https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)) to be able to boot. doesn't mean anything is wrong with the OS.

Upgrades are tested on stock install that uses programs from repositories. as soon as you start adding various drivers manually, adding PPA's, making some major OS modifications.... upgrade might fail. luckily there is another option - you can do a fresh install, tell installer not to format the disk, so the old OS just get's overwritten. then you just need to sort the config files. some old ones might be used some might need some tweaking. 

some people go even a step further - they create separate home partition and then format the OS partition to do the fresh reinstall at will and when necessary.

upgrade process also progressed quite a bit in last few years. now PPA's are automatically disabled and drivers uninstalled before upgrade.


If you do not like Unity you can try Mate (like the old Gnome) or  use Xubuntu desktop instead. so far I prefer Kubuntu and KDE (personal preference). on older PC's I am quite fond of Xubuntu. 

Another option is also Cinnamon (found in Linux Mint) which also looks nice and more traditional desktop like.

---

