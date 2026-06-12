---
title: "HOWTO:  Using D-link AirplusG+ DWL g650+ with ndiswrapper"
date: 2005-10-12
forum: Tutorials
---

### Post by darius_underhill on 2005-10-12
Hi! I just want to share to our fellow Ubuntu Users.  I was finding a lot of threads regarding this issue so I'd like to share how I got my D-Link DWL G650+ Wireless Card.  Moderators: if this thread is already redundant, kindly move it or delete altogether.

First, I'd like to thank the author of the following website:

[http://www.ndeepak.info/tech/wlansarge.php]("http://www.ndeepak.info/tech/wlansarge.php")

For his nearly complete guide.  This is actually a guide for Debian Sarge, but I'm going to describe here the exact steps in my ubuntu hoary laptop (although I will also share some experiences on how to install it in Breezy Preview Release).

1.  First, install the ndiswrapper package.

```
sudo apt-get install ndiswrapper-source ndiswrapper-utils
```

Note for Breezy Users:  There is GUI ndiswrapper in one of the reposotories.  Im not sure where but you may want to try that out.  

Then you will need the drivers from D-Link's website.  (note: I tried using the drivers that came with wireless card but it failed to work)

You can download it from here:

[Windows driver for DWL-G650+]("http://www.dlink.co.uk/?go=gNTyP9Cip9RLIC4AStFCF834mptYKu5YTtvhLPG3yV3oV412l70rOJkmMq5t5jQ=")

Now, extract the file and look for the Windows XP driver INF.  so in this file its GPLUS.inf.  Install it by using the following command:

```
sudo ndiswrapper -i GPLUS.inf
```

Now you will need to install your system's kernel headers.  In my case its "linux-headers-2.6.10-386":

```
sudo apt-get install linux-headers-2.6.10-5-386
```

Next, you will need to install the kernel module for ndiswrapper.

```
cd /usr/src/
tar -jxvf ndiswrapper-source.tar.bz2
```

It will extract a modules directory which holds the ndiswrapper kernel module.  You will need to compile this.

```
cd ./modules/ndiswrapper
make
make install
```

Afterwards, you will now load the modules.

```
depmod -a
modprobe ndiswrapper
```

Currently it will be loaded but to make Ubuntu load it everytime you will need to add the entry "ndiswrapper" in your /etc/modules.

```
sudo cp /etc/modules /etc/modules_backup
sudo echo "ndiswrapper" >> /etc/modules
```

Now I will deviate a bit from the original source of this guide.  For some reason, I hope its only on my system.  If continue following the guide at this point, my system will be able to detect the Wireless card.  So what I did was I restarted my system (restarting the system after hardware driver installation is one of my old Windoze habits).

Try to check your boot messages if your system was able to succesfully load the ndis driver.

Now plug in your wireless card and try running the following command:

```
sudo iwlist wlan0 scan
```

If this causes a "command not found" error, you will need to install the wireless-tools package:

```
sudo apt-get install wireless-tools
```

The output will contain an ESSID for the network. Take note off the ESSID and run the following

```
sudo iwconfig wlan0 essid <ESSID>
```

where <ESSID> is the essid found in the iwlist command earlier.  If you use an encryption key, set it. Security mode can be open or restricted. The default is 'restricted', but for me, it works only if I set the mode to be 'open'.

```
iwconfig wlan0 key open <wepkey>
```

where <wepkey> is your network's wepkey.

Now run iwconfig, and the interface should be all set:

```
sudo iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"BarFoo"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:19:8C:57:C0   
          Bit Rate:54 Mb/s   Tx-Power:10 dBm   Sensitivity=0/3  
          RTS thr:4096 B   Fragment thr:4096 B   
          Encryption key:DEADBEEF00   Security mode:open
          Power Management:off
          Link Quality:100/100  Signal level:-45 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Check the output and make sure that the essid, the wepkey (encryption key), security mode(open) is correct.  Check the value of the access point.  It should contain the MAC address of your Wireless Accesspoint.

To continue, you will need to setup the system for DHCP.  So you will need to add a couple lines to /etc/network/interfaces

```
sudo cp /etc/network/interfaces /etc/network/interfaces_backup
sudo gedit /etc/network/interfaces
```

Add these lines:

```
iface wlan0 inet dhcp
pre-up  iwconfig wlan0 essid "BarFoo" && iwconfig wlan0 key open DEADBEEF00

auto wlan0
```

That's it. To start using the wireless LAN card, issue:

```
sudo ifdown eth0
sodu ifup wlan0
```

To switch back to wired lan.  Just do the opposite of the two lines above.

Extra NOTE:  You can make connecting to a wireless network by install Wifi Radar.

Please see this link for further instructions:

[HOWTO: Wifi Radar on Hoary]("http://www.ubuntuforums.org/showthread.php?t=55745&highlight=radar")

or if you're using breezy you can install it using apt-get.

```
sudo apt-get install wifi-radar
```

Hope this helps.  Feedback will be greatly appreciated.

---

### Post by mlomker on 2005-10-12
Moved to the tips folder.  Thanks for the contribution!

---

### Post by lreyes6 on 2006-07-26
hello i have a doubt... what happend if i change my kernell version?

---

### Post by Feppa on 2006-09-24
Thanx for the great how to! I got it working with WEP but also want WPA. Anyone know how to do this?

---

### Post by jack frost on 2006-09-25
Will this work with the DWL - G650M?

---

### Post by wpault on 2008-12-29
This works very well, although I had to get the D-Link driver off the International (Singapore) D-Link web site

Thank you

---

### Post by moodle on 2009-10-01
I also want to get this card working with WPA.  Any help much appreciated.

---

### Post by goodbye-windows(tm) on 2011-08-28
Is there any hope of making this card run in ubuntu 11.04?? The windows driver appears to be unavailable, and I'm not sure whether I should try to make the card work, or just look for another card.

Would appreciate any guidance.

TY

Art

---

### Post by cariboo on 2011-08-28
The instruction in this thread are no longer valid. I would suggest you start a new thread, as this one is closed.

---

