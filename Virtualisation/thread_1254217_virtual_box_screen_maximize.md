---
title: "virtual box screen maximize"
date: 2009-08-31
forum: Virtualisation
---

### Post by Mia1990 on 2009-08-31
Hi,
I am running VirtualBox the newest version on ubuntu 9 with win xp as a guest when i maximize win xp i only have a small area to work in this would not be a problem but i run autocad while in school and i don't want to use the full screen mode it does not work good.I had it working before but dumb me had to reinstall xp and i have not been able to get it working that way again.Can someone help me please

---

### Post by Chrus on 2009-08-31
Do you have guest additions installed?

---

### Post by Mia1990 on 2009-08-31
yes and the nvidia drivers

---

### Post by rliegh on 2009-08-31
Maybe try it in 'seamless mode'? (you can switch back and forth using the host+l keycombo).

You're sure you reinstalled the guest additions when you reinstalled XP?

---

### Post by Perryg on 2009-08-31
Your description indicates that the guest additions either are not installed or they failed to install correctly.  Start the guest and then click the devices tab at the top left of the guest window and then click unmount the CD/DVD, then click install guest additions.  When done reboot the guest.  If all goes well you should see the GA icon at the lower right part of the guest window.  Then you should be able to use the (host + F) to toggle full screen on and off.

---

