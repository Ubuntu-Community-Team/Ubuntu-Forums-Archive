---
title: "Virtualbox - Ubuntu host+guest, host unreachable"
date: 2009-04-30
forum: Virtualisation
---

### Post by ccf on 2009-04-30
I have two network interfaces, one wired and one wireless (eth0/ath0).  I have the Ubuntu guest (Virtualbox 2.2.2) using bridged networking on eth0 with a static IP set within the guest on the same subnet as the host (and other machines on the LAN).  However, the two cannot reach each other.  Any attempt to ping or traceroute across the bridge results in "Host unreachable" errors (!H in traceroute).

Presumably, the interface doesn't actually need to be plugged in to an actual network at all times in order for the guest and host to be able to see each other, being as they're on the same machine and ifconfig reports the interface as up anyway.

Host and guest are both jaunty.

---

### Post by DuGi on 2009-05-05
it is probably a problem with the 2.2.x version. bridged networking doesn't work for me too...

---

### Post by GoodPanos on 2009-05-05
I believe you have to set the guest on the same network interface as the host.  So if you are connecting via the wireless then you have to bridge the guest on the wireless interface too.

I had the same issue.  If I bridged the guest on the lan interface but was connecting on the wifi interface on the host, it would show up as disconnected on the guest.

---

### Post by DuGi on 2009-05-07
i dont use wifi interface. I noticed the strange thing - when i try to ping guest from another guest it's working but there is no connection between host and guest.

---

### Post by Perryg on 2009-05-07
In VBox 2.2.2, if you want it to work both as a connected and non-connected interface you must setup (2) adapters in the settings for the guest.  Set one to host only and the other to bridged. Then setup the guest accordingly.

---

### Post by DuGi on 2009-05-07
thx! it's working now :)

---

### Post by bumdeal2 on 2009-05-07
how do u creat a thread

---

### Post by ccf on 2009-05-08
> **Perryg said:**
> In VBox 2.2.2, if you want it to work both as a connected and non-connected interface you must setup (2) adapters in the settings for the guest.  Set one to host only and the other to bridged. Then setup the guest accordingly.

My understanding is that host-only networking is exactly that - the guest cannot see the outside world.  It's important that the guest is on the same network as other machines on the LAN while connected and that I don't have to fiddle with the networking settings on the guest when I move the guest between hosts.

---

### Post by Perryg on 2009-05-08
> **ccf said:**
> My understanding is that host-only networking is exactly that - the guest cannot see the outside world.  It's important that the guest is on the same network as other machines on the LAN while connected and that I don't have to fiddle with the networking settings on the guest when I move the guest between hosts.

You are correct, but what if you need for the guest to get to the internet?  That is the reason for the second virtual adapter.

---

### Post by ccf on 2009-05-08
> **Perryg said:**
> You are correct, but what if you need for the guest to get to the internet?  That is the reason for the second virtual adapter.

I still don't get what you're saying.  I have a bridge on the wired adapter (generally can't bridge the wireless when using public networks) - I don't see how adding a host-only adapter would allow it to see the outside world when I'm on the move.  The single most important things for me are working samba and not having to change the guest configuration.

---

### Post by Perryg on 2009-05-08
In your case you can create 3 adapters if needed.  One for the NAT, one for Bridged and one for host-only.  Then you would just need to select the right one in the guest.  The host can switch (I assume) it is the guest that has the problem.  You can have the host only and one of the Internet connections live at the same time.  You can even pull off having all three going at the same time.  Point is as long as they were setup before hand all will be available to the guest OS and no need to reboot the guest.

Say for instance the Host samba and the guest are important.  These can be connected host-only and no problem.
But you still need the public Internet on the guest, so NAT assigned to the second adapter for the wireless card would be the setup for that.  Both of these can be run at the same time and work well together.

OK that still leaves the wired adapter right?  Well create the third adapter and assign it to the hard wired adapter in the host.  With this setup you should just connect to what ever you need when it is available.  The only problem is occasionally some OSs complain at first.  I have seen a few times when people had to do a dhclient -r in ubuntu to get renewed leases, but they say that it is rare and fine for what they want.

Bottom line is try it out.  Mix and match as you see fit.  You have up to 8 adapter settings for the guest in VBox.  4 in the GUI and 4 more for the CLI. If it does not work for you then back it down to only one adapter and that will be that.

---

