---
title: "Wireless No Longer Working?"
date: 2007-01-10
forum: System76 Support
---

### Post by Pobega on 2007-01-10
[http://ubuntuforums.org/showthread.php?t=335113](http://ubuntuforums.org/showthread.php?t=335113)

This is a repost here, but I figured maybe you would be able to help me out more than in the other forum. Until last night my Wireless was working fine, and now it refuses to pick up wireless networks, they don't even show up in nm-applet, all I get is:

[[IMG]http://img80.imageshack.us/img80/5646/ssrs2.th.png[/IMG]](http://img80.imageshack.us/img80/5646/ssrs2.png)
[b]This image shows my "networks" in the top-right

Edit:[/b]
Forgot to mention I'm using Pangolin Value.

---

### Post by Pobega on 2007-01-10
I think this might help identify my problem:

> pobega@ackbar:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID: off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6904   Missed beacon:0

sit0      no wireless extensions.

---

### Post by compwiz18 on 2007-01-10
Remove everything except the lines with "lo" in them from /etc/network/interfaces - be sure to back up the file first though.

---

### Post by Pobega on 2007-01-10
> auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid 1UC68
wireless-key 0FB3D18E79

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth1



auto eth0

I'm not sure which exactly I should get rid of, but I've already backed up so a *teeny* bit more help would be awesome, thanks.

---

### Post by crichell on 2007-01-10
Comment out the network cards lines like so

```

auto lo
iface lo inet loopback


# iface eth0 inet dhcp


#iface eth1 inet dhcp
#wireless-essid 1UC68
#wireless-key 0FB3D18E79

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


#auto eth1



#auto eth0

```

---

### Post by Pobega on 2007-01-10
Wow, thanks, that worked!

I've got to say, System76 support has got to be the best support I've ever gotten from any company. **Ever.**

---

### Post by compwiz18 on 2007-01-10
> **Pobega said:**
> I'm not sure which exactly I should get rid of, but I've already backed up so a *teeny* bit more help would be awesome, thanks.

Sorry - but I'm glad you got it working :D

---

