---
title: "Can this be done ? Ethernet adapter to be hidden from the host but visible to guest ?"
date: 2010-06-04
forum: Virtualisation
---

### Post by Mandrake2002 on 2010-06-04
Hello everyone ,

I am running a Windows XP host and a Ubuntu guest on virtualbox . What I would like to do is to connect the host to the network via wifi and use NAT on the guest to connect to the same network . I would like the guest OS to share the host's ip address . So bridged networking is not an option . Now if my understanding is correct , when I use NAT in both VMware and VirtualBox,  this appears as a wired connection on the host XP .  Now this creates a problem for me . I would like to connect an external X-86 board on to the guest via ethernet . But if I do this , the host XP detects a wired LAN and disconnects the Wifi . 

So , is there anyway to overcome this issue ? Can I hide the ethernet adapter from the host but make it visible to the guest ? Or if you could give me some other ideas it'd be really great .

Thanks a lot

---

### Post by littlepeon on 2010-06-06
what you are suffering from is Windows/your computer automatically assuming that you want either a wired or wireless internet and not both.
have seen various posts about this, sometimes it requires a bios setting switch to allow both.
within XP you will have to manually set your network settings for your wired connection--if you let XP autoconfigure them, it will shut off your wifi.
this can  be achieved by either setting your wired card up manually (using a static ip-not a dynamic one(dhcp)) or by telling XP you want to use ICS (internet connection sharing).
i have not done this in years so you can google/ask here how to do that.
you may have to set up your wired connection on another subnet to achieve your goal.

---

