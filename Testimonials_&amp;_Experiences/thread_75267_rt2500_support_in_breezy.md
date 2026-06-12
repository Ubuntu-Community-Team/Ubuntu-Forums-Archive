---
title: "rt2500 support in breezy"
date: 2005-10-13
forum: Testimonials &amp; Experiences
---

### Post by g-joey on 2005-10-13
Hi folks,

a big, big "thanks!" for putting the rt2500 wifi chipset support into breezy badger! It worked out of the box on a machine where I had never made it work before!

Thanks, Joe

---

### Post by BinaryDigit on 2005-10-18
Ya me too!! I was so ever grateful :D I let the whole world know :P :)

---

### Post by coldsalmon on 2005-10-18
It doesn't work for me!  Am I the only one?  I got it to work in Hoary using ndiswrapper, but no such luck in Breezy.  It says that the file is not a valid driver, even though the same file worked with the same hardware in Hoary.  I installed the package rt2500, but when I run RaConfig2500 it says "Device driver not found."  Here's my iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      RT2500 Wireless  ESSID:""
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

It used to list the card as ra0 before I installed the rt2500 package, and in Hoary it was listed as wlan0.  Any help would be greatly appreciated!  I'm on an Averatec 3700 laptop.

Thanks,

--C

---

### Post by coldsalmon on 2005-10-19
Found it:

[https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/)

---

### Post by macoute on 2005-10-19
Hi,

I followed the instructions from rt2500-HOWTO, but my card doesnt show up in System | Networking. Compiling is OK, but it just doesn't show up. Im using breezy.

I also noticed that "apt-cache search rt2500" shows up some rt2500-related packages, am i possible to install it that way? 

Actually, I am not even sure if my card is a rt2500-card, but it is a card by A-Link, and according to their website it should be. The card is completely plain, there is only mac-address, serial number and some sticker about standards and so on.

---

### Post by queenorych on 2005-10-21
The newer cards comming out seem to prefer the cheaper (i think ti) chipset.  Even the same model number will swtich chipsets.  You can see this on the rt2500 website, or even the tivo website(I just bought a netgear usb nic that only certain serial numbers work on the tivo(runs linux))

As I remeber your best bet is to go with gigabyte, Asus, MSI, etc.  See newegg.com

---

