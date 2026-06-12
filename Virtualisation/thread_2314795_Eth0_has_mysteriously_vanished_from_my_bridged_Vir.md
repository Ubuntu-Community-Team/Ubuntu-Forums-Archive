---
title: "Eth0 has mysteriously vanished from my bridged VirtualBox VM"
date: 2016-02-23
forum: Virtualisation
---

### Post by spacer.x-infinity on 2016-02-23
Ultra-newbie question here:

I am trying to set up a bridged Kubuntu 14.04 VirtualBox VM that connects to the same WIFI network that my Win 7 host uses. The "Bridged Adapter" network setting has been enabled, Promiscuous Mode is in effect, the "Cable Connected" box has been checked, and my */etc/network/interfaces* file has been modified to read thusly:

```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

iface eth0 inet static
       address 192.xxx.x.xxx
       netmask 255.255.255.0
       network 192.xxx.x.x
       broadcast 192.xxx.x.xxx
       gateway 192.xxx.x.x

```

I've successfully managed to do this in the past but configuration difficulties have led me to uninstall and reinstall my VM several times and I haven't managed get bridged networking up and running again since then. Prior to editing my *interfaces* file, I noticed that VirtualBox defaulted to its own wired connection. However, after making those modifications and rebooting the system, it, along with any other available connection has simply vanished. When I run *ifconfig,* the only network displayed is my loopback device. After editing *interfaces* but before the reboot, both *lo* and *eth0* were still visible when I ran *ifconfig.* What am I overlooking here? This has worked for me in the past but I can't remember what I did then that I'm neglecting to do this time around. Any help would be appreciated.

---

