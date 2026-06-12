---
title: "Karmic (64 bit), VirtualBox, and USB Reading/Writing Problems"
date: 2009-12-27
forum: Virtualisation
---

### Post by wangsuda on 2009-12-27
For those who run Karmic AND VirtualBox 3.1.2 and are having trouble getting your virtual systems to read and write to USB devices, here's an easy way to permanently fix that problem. This post is an addition to [http://ubuntuforums.org/showpost.php?p=6122145&postcount=4](http://ubuntuforums.org/showpost.php?p=6122145&postcount=4) by bodhi.zazen and is Karmic-specific.

1. Go to System>Administration>Users and Groups
2. Click on your user name and unlock
3. Click on "manage groups"
4. Scroll down until you see "vboxusers." Click on it and then on "Propertiers"
5. Click on any and all accounts you want to add to VirtualBox. This would generally be you. Don't click on root
6. Close everything
7. Reboot

TAH DAH! You are done! Now USB devices can be read and written to!

---

