---
title: "Cannot install VMwareTools on guest Ubuntu8.04 under WindowXP"
date: 2008-10-02
forum: Virtualisation
---

### Post by homocow on 2008-10-02
Pretty new to Ubuntu, so decided to set 1 up in VMware to try it out.

OK, so i setted up VMware6.5.0 under WindowXP SP3, installed Ubuntu8.04 normally (not easy install, i told vmware to make a blank disk first, then installed ubuntu from a cd), after installation i wanted to install VMwareTools, but after clicking VM->Install VMware Tools Installation, nothing happens, there was no disk, nothing happened... except VM->Install VMware Tools Installation greying out...

I tried going under su, and mount /dev/cdrom /mnt/cdrom as the VMware tutorial told me, but it jst says medium not found.... and i tried searching around for VMwareTools, and i found nothing...

Been struggling on this for over 3hrs now... and still nothing... help...

---

### Post by EchoBeach on 2008-10-02
The thing about VMware Tools is that it uses a 'virtual CD' - if that's the correct way to describe it.
If the CD/DVD drive that you have configured for the VM is not empty, it will mask the 'Tools CD.
As long as the drive is empty, you should see a folder open or an icon appear on the desktop when you select 'VM' -> 'Install VMWare Tools'.
Echo

---

### Post by homocow on 2008-10-02
I am pretty sure my cd/dvd rom is empty, i physically assigned a rom for VMware, and not let it auto detect. At first i thot it was the cd/dvd rom from powerIso and Daemon that might be conflicting with it, but after removing them, and remaking a "machine" and reinstalling ubuntu, still no luck...

Frustrating when a program doesnt do anything when its suppose to do something... at least gimme an error to search for ><...

---

