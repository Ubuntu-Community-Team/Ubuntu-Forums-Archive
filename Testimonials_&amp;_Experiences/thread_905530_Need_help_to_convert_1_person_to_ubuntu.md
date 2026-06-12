---
title: "Need help to convert 1 person to ubuntu"
date: 2008-08-30
forum: Testimonials &amp; Experiences
---

### Post by milanvora2 on 2008-08-30
Hi

I've just got my brother to try out ubuntu. the only issue he is facing is that the wpn111 usb network adapter is not initialized at each reboot..

I have to manually do rmmod ndiswrapper then re-plug the stick and then modprobe to re-initialize the wireless.

This is currently a showkiller for him.
Any way you guys would know how to solve this problem

---

### Post by pytheas22 on 2008-08-30
Does the problem only occur after each reboot?  If so, you can write an init script to rmmod ndiswrapper and reinsert it.

If the crashes occur randomly while your brother is using the computer, I don't know of a solution.  I know of several other people who experience the same problem, but we were not able to figure out a solution other than to unplug the adapter and reinsert it.  Unfortunately the WPN111 is one of the worst pieces of wireless-networking hardware that a Linux user can own.

---

### Post by Crafty Kisses on 2008-08-30
The weird thing is my friend has this card and it works perfect under Hardy, very weird. :(

---

### Post by milanvora2 on 2008-08-30
It only happens at boot.
I'm noticing that the ndiswrapper is not getting loaded.
If i do a lsmod, it's not visible.
After manually starting it, it works.
It's only a problem at boot. After that it seems for the time being to work fine.

---

### Post by pytheas22 on 2008-08-30
> It only happens at boot.
I'm noticing that the ndiswrapper is not getting loaded.
If i do a lsmod, it's not visible.
After manually starting it, it works.
It's only a problem at boot. After that it seems for the time being to work fine. 

ndiswrapper not getting loaded is a common problem.  Run this, which should fix it:
```

echo 'ndiswrapper' sudo tee -a /etc/modules
```

Let me know if that does it.

I'm glad to hear that you don't experience the bugginess with the WPN111 that other users report.  I think it might only occur when connecting to WPA networks (you're not on WPA, are you?).

---

### Post by starcannon on 2008-08-30
> **milanvora2 said:**
> Hi

I've just got my brother to try out ubuntu. the only issue he is facing is that the wpn111 usb network adapter is not initialized at each reboot..

I have to manually do rmmod ndiswrapper then re-plug the stick and then modprobe to re-initialize the wireless.

This is currently a showkiller for him.
Any way you guys would know how to solve this problem

Buy him a usb wifi from this list [[COLOR="DarkOrange"]**[SIZE="3"]Supported USB Wifi List[/SIZE]**[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") for a gift. Be sure to choose one that does not require ndiswrapper.

He's happy, your happy, a win only card is in the trash can where it belongs. And the world is a better place ;)

---

