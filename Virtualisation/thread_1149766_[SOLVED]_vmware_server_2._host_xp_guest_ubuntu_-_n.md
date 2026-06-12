---
title: "[SOLVED] vmware server 2.* host: xp guest: ubuntu - networking problems"
date: 2009-05-05
forum: Virtualisation
---

### Post by milanm on 2009-05-05
Hello everyone,

Yesterday I thought I'd give vmware server 2.* a ride. I have been using 1.* for some time, but this new version went through massive changes.

Setup: xp host, kubuntu 9.04 64-bit guest. 

Symptoms: ethernet doesn't work. Bridged, Hosted, NAT mode, doesn't matter. 

Cause: More likely than not, your vmnet0 network is not configured to point to a proper physical device on your host (xp) machine.

Solution: in XP, click on start -> all programs -> vmware -> vmware server -> Manage Virtual Networks.

Most people (me included) go by default to "Vmware Server Home Page" (a web browser window) which is a MISTAKE that ended up costing me a few hours and lots of frayed nerves. 

Once in "Manage Virtual Networks", I:

1) Clicked on a tab called "Automatic Bridging" and DISABLED it by removing a check-mark. 

2) Clicked on a tab called "Host Virtual Network Mapping" and under VMnet0 pull-down, I selected the ethernet adapter on my laptop. Notice by default that this was set to the wireless card, which is an idiotic choice. 

I made no further changes on XP. Restart your guest instance and hopefully your problems are solved.

If they are not, here are other pointers that I tried yesterday in guest instance (kubuntu). I didn't undo them because they were too much work, but if the above doesn't work for you, try these work-arounds:

* I read somewhere that bridged adapter must have a MAC address range starting at 00:50:56:00:00:00. So I went into vmware browser page and clicked on the guest os, then in "summary" clicked on "network adapters -> edit" and then under "MAC address" set it to "manual" and typed in 00:50:56:00:00:10.

* If you are working with wireless, I heard that RPC for 802.11 spec doesn't allow wireless to have a virtual MAC address. So it appears that wireless bridge networks are out of the question. Wireless NAT or host-only might work, though. This needs to be confirmed.

* I also modified /etc/udev/rules.d/70-persistent-net.rules script to add this line:

SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:50:56:00:00:10", ATTR{type}=="1", KERNEL=="eth*", NAME=="eth2"

In case you're wondering, the reason I have eth2 up there is because I tried various eth0 and eth1 before giving up. 

I think that's all I did on guest, prior to realizing that problems are on host. As I wrote above, I didn't undo any of these steps, because I've suffered enough ;)


Hope this helps ton of people out there with this problem. I really wish VMware had a bit better manuals. I also wish they didn't tack on "virtual" prefix to EVERYTHING that they do. Usability really becomes an issue and the only plus-side is that your staff sounds a bit more important when throwing phrases around.

---

