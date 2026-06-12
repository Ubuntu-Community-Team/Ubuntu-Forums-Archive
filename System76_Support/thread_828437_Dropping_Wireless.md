---
title: "Dropping Wireless"
date: 2008-06-13
forum: System76 Support
---

### Post by einnar on 2008-06-13
I have not been able to maintain a wireless connection for more than 10 minutes on my Serval Performance.

It shows a connection on the taskbar, but I have no connectivity. i have searched the threads, and the network config only has the 2 lines shown. I'd put them up, but I have less than 10 mins...

---

### Post by pytheas22 on 2008-06-13
Please post the output of:
```

iwconfig
lshw -C Network
lspci
lsusb
```

so that we can help you better.

---

### Post by einnar on 2008-06-14
IWCONFIG :
> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"ccc@bldg422"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:15:6D:51:0B:D7   
          Bit Rate=36 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=51/100  Signal level=-62 dBm  Noise level=-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lshw -C Network :
> WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:d6:9c:cf
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.77 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1d:e0:9b:69:99
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 ip=10.119.137.123 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g

lspci :
> 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
0e:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0e:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0e:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
0e:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev ff)


lsusb :
> 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 04f2:b018 Chicony Electronics Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 1532:000d  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 147e:2016  
Bus 002 Device 002: ID 0a5c:2101 Broadcom Corp. 
Bus 002 Device 001: ID 0000:0000  


Thanks!

---

### Post by pytheas22 on 2008-06-14
Thanks for the information.  I found several bug reports ([here]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/144621"), [here]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/148227") and [here]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/137565")) that look like they cover your problem.  It seems that your wireless card has issues when connecting to 802.11n networks--is this what you're using?  There's a simple fix [here]("http://benlynn.blogspot.com/2008/03/thinkpad-x61-wireless-and-ubuntu.html") that you can try.

If that doesn't work, please run the command:
```

dmesg | grep wlan0
```

right after your card loses connectivity next time, and post the output here.

---

### Post by Brandel Valico on 2008-06-14
Just as an aside question. Are you using a wireless telephone near your wireless computer. I have noticed that since gutsy at times being near a wireless phone will cause the connection to drop. This happens almost around 95% of the time I answer my wireless phone at my house if the phone is within a foot or two of my laptop. The percentage goes upto a 100% if I do so within a foot of my laptop. This also happens on my wifes laptop as well. I have a hp compaq nc6000 she has a sony viao. 

I realize that this probably isn't the issue for you. But thought I would mention it just in case. Sometimes it's something just as simple as this happening and not so much a hardware issue.

---

