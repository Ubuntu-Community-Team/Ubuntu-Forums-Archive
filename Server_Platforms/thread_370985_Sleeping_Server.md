---
title: "Sleeping Server"
date: 2007-02-26
forum: Server Platforms
---

### Post by Uta on 2007-02-26
I have been trying to figure out exactly what is going on with my router and server. All the boxes that are hard-wired, connect anytime they are turned on but the wireless do not (this is first thing in the morning or after no activity for an hour or so) "unless" I first go to the server box, prompt it and then ping something.
Is this a sleeping server box or router issue? The wireless boxes "are" being assigned "IPs" but can not connect. Do servers have a sleep setting or a setting that "wakes on request". Where would I check this? My server is a Edgy-Server, my router is a DI-624 with the latest firmware.
Thanks!

---

### Post by houstonbofh on 2007-02-26
I can not follow this at all...  Is your server doing dhcp?  What router are you using?  What AP?  Can the WiFi clients ping anything?

---

### Post by Uta on 2007-02-26
The router is the dhcp server. but the server box is doing the dns. As I stated in my first post the router is a DI-624, that is made by D-Link. The wireless boxes as I said, do receive an IP but can not ping the server or anything outside our lan. It is confusing.
Thanks.

---

### Post by houstonbofh on 2007-02-26
I think the DHCP lease if stale, and the server may not be responding.  Or the Dlink router could be hanging and not passing DHCP well.  You might try busting out the vents on the Dlink.  They run hot, and it is how I made the one my brother has stable.

Also, while it is broke, do an "ifconfing" and see if it comes back as expected.  You might also try a "sudo dhclient" as well while it is broke.

---

### Post by Uta on 2007-02-26
I still have a DHCP issue? From the wireless box that has lost it's connect, it can ping the router but not the local dns server or the outside world.
If I do ifconfig you can see it does have an assigned IP
-------------------------------------------------------------
wlan0     Link encap:Ethernet  HWaddr 00:80:C8:10:B8:79  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::280:c8ff:fe10:b879/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:745 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:105842 (103.3 KiB)  TX bytes:8443 (8.2 KiB)
          Interrupt:10 Base address:0x1400 
-------------------------------------------------------------
If I :
sudo dhclient wlan0
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:80:c8:10:b8:79
Sending on   LPF/wlan0/00:80:c8:10:b8:79
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.0.1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.0.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.104 -- renewal in 300587 seconds.

----------------------------------------------------------
Should I set the DHCP Lease to a shorter time, currently it's set for a week?
Thanks.

---

### Post by slayerboy on 2007-02-26
Ok stupid oberservation.  If your wired boxes can connect and ping and get to the net just fine while your wireless cannot, then it's not a server issue, IMHO.  It's a wireless router issue.  Not sure if overheating would cause that.  It's not a DHCP issue IMHO either because the wired boxes are connecting fine, or do I have that wrong?

---

### Post by Uta on 2007-02-26
I agree with you that it has been narrowed down to a "wireless router issue" but can I do about this?
Thanks.

---

### Post by slayerboy on 2007-02-26
first you need to look at how many wireless devices you have and how old your wireless router is

then you need to see if maybe updating firmware for the wireless router resolves the issue, or any other "bending the vents" things work like what was mentioned above

next, you might just need to look at getting a new wireless router.  if you go this way, you might just be able to get it so that you can have your server act as a router and you'll just need a wireless accespoint to plug your server into.

But check the firmware, that'd be my first guess.

---

