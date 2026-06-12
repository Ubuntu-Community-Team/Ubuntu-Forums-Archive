---
title: "My experience installing Gutsy on Toshiba A215-S7416."
date: 2007-12-30
forum: Testimonials &amp; Experiences
---

### Post by hari_home on 2007-12-30
Purpose:
This is a recollection of how I made Gutsy 32-bit work on my Toshiba Laptop. 
It is mainly for my own referece, but it is written so that anyone with moderate 
computer knowledge should be able to read and understand it.

Machine: This laptop is a special build for Wal-Mart. The stats are below. 

Toshiba 15.4" Satellite A215-S7416 from walmart.com for $598 in Dec 07 just
before Christmas.

Operating System   : Genuine Windows Vista® Home Basic (32-bit)
Processor Type     : AMD Athlon™ 64 X2 Dual-Core Processor   
Processor Number   : TK-53   
Processor Speed    : 1.70GHz   
Front Side Bus     : HyperTransport™ Technology @ up to 800MHz  
Memory Size        : 2048MB
Memory Speed       : PC5300 DDR2 667MHz SDRAM
Display Size       : 15.4" widescreen
Display Type       : WXGA with TruBrite® Technology
Display Resolution : 1280x800.
Graphics Engine    : ATI® Mobility Radeon™ X1200
Graphics Memory    : 128MB-319MB dynamically allocated shared graphics memory
Hard Drive Size    : 120GB
Hard Drive Speed   : 5400rpm
Optical Drives     : DVD-SuperMulti drive (+/-R double layer) supporting up to 11 fomats
Wireless LAN       : Realtek 802.11b/g wireless-LAN 	

1. Used Windows Vista Disk Manager to size the volume to half
   (max allowed by Vista).

2. Installed ubuntu gutsy 64bit AMD and Intel.

3. During install, used Guided option to use largest continguous free space. 64-bit Gutsy 
   didn't work as well. Some issues were:
   a. ALSA didn't work. Used OSS drivers for Audio.
   b. Internal wireless did not work. Had to use External USB adapter. 
      (may be fixed with a 64-bit driver under ndiswrapper.)
   c. w64 codecs were a little unpredictable, tried and failed to install w32codecs.
   d. Flash player WOULD NOT work.
   ...
   If someone else can fix these issues, great. I decided to take a different route.

4. Decided to put 32-bit gutsy on the machine instead. Tried installing over the 64-bit OS, 
   but it didn't work. Attempted using SystemRescueCD to run Gparted to erase the partition,
   but X server would not start. I ended up using Gparted on the Ubuntu live CD. 
   a. After the live CD loads, from the desktop, press <Alt>+F2. Type "sudo gparted".
   b. Select the biggest volume from the dropdown menu on the right. 
   c. There should be a NTFS partition and an Ext3 partition. Delete the Ext3 partition. 
     (You should have already backed up anything you cared about.)
   d. Click "Apply" and exit.
   NOTE: Gparted is a weapon of mass destruction. Be careful how you use it. 

5. Before you start any install, it's easiest if you connect an Ethernet cable instead of 
   using wireless. Again, use largest continuous free space when installing. Use the 
   Restricted Driver for the graphics card. 

6. Use Automatix2 to take care of your install issues. Easiest thing is to use the repos 
   to get it. Refer to "Installing Automatix2 with apt" under the "Installation" wiki 
   from [www.getautomatix.com](www.getautomatix.com). While there grab all the audio and video codecs, flash, 
   java, and anything else that looks like you might need it. BE SURE TO GRAB NDISWRAPPER 
   AND ALSA DRIVERS. You will need it for the next steps.