### Post by einnar on 2008-06-17
I'll try to get the output of ```
dmesg | grep wlan0
``` soon. Unfortunately, wireless isn't working at all right now, so I can't post it.

---

### Post by pytheas22 on 2008-06-17
Alright, get the output when you can.  Is there a reason wireless isn't working now at all (i.e. did you do something that you know broke it or did it just break without apparent cause)?

---

### Post by thomasaaron on 2008-06-18
einnar,

1. Make sure your wireless toggle switch is on (slide it to the right).
2. Follow these instructions to ensure your interfaces file isn't hosed...

To fix your /etc/network/interfaces file, go to a terminal
(Application > Accessories > Terminal) and enter the following command:

sudo gedit /etc/network/interfaces

This will launch a text editor with the interfaces file opened in it.

In this file, put a comment (#) in front of EVERY line of the file
EXCEPT for these two lines:

auto lo
iface lo inet loopback

Click SAVE on the text editor and reboot your computer.
It should now boot faster and connect to networks more easily.

NOTE:
Unless you are dealing with static IP addresses (which is pretty rare for the
general end-user) you should NOT establish a network connection by going to
System > Administration > Network.

Instead, you should connect to the Internet using the Network Manager icon
in the upper right corner of your screen (the one that looks like a little
computer monitor).

---

### Post by einnar on 2008-06-20
Thomas,

My interfaces file only has those 2 lines in it.
The switch is also on.
It can see wireless networks, but won't stay connected to them properly. At times it shows connection, but won't browse. Other times, it will repeatedly try to connect, but never manages to. I am trying to connect via DHCP to a password protected service. I manage occasionally to connect, and then I will have anywhere from 5 to 45 minutes of connectivity, then nothing. Using that icon to try to reestablish won't work. Rebooting works about 50% of the time.

Thanks.

---

### Post by pytheas22 on 2008-06-20
Did you try looking at the dmesg output when the connection drops?  There's a good chance that it will mention what's going wrong and make tracking down a solution easier.

---

### Post by einnar on 2008-07-14
I finally got on the network again. Here's the output. Different provider from the first time. Still dropping signal.

Thanks!


```
not in authenticate state - ignored
[ 5395.257082] wlan0: authentication frame received from 00:20:a6:5b:9a:d0, but not in authenticate state - ignored
[ 5399.168654] wlan0: Initial auth_alg=0
[ 5399.168664] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5399.168736] wlan0: Initial auth_alg=0
[ 5399.168742] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5399.170399] wlan0: RX authentication from 00:20:a6:5b:9a:d0 (alg=0 transaction=2 status=0)
[ 5399.170408] wlan0: authenticated
[ 5399.170413] wlan0: associate with AP 00:20:a6:5b:9a:d0
[ 5399.172263] wlan0: authentication frame received from 00:20:a6:5b:9a:d0, but not in authenticate state - ignored
[ 5399.174508] wlan0: RX ReassocResp from 00:20:a6:5b:9a:d0 (capab=0x421 status=0 aid=5)
[ 5399.174517] wlan0: associated
[ 5682.994544] wlan0: RX disassociation from 00:20:a6:5b:9a:d0 (reason=8)
[ 5682.994552] wlan0: disassociated
[ 5682.995075] wlan0: RX deauthentication from 00:20:a6:5b:9a:d0 (reason=3)
[ 5682.995081] wlan0: deauthenticated
[ 5683.026545] wlan0: RX disassociation from 00:20:a6:5b:9a:d0 (reason=8)
[ 5683.027004] wlan0: RX deauthentication from 00:20:a6:5b:9a:d0 (reason=3)
[ 5688.097485] wlan0: Initial auth_alg=0
[ 5688.097497] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5688.098722] wlan0: Initial auth_alg=0
[ 5688.098729] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5688.296757] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5688.496446] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5688.696214] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 5693.100848] wlan0: Initial auth_alg=0
[ 5693.100859] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5693.101114] wlan0: Initial auth_alg=0
[ 5693.101120] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5693.297155] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5693.496891] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5693.696604] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 5698.105116] wlan0: Initial auth_alg=0
[ 5698.105128] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5698.105209] wlan0: Initial auth_alg=0
[ 5698.105215] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5698.301541] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5698.501212] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5698.700911] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 5723.084323] wlan0: Initial auth_alg=0
[ 5723.084334] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5723.084632] wlan0: Initial auth_alg=0
[ 5723.084638] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5723.283507] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5723.483203] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5723.682905] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 5728.087515] wlan0: Initial auth_alg=0
[ 5728.087527] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5728.087611] wlan0: Initial auth_alg=0
[ 5728.087617] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5728.283912] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5728.483581] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5728.683301] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 5733.092033] wlan0: Initial auth_alg=0
[ 5733.092046] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5733.092092] wlan0: Initial auth_alg=0
[ 5733.092097] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5733.288285] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5733.487957] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5733.687656] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 5738.092486] wlan0: Initial auth_alg=0
[ 5738.092497] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5738.092549] wlan0: Initial auth_alg=0
[ 5738.092554] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5738.288664] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5738.488342] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5738.688059] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 5743.092916] wlan0: Initial auth_alg=0
[ 5743.092927] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5743.092978] wlan0: Initial auth_alg=0
[ 5743.092983] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5743.289046] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5743.488739] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5743.688415] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 5748.093004] wlan0: Initial auth_alg=0
[ 5748.093015] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5748.093058] wlan0: Initial auth_alg=0
[ 5748.093062] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5748.289432] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5748.489106] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5748.688805] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 5753.093332] wlan0: Initial auth_alg=0
[ 5753.093345] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5753.093430] wlan0: Initial auth_alg=0
[ 5753.093435] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5753.289754] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5753.489475] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5753.689210] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 5758.097767] wlan0: Initial auth_alg=0
[ 5758.097777] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5758.097866] wlan0: Initial auth_alg=0
[ 5758.097872] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5758.294168] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5758.493889] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5758.693529] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 5763.098288] wlan0: Initial auth_alg=0
[ 5763.098300] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5763.098387] wlan0: Initial auth_alg=0
[ 5763.098392] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 5763.100723] wlan0: RX authentication from 00:20:a6:5b:9a:d0 (alg=0 transaction=2 status=0)
[ 5763.100732] wlan0: authenticated
[ 5763.100737] wlan0: associate with AP 00:20:a6:5b:9a:d0
[ 5763.102463] wlan0: authentication frame received from 00:20:a6:5b:9a:d0, but not in authenticate state - ignored
[ 5763.104757] wlan0: RX ReassocResp from 00:20:a6:5b:9a:d0 (capab=0x421 status=0 aid=5)
[ 5763.104764] wlan0: associated
[ 6131.848397] wlan0: RX disassociation from 00:20:a6:5b:9a:d0 (reason=8)
[ 6131.848407] wlan0: disassociated
[ 6131.852144] wlan0: RX deauthentication from 00:20:a6:5b:9a:d0 (reason=3)
[ 6131.852151] wlan0: deauthenticated
[ 6131.882008] wlan0: RX disassociation from 00:20:a6:5b:9a:d0 (reason=8)
[ 6131.882494] wlan0: RX deauthentication from 00:20:a6:5b:9a:d0 (reason=3)
[ 6131.956712] wlan0: Initial auth_alg=0
[ 6131.956722] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6131.958211] wlan0: Initial auth_alg=0
[ 6131.958219] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6132.156606] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6132.356309] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6132.556021] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 6136.956710] wlan0: Initial auth_alg=0
[ 6136.956722] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6136.956805] wlan0: Initial auth_alg=0
[ 6136.956811] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6137.153003] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6137.352716] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6137.552387] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 6141.957100] wlan0: Initial auth_alg=0
[ 6141.957111] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6141.957393] wlan0: Initial auth_alg=0
[ 6141.957400] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6142.153401] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6142.353075] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6142.552794] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 6146.957652] wlan0: Initial auth_alg=0
[ 6146.957664] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6146.957745] wlan0: Initial auth_alg=0
[ 6146.957751] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6147.153737] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6147.353455] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6147.553159] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 6151.957701] wlan0: Initial auth_alg=0
[ 6151.957711] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6151.957752] wlan0: Initial auth_alg=0
[ 6151.957757] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6152.154145] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6152.353838] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6152.553558] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 6156.958247] wlan0: Initial auth_alg=0
[ 6156.958258] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6156.958544] wlan0: Initial auth_alg=0
[ 6156.958551] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6157.154715] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6157.354247] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6157.553941] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 6161.958785] wlan0: Initial auth_alg=0
[ 6161.958796] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6161.959098] wlan0: Initial auth_alg=0
[ 6161.959104] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6162.154857] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6162.354601] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6162.554298] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 6166.959147] wlan0: Initial auth_alg=0
[ 6166.959158] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6166.959209] wlan0: Initial auth_alg=0
[ 6166.959214] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6167.155261] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6167.354983] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6167.554724] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 6176.956721] wlan0: Initial auth_alg=0
[ 6176.956733] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6176.956781] wlan0: Initial auth_alg=0
[ 6176.956786] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6177.156090] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6177.355778] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6177.555468] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 6181.960188] wlan0: Initial auth_alg=0
[ 6181.960199] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6181.960481] wlan0: Initial auth_alg=0
[ 6181.960488] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6182.156462] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6182.356097] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6182.555994] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 6186.960608] wlan0: Initial auth_alg=0
[ 6186.960619] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6186.960667] wlan0: Initial auth_alg=0
[ 6186.960672] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6187.156844] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6187.356543] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6187.556232] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 6191.960944] wlan0: Initial auth_alg=0
[ 6191.960955] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6191.961248] wlan0: Initial auth_alg=0
[ 6191.961254] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6192.157200] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6192.356895] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6192.556596] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 6196.961370] wlan0: Initial auth_alg=0
[ 6196.961380] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6196.961433] wlan0: Initial auth_alg=0
[ 6196.961437] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6197.157571] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6197.357307] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6197.556996] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 6201.961831] wlan0: Initial auth_alg=0
[ 6201.961842] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6201.961894] wlan0: Initial auth_alg=0
[ 6201.961899] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6202.157913] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6202.357659] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6202.557378] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 6206.962920] wlan0: Initial auth_alg=0
[ 6206.962931] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6206.962993] wlan0: Initial auth_alg=0
[ 6206.962999] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6207.162349] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6207.362060] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6207.561739] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 6211.966573] wlan0: Initial auth_alg=0
[ 6211.966585] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6211.966639] wlan0: Initial auth_alg=0
[ 6211.966644] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6211.968968] wlan0: RX authentication from 00:20:a6:5b:9a:d0 (alg=0 transaction=2 status=0)
[ 6211.968976] wlan0: authenticated
[ 6211.968981] wlan0: associate with AP 00:20:a6:5b:9a:d0
[ 6211.971221] wlan0: authentication frame received from 00:20:a6:5b:9a:d0, but not in authenticate state - ignored
[ 6211.974355] wlan0: RX ReassocResp from 00:20:a6:5b:9a:d0 (capab=0x421 status=0 aid=5)
[ 6211.974362] wlan0: associated
[ 6551.148677] wlan0: RX disassociation from 00:20:a6:5b:9a:d0 (reason=8)
[ 6551.148686] wlan0: disassociated
[ 6551.167296] wlan0: RX deauthentication from 00:20:a6:5b:9a:d0 (reason=3)
[ 6551.167305] wlan0: deauthenticated
[ 6551.182262] wlan0: RX disassociation from 00:20:a6:5b:9a:d0 (reason=8)
[ 6551.182719] wlan0: RX deauthentication from 00:20:a6:5b:9a:d0 (reason=3)
[ 6551.257376] wlan0: Initial auth_alg=0
[ 6551.257385] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6551.258853] wlan0: Initial auth_alg=0
[ 6551.258860] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6551.457846] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6551.657531] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6551.857243] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 6556.258326] wlan0: Initial auth_alg=0
[ 6556.258337] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6556.258610] wlan0: Initial auth_alg=0
[ 6556.258618] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6556.458200] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6556.657945] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6556.857617] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 6561.258425] wlan0: Initial auth_alg=0
[ 6561.258437] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6561.258923] wlan0: Initial auth_alg=0
[ 6561.258930] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6561.458594] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6561.658286] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6561.857981] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 6566.258883] wlan0: Initial auth_alg=0
[ 6566.258894] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6566.259191] wlan0: Initial auth_alg=0
[ 6566.259197] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6566.454980] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6566.654680] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6566.854393] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 6571.263090] wlan0: Initial auth_alg=0
[ 6571.263102] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6571.263151] wlan0: Initial auth_alg=0
[ 6571.263156] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6571.459382] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6571.659078] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6571.858807] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 6576.263640] wlan0: Initial auth_alg=0
[ 6576.263651] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6576.263722] wlan0: Initial auth_alg=0
[ 6576.263727] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6576.459739] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6576.659410] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6576.859157] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 6581.263726] wlan0: Initial auth_alg=0
[ 6581.263738] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6581.263825] wlan0: Initial auth_alg=0
[ 6581.263830] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6581.460123] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6581.659846] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6581.859512] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 6586.264417] wlan0: Initial auth_alg=0
[ 6586.264429] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6586.264709] wlan0: Initial auth_alg=0
[ 6586.264716] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6586.464497] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6586.664198] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6586.863890] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 6591.264578] wlan0: Initial auth_alg=0
[ 6591.264589] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6591.264642] wlan0: Initial auth_alg=0
[ 6591.264647] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6591.460887] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6591.660585] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6591.860305] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 6596.265207] wlan0: Initial auth_alg=0
[ 6596.265219] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6596.265291] wlan0: Initial auth_alg=0
[ 6596.265296] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6596.461290] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6596.660968] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6596.860642] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 6601.265446] wlan0: Initial auth_alg=0
[ 6601.265457] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6601.265508] wlan0: Initial auth_alg=0
[ 6601.265513] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6601.461670] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6601.661368] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6601.861067] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 6611.259241] wlan0: Initial auth_alg=0
[ 6611.259253] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6611.259302] wlan0: Initial auth_alg=0
[ 6611.259308] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6611.458425] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6611.658114] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6611.857835] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 6616.262624] wlan0: Initial auth_alg=0
[ 6616.262636] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6616.262722] wlan0: Initial auth_alg=0
[ 6616.262727] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6616.458804] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6616.658525] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6616.858200] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 6631.248504] wlan0: Initial auth_alg=0
[ 6631.248514] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6631.248710] wlan0: Initial auth_alg=0
[ 6631.248714] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 6631.251053] wlan0: RX authentication from 00:20:a6:5b:9a:d0 (alg=0 transaction=2 status=0)
[ 6631.251059] wlan0: authenticated
[ 6631.251064] wlan0: associate with AP 00:20:a6:5b:9a:d0
[ 6631.252752] wlan0: authentication frame received from 00:20:a6:5b:9a:d0, but not in authenticate state - ignored
[ 6631.258223] wlan0: RX ReassocResp from 00:20:a6:5b:9a:d0 (capab=0x421 status=0 aid=4)
[ 6631.258234] wlan0: associated
[ 7431.626715] wlan0: RX disassociation from 00:20:a6:5b:9a:d0 (reason=8)
[ 7431.626724] wlan0: disassociated
[ 7431.627213] wlan0: RX deauthentication from 00:20:a6:5b:9a:d0 (reason=3)
[ 7431.627220] wlan0: deauthenticated
[ 7431.660042] wlan0: RX disassociation from 00:20:a6:5b:9a:d0 (reason=8)
[ 7431.660545] wlan0: RX deauthentication from 00:20:a6:5b:9a:d0 (reason=3)
[ 7431.735806] wlan0: Initial auth_alg=0
[ 7431.735817] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7431.737303] wlan0: Initial auth_alg=0
[ 7431.737310] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7431.936345] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7432.136006] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7432.335774] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 7441.729737] wlan0: Initial auth_alg=0
[ 7441.729747] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7441.730017] wlan0: Initial auth_alg=0
[ 7441.730022] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7441.929143] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7442.128793] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7442.328563] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 7446.733011] wlan0: Initial auth_alg=0
[ 7446.733021] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7446.733311] wlan0: Initial auth_alg=0
[ 7446.733316] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7446.929470] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7447.129231] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7447.328944] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 7451.733531] wlan0: Initial auth_alg=0
[ 7451.733542] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7451.733842] wlan0: Initial auth_alg=0
[ 7451.733848] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7451.929884] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7452.129658] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7452.329247] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 7456.737825] wlan0: Initial auth_alg=0
[ 7456.737837] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7456.737910] wlan0: Initial auth_alg=0
[ 7456.737916] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7456.934314] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7457.133958] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7457.333650] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 7461.738467] wlan0: Initial auth_alg=0
[ 7461.738478] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7461.738760] wlan0: Initial auth_alg=0
[ 7461.738767] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7461.934630] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7462.134325] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7462.334062] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 7481.720641] wlan0: Initial auth_alg=0
[ 7481.720649] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7481.722373] wlan0: Initial auth_alg=0
[ 7481.722378] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7481.920190] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7482.119852] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7482.319571] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 7486.724264] wlan0: Initial auth_alg=0
[ 7486.724276] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7486.724360] wlan0: Initial auth_alg=0
[ 7486.724365] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7486.920626] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7487.120281] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7487.319997] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 7491.724253] wlan0: Initial auth_alg=0
[ 7491.724260] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7491.724285] wlan0: Initial auth_alg=0
[ 7491.724288] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7491.920956] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7492.120671] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7492.320382] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 7496.724636] wlan0: Initial auth_alg=0
[ 7496.724643] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7496.724760] wlan0: Initial auth_alg=0
[ 7496.724763] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7496.921365] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7497.121051] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7497.320760] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 7501.725252] wlan0: Initial auth_alg=0
[ 7501.725263] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7501.725541] wlan0: Initial auth_alg=0
[ 7501.725549] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7501.921773] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7502.121411] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7502.321114] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 7506.725851] wlan0: Initial auth_alg=0
[ 7506.725862] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7506.726007] wlan0: Initial auth_alg=0
[ 7506.726013] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7506.922112] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7507.121853] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7507.321506] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 7511.726524] wlan0: Initial auth_alg=0
[ 7511.726532] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7511.726554] wlan0: Initial auth_alg=0
[ 7511.726557] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7511.731958] wlan0: RX authentication from 00:20:a6:5b:9a:d0 (alg=0 transaction=2 status=0)
[ 7511.731963] wlan0: authenticated
[ 7511.731967] wlan0: associate with AP 00:20:a6:5b:9a:d0
[ 7511.732756] wlan0: authentication frame received from 00:20:a6:5b:9a:d0, but not in authenticate state - ignored
[ 7511.735401] wlan0: RX deauthentication from 00:20:a6:5b:9a:d0 (reason=6)
[ 7511.735405] wlan0: deauthenticated
[ 7512.733266] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7512.736922] wlan0: RX authentication from 00:20:a6:5b:9a:d0 (alg=0 transaction=2 status=0)
[ 7512.736928] wlan0: authenticated
[ 7512.736932] wlan0: associate with AP 00:20:a6:5b:9a:d0
[ 7512.744667] wlan0: RX ReassocResp from 00:20:a6:5b:9a:d0 (capab=0x421 status=0 aid=3)
[ 7512.744676] wlan0: associated
[ 7819.872470] Inbound IN=wlan0 OUT= MAC=00:1d:e0:9b:69:99:00:1e:4c:63:a6:b4:08:00 SRC=65.124.17.249 DST=65.124.17.75 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=21084 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 7821.295322] Inbound IN=wlan0 OUT= MAC=00:1d:e0:9b:69:99:00:1e:4c:63:a6:b4:08:00 SRC=65.124.17.249 DST=65.124.17.75 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=21086 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 7823.716638] Inbound IN=wlan0 OUT= MAC=00:1d:e0:9b:69:99:00:1e:4c:63:a6:b4:08:00 SRC=65.124.17.249 DST=65.124.17.75 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=21088 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 7988.335861] wlan0: RX disassociation from 00:20:a6:5b:9a:d0 (reason=8)
[ 7988.335867] wlan0: disassociated
[ 7988.336411] wlan0: RX deauthentication from 00:20:a6:5b:9a:d0 (reason=3)
[ 7988.336413] wlan0: deauthenticated
[ 7988.368817] wlan0: RX disassociation from 00:20:a6:5b:9a:d0 (reason=8)
[ 7988.369329] wlan0: RX deauthentication from 00:20:a6:5b:9a:d0 (reason=3)
[ 7988.443947] wlan0: Initial auth_alg=0
[ 7988.443957] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7988.445427] wlan0: Initial auth_alg=0
[ 7988.445435] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7988.644234] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7988.844000] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7989.043622] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 7998.437893] wlan0: Initial auth_alg=0
[ 7998.437905] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7998.437987] wlan0: Initial auth_alg=0
[ 7998.437993] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7998.637004] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7998.836688] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7999.036392] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 8003.440992] wlan0: Initial auth_alg=0
[ 8003.441002] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 8003.441270] wlan0: Initial auth_alg=0
[ 8003.441276] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 8003.637383] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 8003.837131] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 8004.036816] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 8008.441557] wlan0: Initial auth_alg=0
[ 8008.441567] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 8008.441847] wlan0: Initial auth_alg=0
[ 8008.441853] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 8008.637800] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 8008.837497] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 8009.037150] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
```

---

### Post by pytheas22 on 2008-07-14
Thanks for the dmesg.

I think that your issue may be related to this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217809").  There, they mention that applying all system updates may fix the problem.  Someone also suggests that it seems to be related to using a WPA-password that includes quotes (" ') and blank spaces ( ).  Does your passphrase include such characters, and have you applied all updates to your system?  If you have, then there are other things to try, but please let me know the status of these things first.

Also, when the Internet breaks, do these commands make it work again:
```

