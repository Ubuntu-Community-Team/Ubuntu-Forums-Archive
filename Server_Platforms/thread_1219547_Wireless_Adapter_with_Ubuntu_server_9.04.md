---
title: "Wireless Adapter with Ubuntu server 9.04"
date: 2009-07-21
forum: Server Platforms
---

### Post by giddensdb on 2009-07-21
I want to setup a home server to store files.  I want to put it in a closet out of the way without having to run cables, so can I use my USB wireless adapter that works under the desktop version??

---

### Post by prshah on 2009-07-21
> **giddensdb said:**
>  can I use my USB wireless adapter that works under the desktop version??

Yes. However, since the server version (by default) lacks a GUI, you will need to use command line tools to access it.

Post back with more details about adapter, wireless network security type (no passwords, please) and LAN config for more specific instructions, if you need them.

---

### Post by giddensdb on 2009-07-22
Belkin N Wireless USB Adapter

LAN is simply a router that I connect to the internet with.  I have a laptop, the old pc I want to use as a file server and a ps3.  I don't have any security setup, but my router does offer mac address filtering so only certian pieces of hardware can connect.  Plus my esid is not broadcast.

---

### Post by prshah on 2009-07-22
> **giddensdb said:**
> Belkin N Wireless USB Adapter

I don't have any security setup

my esid is not broadcast.

I assume that you will be using ndiswrapper to setup the adapter. [Look here]("http://ubuntuforums.org/showpost.php?p=4723545&postcount=1") for a commandline guide to setup ndiswrapper. 

Once your adapter is setup (visible under iwconfig), you can then connect to the wireless router with the command```
sudo iwconfig wlan0 essid youressid && sudo dhclient wlan0
``` (replace wlan0 with the actual name of your network interface, as shown with iwconfig.)

Post back here if you run into any problems.

---

### Post by kerry_s on 2009-07-22
> **giddensdb said:**
> Belkin N Wireless USB Adapter

LAN is simply a router that I connect to the internet with.  I have a laptop, the old pc I want to use as a file server and a ps3.  I don't have any security setup, but my router does offer mac address filtering so only certian pieces of hardware can connect.  Plus my esid is not broadcast.

just put your settings in /etc/network/interfaces and it will auto connect and be ready at every boot, it will also reconnect if lost.

```

allow-hotplug wlan0
iface wlan0 inet dhcp
wireless-essid your-essid

```

---

### Post by wcryer on 2009-07-22
I am trying to do a similar project. old laptop for file/print server. I have ubuntu server 9.04 on there. My wireless is wpa2 and have been unable to connect. It sees my wireless card as eth1 and after trying to jump through a whole bunch of hoops for wpa_supplicant and all that business i tried to find a gui to put on a disc. i could only find gnome that would fit on a dvd (which it doesnt have) so I am currently running linux mint 5 off of a disc. Does this even work for a server edition? 
 
anyways, the network manager does not seem to recognize my broadcasted network. it wont let me type in any of the dialog fields. I'm not sure what else to try. Anyone have any pointers?
 
Thanks in advance

---

### Post by Dirty_habiT on 2009-07-30
My wireless on my toshiba laptop does not work either on ubuntu server 9.04.  It has all the most recent updates.

I've tried almost everything I could find online including the Wireless Security HOWTO (search for it).

The chipset is RTL8187B.  I'm at my wit's end, no dhcp and no static IP works.

---