### Post by Uta on 2007-02-27
Thanks for your input. The router is only a year old and the firmware was updated 2 weeks ago. (That's when the issue began). I will check if I can revert to an older version of firmware.
I'm afraid I don't understand "bending the vents" suggestion. The router is only slightly warm to the touch, not hot?
Thanks.

---

### Post by houstonbofh on 2007-02-27
I think it looks more like a DNS issue.  You say your WiFi users "can not get to the net" but did you try by IP address?  Ping 4.2.2.2 and see if it works.  I suspect some arp issues preventing you from finding DNS.  (Which still could be the dlink)

---

### Post by Uta on 2007-02-27
Yes, I have tried pinging by IP from a wireless client when it was in a down state.
As stated it can ping the router, but not the dns server or any other lan clients.
Could elaborate about "arp issues"
Thanks.

---

### Post by houstonbofh on 2007-03-01
Funny thing is I just went through this on a m0n0wall list.  Cut and paste FTW!  Now this guy had a slightly different problem, but how arp reacts still applies.
> This is way beyond the normal scope of this list.  So lets go!  :)

First lets start with the arp table.  Every system on your network has one.  Every computer, switch and AP.  For one interface devices, (desktops) it is a simple table.  Type 'arp -a' from the command line to see it.  (Windows, Mac, Linux or Unix...)  It shows the IP address translated to mac address of everything it has seen.  In a switched network, that will be the router.  It may include printers, servers, and other systems you touch.  At home connected directly to a router with no other items, it will only be the router.

Now a switch has a much more complex routing table.  It has no IP stuff.  It just knows the port each MAC address hangs off.  Now what happens when a MAC address moves?  This depends on how far down a chain it is.

Say you have a switch at the router.  It has several switches off it for each floor.  Each floor has several switches for each region of the floor.  Each region has one (or more) AP.  Now Bob's laptop walks down the hall.  On the way it connects to the floor above.  The AP says "I have bob's MAC."  The regional switch says "I have Bob's MAC."  The floor switch says "I have Bob's MAC." The router switch says "I have Bob's MAC." down the chan to the floor switch on Bob's floor who now says "I have Bob's MAC." but on a different port... And the regional switch says "He has Bob's MAC." and on to the AP.  But by now Bob has gone back to his desk.  So the first AP says, "But I have Bob's MAC..."

If you have someone on a edge between to APs they can flip back and forth, and this goes on.

Solutions...  You can shorten the "lease time" (I know it is not lease time, but the analogy works) on some advanced switches.  You can use different ESSIDs so the client doesn't move as easily.  You can use less switches on the wireless network.

---

### Post by Uta on 2007-03-02
Thank you for your explanation. I appreciate you taking the time to explain.
Unforunately my issue remains.
As stated before the only way I have found to get the wireless clients online is to go to the server box, prompt and then ping something. 

Before going to bed last night I shorten the lease time on the router to it's shortest release (1 hour) but the this morning when I booted my laptop, it got an IP from the router (as usual) but could not reach the outside Internet till I went to the server box and pinged something. Returning to the laptop and reloading the browser, now I could connect.
This is whyI suspect the server (which is the dns server though not the dhcp server (the router is).

Strange.

This all started when I upgraded the firmware of the router. I have contacted D-Link but no one will tell me if it's ok to re-flash the router with an earlier version of firmware.

---

### Post by houstonbofh on 2007-03-02
Not a clean fix, but you could install "The Angle Network Monitor" from [http://www.paganini.net/index.cgi/angel/angel.html](http://www.paganini.net/index.cgi/angel/angel.html)  It will monitor your network, and that means constant connections every 5 (configurable) minutes.

---

### Post by Uta on 2007-03-21
I have been using a "ping loop" to keep my server awake and that works but seems sort of hack-ish.
It was suggested that I probably had a power-saving daemon running and I did find this.

/lib/modules/2.6.17-10-powerpc/kernel/drivers/cpufreq/cpufreq_powersave.ko
/lib/modules/2.6.17-11-powerpc/kernel/drivers/cpufreq/cpufreq_powersave.ko

Would this put my server to sleep?

If this is the issue, should I blacklist it?

Thanks!

---

### Post by houstonbofh on 2007-03-22
Why not look at your power saving options? If you have gnome,  'gnome-power-preferences' is the program to look.

---

### Post by Uta on 2007-03-22
This is a headless server and after doing "lsmod" I see that there is no powersave module loaded.
It was suggested that the issue could be something in the BIOS, but no there was nothing there to do with sleep settings...
Back to my ping loop

---