sudo rmmod iwl4965
sudo modprobe iwl4965
```

Then wait a few seconds and it should connect again.

Finally, a work-around for your problem would be to use ndiswrapper.  This shouldn't be necessary because Intel wireless cards should work very well on Linux--this is just some bug that you're having--but ndiswrapper would also make the card work, hopefully without being buggy.  To do that, you would do:

First, download the Windows drivers for your card from here, extract the .zip file and save it to your desktop.

Then run these commands in a terminal:
```

sudo apt-get install ndiswrapper*
cd ~/Desktop/V11*
sudo ndiswrapper -i netw4x32.inf
```

(***important--if you are using a 64-bit system, replace the last command above with:
```

sudo ndiswrapper -i netw4x64.inf
```

then continue to follow the normal steps below)

```
sudo ndiswrapper -m
sudo -s
echo 'blacklist iwl4965' >> /etc/modprobe.d/blacklist
```

(These instructions are based on [this]("http://ubuntuforums.org/showpost.php?p=2829876&postcount=1"), a tutorial for KDE for your card).

Then reboot and your wireless should be working better.  But I emphasize that ndiswrapper is only a work-around, not a real solution.  It would be preferable to get your card working reliably with the native Linux driver.

---

### Post by einnar on 2008-07-14
That bug report seems to be mostly 8.04. I'm on 64bit 7.10. Fully patched and updated. The passkey contains no spaces or symbols.

 I'll try the modprobe next time it quits...

I'm also having another issue [HERE]("http://ubuntuforums.org/showthread.php?t=859711"). Not sure if it's related or not.

Does it matter that I'm not running KDE for the purposes of that fix, and/or tutorial?

thanks again.

---

### Post by pytheas22 on 2008-07-15
> That bug report seems to be mostly 8.04. I'm on 64bit 7.10. Fully patched and updated. The passkey contains no spaces or symbols.

Sorry, didn't realize this.  The problems described in the bug report still seem similar to yours, though.
> 
I'm also having another issue HERE. Not sure if it's related or not.

I don't think it's related, but you never know.
> 
Does it matter that I'm not running KDE for the purposes of that fix, and/or tutorial?

No, it should work fine on Gnome; that's why I wrote out the steps here instead of just linking to the tutorial.  As long as you make sure to use the right Windows driver for 64-bit, it should work fine.

---

### Post by einnar on 2008-07-15
The following code : 

```
sudo rmmod iwl4965
sudo modprobe iwl4965
```


Does reconnect me to the network.
I'll look at the tutorial, and let you know.

Thanks again. :)

---

### Post by einnar on 2008-07-15
the tutorial killed my card completely...
```

