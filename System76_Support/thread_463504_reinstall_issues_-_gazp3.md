---
title: "reinstall issues - gazp3"
date: 2007-06-03
forum: System76 Support
---

### Post by tedrampart on 2007-06-03
Okay, 

so I decided I would reinstall so I could set up a dual boot with windows (haven't installed windows yet) and try to fix issues like the swap and cpu scaling, also to setup a seperate /home partition.

when I reinstalled, everything seemed fine, though I did have to use apt-get to install the nvidia drivers and setup the xconfig.

a few things came up when I booted up post-install:
1) the boot hung part way through the bootup, when I ran the boot without the splash, it hung at "configuring network devices" .. though both the wireless and wired networks work.

2) sound doesn't come through the speakers, but no errors come up when I try to play some of the media files that came with the install.  also the bootup sounds don't play.

I've ran the System76 driver install, as well as the restore, but these problems still occur.

anyone have any thoughts or experiences with this?

thanks

---

### Post by unique on 2007-06-03
Well for your first problem you will want to comment out your network/interfaces file like follows.
```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

```
You only want to leave the loop back interface. Comment out everything else.
Network manager takes care of everything so you don't need it to load during boot. 

For your second problem make sure you have the package build-essential installed. i would also recommend running the system76-driver from a terminal so you can see if you get any errors.

---

### Post by tedrampart on 2007-06-03
okay, so I got the network fixed from the above suggestion...

and also tried re-running the system76 driver from the console, and didn't see any error messages..

and still the sound isn't working.  alsa isn't reporting any issues, it just seems as though the speakers aren't working.

also, it seems that acpi frequency scaling isn't supported.

edit - okay seems all I needed to do was turn off the external amplifier in alsa mixer..

---