7. Once you have the drivers for ALSA, here is the trick.
   a. In a terminal, type "sudo gedit /etc/modprobe.d/alsa-base" 
      (you can use any other editor, too.)
   b. at the bottom of the file. add the following:
      "options snd-hda-intel model=acer #use acer even though the machine is toshiba"
      (the # is a comment which will remind you what the line is for.)
   c. Save and exit. You will probably have to reboot.
   d. Open up a terminal and type "alsamixer." Make sure none of the channels are muted, 
      and be sure to set the PCM between 70-80 to avoid nasty distortions. 

8. <Install Wireless>
   You can use ndiswrapper or install a modified realtek rtk8187 driver to work with
   realtek rtk8197 is this machine.

   I used the modified realtek 8187 driver. See limitations.
   See [http://www.datanorth.net/~cuervo/blog/linux-on-the-satellite-a215-s7407/](http://www.datanorth.net/~cuervo/blog/linux-on-the-satellite-a215-s7407/)
   I still have difficulty getting the wireless driver to startup automatically.
   I may try ndiswrapper.

   If you want to try ndiswrapper see:
   [http://tiagoboldt.net/blog/toshiba-l40-ndiswrapper-realtek-8187/](http://tiagoboldt.net/blog/toshiba-l40-ndiswrapper-realtek-8187/)

9. When finished, make an image backup of your drive. It's not required, but if you need 
   to redo your computer, it's much easier to restore an image than it is to
   repeat all the above steps. I used Acronis True Image 10.

---

### Post by Feanor3 on 2007-12-31
Hey I got my wireless drivers loaded at startup.

You just need to add the following to your /etc/network/interfaces .
```

pre-up "path to wlan0up"/wlan0up

```

Here's what mine looks like:

```

cmoerman@vm-base:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
pre-up /usr/src/rtl8187b-modified/wlan0up

```

Reboot, take a look at your Network Manager, and any wireless networks should come up.

*EDIT* \
Can you get WPA working with the modified driver? Mine won't, I'm considering trying ndiswrapper for a while, but I like to support native drivers as much as possible
*/EDIT*

I've been having issues getting the sound to work, but I'm about to try your steps.

---

### Post by hari_home on 2007-12-31
Thanks. I too just did the same and then saw your post. Now the Wireless started on reboot.

hari@hari-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

pre-up          /root/rtl8187b-modified/wlan0up

---

### Post by DishBreak on 2007-12-31
Proud Co-author =). 

Oh, for the alsa-base, comments can't be in-line....put the comment on the line above or below. my mistake.

---

### Post by hari_home on 2007-12-31
DishBreak and hari_home wrote co-authored the original post.
The comments above is a warning that inline comments are not OK.

In file /etc/modprobe.d/alsa-base

Correct:
options snd-hda-intel model=acer
# use acer to get correct support

Wrong:
options snd-hda-intel model=acer # use acer to get correct support

For Alsa I used:

alsa-driver-1.0.15rc3.tar.bz2
alsa-firmware-1.0.15rc1.tar.bz2
alsa-lib-1.0.15rc3.tar.bz2
alsa-utils-1.0.15rc1.tar.bz2 

Good luck.

---

### Post by DishBreak on 2008-01-05
Quick update. We are again having problems with internal wireless, can't get it to work with ndiswrapper. I'm going to try the madwifi drivers first, then ndiswrapper.

---

### Post by hari_home on 2008-01-06
Here is an update on network access:

The internal wireless card with the modified driver rtl8187b-modified
absolutely refused to connect to netgear 802.11g turbo MIMO router although it
connected to Microsoft 802.11b router.

I recalled that Airlink 101 802.11g USB adapter worked with this machine with ubuntu gutsy i86_64 with ndiswrapper. From airlink website I got a driver and it worked with ndiswrapper
but stopped working.

I did lsusb and found that it uses ralink chip.

 lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 003 Device 002: ID 148f:2573 Ralink Technology, Corp. 
Bus 003 Device 001: ID 0000:0000  

I was pleasantly surprised to see
[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

Then I did the following:

Downloaded [http://www.ralinktech.com.tw/data/RT73_Linux_STA_Drv1.0.4.0.tar.gz](http://www.ralinktech.com.tw/data/RT73_Linux_STA_Drv1.0.4.0.tar.gz)
su root

gunzip RT73_Linux_STA_Drv1.0.4.0.tar.gz
tar xvf RT73_Linux_STA_Drv1.0.4.0.tar

cd /home/hari/Desktop/
cd RT73_Linux_STA_Drv1.0.4.0/Module/
See file README

Edited fille ifcfg-rausb0
DEVICE=wlan1
ONBOOT=yes

## Confirm your AP supports dhcp or connects up the ethernet 
## before set-up as a dynamic IP
BOOTPROTO=dhcp

cp Makefile.6  ./Makefile
# The above is because my kernel is  2.6.22-14-generic
make all
make install

After some trial and error the following are my startup files:

/etc/network/interfaces

auto lo
iface lo inet loopback

/etc/modprobe.conf
alias rausb0 rt73

#   rausb0 for Airlink
/etc/modprobe.d/blacklist

# Broadcom Wireless Driver. Pain in neck.
blacklist bcm43xx

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187
blacklist ath_pci

blacklist islsm
blacklist prism54usb
blacklist rt2500usb

I had to restart network a few times to get this right.

/etc/init.d/networking restart

Finally I am able to report that I did a complete cold start and got it to connect with 84%
signal strength.

Now I wonder what happens if I go to another wireless access point point or router.

Hope the next release of Ubuntu does a better job of supporting wireless so that the
internal USB2 Realtek RT8197 would work.

Hope this helps some one else.

---

### Post by Sef on 2008-01-06
Moved to Testimonials and Experiences.

Note:  Automatix is not recommended because it has been known to break systems.  Almost everything can be installed through Add/Remove, if not, then Synaptic will do the trick.

---

### Post by blackstripes on 2008-01-14
> **Feanor3 said:**
> Hey I got my wireless drivers loaded at startup.

You just need to add the following to your /etc/network/interfaces .
```

pre-up "path to wlan0up"/wlan0up

```

Here's what mine looks like:

```

cmoerman@vm-base:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
pre-up /usr/src/rtl8187b-modified/wlan0up

```

Reboot, take a look at your Network Manager, and any wireless networks should come up.

*EDIT* \
Can you get WPA working with the modified driver? Mine won't, I'm considering trying ndiswrapper for a while, but I like to support native drivers as much as possible
*/EDIT*

I've been having issues getting the sound to work, but I'm about to try your steps.

Can anyone tell me what I need to do in order to gain permission to modify my filesystem?  Right now my laptop will not let me modify this file, or move anything to /usr/src...

P.S.  I have been using Ubuntu for all of 2 days and am extremely overwhelmed to say the least. :)

---

### Post by hari_home on 2008-01-20
I do any driver installation as root. If required I make some specific files executable by all users. In general this is good practice.

---

### Post by Monicab on 2008-09-01
Hello. I have this exact same laptop model and i am able to run everything but the wireless card. Im desperate now. I cannot connect to the internet through the wireless card which is TERRIBLE and the reason I dont use Ubuntu since i need it most of the time :(.

Has anyone found a definite solution to this problem? My system DOES detect the wireless card which is described in lspci -v output:

```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
	Subsystem: Toshiba America Info Systems Unknown device ff10
	Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: f8000000-f81fffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f7ffffff
	Capabilities: <access denied>

00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914 (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
	Capabilities: <access denied>

00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=0d, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f8200000-f82fffff
	Prefetchable memory behind bridge: 0000000088000000-00000000880fffff
	Capabilities: <access denied>

00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0e, subordinate=13, sec-latency=0
	Capabilities: <access denied>

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01 [AHCI 1.0])
	Subsystem: Toshiba America Info Systems Unknown device ff10
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 8440 [size=8]
	I/O ports at 8434 [size=4]
	I/O ports at 8438 [size=8]
	I/O ports at 8430 [size=4]
	I/O ports at 8400 [size=16]
	Memory at f8609000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff10
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at f8604000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff10
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f8605000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff10
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at f8606000 (32-bit, non-prefetchable) [size=4K]

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff10
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f8607000 (32-bit, non-prefetchable) [size=4K]

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff10
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at f8608000 (32-bit, non-prefetchable) [size=4K]

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff10
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 21
	Memory at f8609400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
	Subsystem: Toshiba America Info Systems Unknown device ff10
	Flags: 66MHz, medium devsel
	I/O ports at 8410 [size=16]
	Capabilities: <access denied>

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
	Subsystem: Toshiba America Info Systems Unknown device ff10
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8420 [size=16]

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
	Subsystem: Toshiba America Info Systems Unknown device ff0a
	Flags: bus master, slow devsel, latency 64, IRQ 17
	Memory at f8600000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
	Subsystem: Toshiba America Info Systems Unknown device ff10
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=14, subordinate=19, sec-latency=64
	Memory behind bridge: f8300000-f83fffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series] (prog-if 00 [VGA controller])
	Subsystem: Toshiba America Info Systems Unknown device ff1a
	Flags: bus master, fast devsel, latency 64, IRQ 19
	Memory at f0000000 (64-bit, prefetchable) [size=128M]
	Memory at f8100000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at 9000 [size=256]
	Memory at f8000000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

[B]08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
	Subsystem: Toshiba America Info Systems Unknown device ff10
	Flags: bus master, fast devsel, latency 0, IRQ 220
	I/O ports at a000 [size=256]
	Memory at f8200000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at 88000000 [disabled] [size=128K]
	Capabilities: <access denied>[/B]

14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff10
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at f8300000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

14:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Subsystem: Toshiba America Info Systems Unknown device ff10
	Flags: bus master, medium devsel, latency 32, IRQ 22
	Memory at f8300800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

14:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Toshiba America Info Systems Unknown device ff10
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at f8300c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

14:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
	Subsystem: Toshiba America Info Systems Unknown device ff10
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at f8301000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

```

and when i go to System-->Administration-->Network i DO can see the three connection options including Wireless conection. Even more, my Gnome Network Manager has the "activate wireless" option enabled but the wireless connections list is empty even when there ARE wireless connections available. This same laptop's wireless works well in Windoze.

Please help!! I have been with this problem for months and if i dont get a solution to this ill simply have to remove Ubuntu since i cant use it :(

If it is of any help the output of ifconfig is
```
casiopea@casiopea-laptop:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:a0:d1:8b:5b:da  
          inet dirección:192.168.0.100  Difusión:192.168.0.255  Máscara:255.255.255.0
          dirección inet6: fe80::2a0:d1ff:fe8b:5bda/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:1582 errors:0 dropped:0 overruns:0 frame:0
          TX packets:590 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:1091096 (1.0 MB)  TX bytes:94580 (92.3 KB)
          Interrupción:220 Dirección base: 0x8000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:304 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:15200 (14.8 KB)  TX bytes:15200 (14.8 KB)

wlan0     Link encap:Ethernet  direcciónHW 00:16:44:79:db:7c  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

and iwconfig returns:

```
casiopea@casiopea-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Channel=47  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   Fragment thr:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

and lsusb returns:
```
Bus 006 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

Thanks in advance for your help!! :)

---

### Post by Monicab on 2008-09-01
I left clicked the Gnome Network Manager's icon and entered in the "connect to another wireless networks" dialog box, typed in the name, security type, password and authentication of a well known home network (in my house) within the dialog box's options AND it seemed to connect (the bars icon appeared instead of the two monitors at the Network Manager), the signal strenght appeared at 30% but STILL i couldnt connect to the internet. When i viewed the connection properties, no IP or route to host were set. Weird... WHAT THE HELL IS WRONG? :confused:

I still can connect through ethernet from the same connection though... at least... but not enough for everywhere else... :(

---

### Post by fermin on 2008-09-06
Hey i have this same issue for some time now. I got to think this could never be solved. Ubuntu is useless in this laptop without wireless support nowadays. I would also appreciate the help infinitely. :)

---

### Post by hari_home on 2008-10-15
Folks,

Please search for Toshiba A215-S7416 to see my new posting. I am not very active on the forums as I can be. The kernel in 8.04 does not have driver for the internal USB2 wireless card with rtl8187 chip. There are some workarounds with which I had limited success. Finally, I bought a cheap $20
"My Essentials" external USB2 wireless card and it worked out of the box.

I now upgraded this machine to 8.1 Beta as root update-manager --devel
and the new kernel has the driver for rtl8187. I am a happier camper:)

However, if you plan to do this, better back up your data. I "backup" on gmail or a memory stick.

Good luck!

---

### Post by detroit/zero on 2008-10-15
> **hari_home said:**
> 
7. Once you have the drivers for ALSA, here is the trick.
   a. In a terminal, type "sudo gedit /etc/modprobe.d/alsa-base" 
      (you can use any other editor, too.)
   b. at the bottom of the file. add the following:
      "options snd-hda-intel model=acer #use acer even though the machine is toshiba"
      (the # is a comment which will remind you what the line is for.)
   c. Save and exit. You will probably have to reboot.
   d. Open up a terminal and type "alsamixer." Make sure none of the channels are muted, 
      and be sure to set the PCM between 70-80 to avoid nasty distortions. 

On my Toshiba Satellite a135, which has all the same specs as your machine with the exceptions of an Intel 2-Core processor and less RAM, I've found that changend the model to "lenovo" instead of "acer" enables the detection that automagically switches off the laptop speakers when you plug headphones in.

It would look like```
 options snd-hda-intel model=lenovo
```Just thought I'd throw that in there. I can't say I ever had any of the other problems that you've had, though.

lspci -v:```
zero@zero-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
    Subsystem: Toshiba America Info Systems Unknown device ff00
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Unknown device ff02
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at dc100000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 1800 [size=8]
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Memory at dc200000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Toshiba America Info Systems Unknown device ff02
    Flags: bus master, fast devsel, latency 0
    Memory at dc180000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
    Subsystem: Toshiba America Info Systems Unknown device ff01
    Flags: bus master, fast devsel, latency 0, IRQ 21
    Memory at dc440000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d6000000-d7ffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
    Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d8000000-d9ffffff
    Prefetchable memory behind bridge: 00000000d2000000-00000000d3ffffff
    Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: da000000-dbffffff
    Prefetchable memory behind bridge: 00000000d4000000-00000000d5ffffff
    Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Toshiba America Info Systems Unknown device ff00
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Toshiba America Info Systems Unknown device ff00
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Toshiba America Info Systems Unknown device ff00
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Toshiba America Info Systems Unknown device ff00
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
    Subsystem: Toshiba America Info Systems Unknown device ff00
    Flags: bus master, medium devsel, latency 0, IRQ 19
    Memory at dc444000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=0a, sec-latency=56
    Memory behind bridge: dc000000-dc0fffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Toshiba America Info Systems Unknown device ff00
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
    Subsystem: Toshiba America Info Systems Unknown device ff00
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 18b0 [size=16]
    Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
    Subsystem: Toshiba America Info Systems Unknown device ff00
    Flags: medium devsel, IRQ 11
    I/O ports at 18c0 [size=32]

04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
    Subsystem: Askey Computer Corp. Unknown device 7106
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d8000000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
    Subsystem: Toshiba America Info Systems Unknown device ff00
    Flags: bus master, fast devsel, latency 0, IRQ 220
    I/O ports at 4000 [size=256]
    Memory at da000000 (64-bit, non-prefetchable) [size=4K]
    [virtual] Expansion ROM at d4000000 [disabled] [size=64K]
    Capabilities: <access denied>

06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
    Subsystem: Toshiba America Info Systems Unknown device ff00
    Flags: bus master, medium devsel, latency 168, IRQ 17
    Memory at dc006000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
    Memory window 0: 50000000-53fff000 (prefetchable)
    Memory window 1: 54000000-57fff000
    I/O window 0: 00001400-000014ff
    I/O window 1: 00001c00-00001cff
    16-bit legacy interface ports at 0001

06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
    Subsystem: Toshiba America Info Systems Unknown device ff00
    Flags: bus master, medium devsel, latency 32, IRQ 16
    Memory at dc005000 (32-bit, non-prefetchable) [size=2K]
    Memory at dc000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
    Subsystem: Toshiba America Info Systems Unknown device ff00
    Flags: bus master, medium devsel, latency 57, IRQ 18
    Memory at dc004000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

06:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
    Subsystem: Toshiba America Info Systems Unknown device ff00
    Flags: bus master, medium devsel, latency 57, IRQ 20
    Memory at dc005800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
```

---

