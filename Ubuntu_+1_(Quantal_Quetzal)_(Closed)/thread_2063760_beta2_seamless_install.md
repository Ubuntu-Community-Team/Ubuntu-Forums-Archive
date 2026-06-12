---
title: "beta2 seamless install"
date: 2012-09-27
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-09-27
So far, so good.  Installed straightaway on:

```

ventrical@ventrical-P4M266A-8237:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0a.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV350 AQ [Radeon 9600]
01:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV350 AQ [Radeon 9600] (Secondary)
ventrical@ventrical-P4M266A-8237:~$ 

```

---

### Post by jerrylamos on 2012-09-27
Widescreen notebook with external monitor amd64 install, three crashes but survived.  One of the crashes was apport crashing reporting a crash.

Netbook live boot with external TV VGA 1366x768 mouse and keyboard would not work unless monitor disconnected & reboot using only the laptop screen.  

After install a .xprofile with xrandr and an xorg.conf got the TV running.

Hidden wirelss WPA is a @#$% with QQ.  PP runs fine.  Example, select a field to enter network name, wait for a minute before I can even key anything in.  Yes there's a launchpad bug written.  Among other delays the  "authenticate" is not being issued to the kernel.  Once it is, connection comes right up.  Well, I can get by.  Not a showstopper.  An annoyance.

Screen lock did won't wake up, so ctrl-alt-F1 sudo service lightdm restart.  Turned off screen lock.

3rd pc 3.3 gHz tower first live install proceeding went to zebra stripes no response to anything.  ATI radeon Xpress 200.  Tried nomodeset boot proceeding screen went black.  Third try at install ran O.K.

So the easiest install was the one with three crashes.

---

### Post by ventrical on 2012-09-27
Well the install went seamless but there are already bugs - like the new Floppy Disk Icon .. the light will come on and stay on if you try to access data from a 1.2MB floppy and it will not go out until you reboot.

I'll have to check that out in the morning because I remember a bug that effenberg tried to help me with  on a USB floppy that worked fine in Maveric and Lucid but coughed in Oneiric.

---

### Post by cariboo on 2012-09-27
Jailed double post.

---