sudo rmmod iwl4965
ERROR: Module iwl4965 does not exist in /proc/modules
```

Got this a few times, but eventually the 2 commands I used before brought it back. It doesn't last through a reboot, though, and doesn't last for anywhere near as long as it did before.

Any thoughts?

---

### Post by einnar on 2008-07-15
Okay.. got it to come up.. 

I added the following to /etc/modules

ndiswrapper
iwl4965

I tried ndiswrapper by itself, after rereading that other tutorial. No effect. After adding iwl4965 below it, I'm back on the network.

I'll let you know how long.

---

### Post by einnar on 2008-07-15
About 5 mins, apparently.. and i have to :

sudo rmmod iwl4965
sudo modprobe iwl4965

....to get it to work...

---

### Post by einnar on 2008-07-15
It's dropping the card now. Before, I could see the card. Now it's just forgetting the card is there every 3-5 minutes.

how do I undo the last "fix" ? :(

---

### Post by pytheas22 on 2008-07-17
ndiswrapper should work; I'm not sure why it won't.

You can uninstall ndiswrapper, though, with:
```

sudo apt-get remove --purge ndiswrapper*
```

Also, if both ndiswrapper and iwl4965 are in /etc/modprobe.d/blacklist, then I'm not sure which driver is controlling your card now.  What is the output of:
```

lshw -C Network
lsmod | grep iwl
```

I'm travelling now so I apologize if I can't respond quickly, but I'll do my best.

---

