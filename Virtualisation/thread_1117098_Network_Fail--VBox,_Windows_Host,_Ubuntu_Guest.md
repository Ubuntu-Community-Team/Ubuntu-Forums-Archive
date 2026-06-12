---
title: "Network Fail--VBox, Windows Host, Ubuntu Guest"
date: 2009-04-05
forum: Virtualisation
---

### Post by ShinHadoken on 2009-04-05
Ok guys, I've got VirtualBox running in Windows Vista. Ubuntu Intrepid as guest. Here's the problem: when I try to do any network activity on the guest, such as load a web page, all of a sudden my wireless connection says "Local only" (guest sees a wired eth0 interface that's always connected). Somehow, I'm getting knocked off the internet. After I reboot, everything's fine though. It's a Toshiba Satellite A205-S5804 laptop, with a Realtek RT8187B wireless card. Any suggestions?

Thanks a ton,

-SH

---

### Post by Perryg on 2009-04-05
> **ShinHadoken said:**
> Ok guys, I've got VirtualBox running in Windows Vista. Ubuntu Intrepid as guest. Here's the problem: when I try to do any network activity on the guest, such as load a web page, all of a sudden my wireless connection says "Local only" (guest sees a wired eth0 interface that's always connected). Somehow, I'm getting knocked off the internet. After I reboot, everything's fine though. It's a Toshiba Satellite A205-S5804 laptop, with a Realtek RT8187B wireless card. Any suggestions?

Thanks a ton,

-SH

Could you provide the network information for the host and the guest?
Also are you using HIF or NAT in VBox?
It might help to determine what the problem is.

---

### Post by ShinHadoken on 2009-04-05
Well, the wireless network is WPA encrypted, and VBox is using NAT.

---

### Post by Perryg on 2009-04-05
> **ShinHadoken said:**
> Well, the wireless network is WPA encrypted, and VBox is using NAT.

Well that's a start.

Now some more information if you please.

The address, subnet mask, gateway that type of thing.  (See Below)
What we are looking for here is to make sure that you do not have a network conflict.

Also unless it is necessary that you use NAT on the guest I would suggest that you use Host Interface instead.  Easier and not as much to dink with.

HINT:
Windows  ipconfig /all
*NIX   ifconfig

Post outputs here.

---

### Post by ShinHadoken on 2009-04-05
Actually, I've solved the problem. I tested this out by using my ethernet card, instead of my wlan card. Worked like a charm, which tells me that VBox is having a rough time with the wireless driver (which doesn't surprise me, my card isn't very well supported. Until Intrepid, I used to have to use a patched driver while I was dual-booting) So, I'm going to use VBox on my desktop, which is hardwired.

---

### Post by Perryg on 2009-04-05
> **ShinHadoken said:**
> Actually, I've solved the problem. I tested this out by using my ethernet card, instead of my wlan card. Worked like a charm, which tells me that VBox is having a rough time with the wireless driver (which doesn't surprise me, my card isn't very well supported. Until Intrepid, I used to have to use a patched driver while I was dual-booting) So, I'm going to use VBox on my desktop, which is hardwired.

That works!

After I looked over your info. I was going to suggest that you should look at the adapter if all looked right.
Say if you do have any more problems and need help just remember to post as much information as you can.  It is really hard to help without it.

---

### Post by ShinHadoken on 2009-04-05
Alright, thanks. I'm a network guru (hence why I use Linux) but I don't have a lot of experience with this virtual machine thing, so I'm not quite sure what information is relevant and what isn't. I'm glad I got it to work though. I have to have Winblows--err, Windows, hehe, because of work, and IT won't let me dual-boot. But, now that they've got virtualization, I can have Ubuntu still. Thanks for your help! I knew if there's one place I can find help with this problem, it's the Linux community.

---

