---
title: "NEED HELP with WIRELESS!"
date: 2007-12-02
forum: System76 Support
---

### Post by hodad on 2007-12-02
Bought a Pangolin laptop a month ago, and I love it - BUT - I have now logged approximately 24 hrs trying to get the internet to work seamlessly.  Here's the basic problem:  On the road, I try to get wireless to work, (which it did on one occasion).  When I get home, I plug in my wired internet connection (to eth2) and have to change the network settings with the System - Network/Network Tools apps. to get the wired network to work, which in turn hoses the wireless settings.  As a solution, I bought a Linksys Wireless G router (WRT54G) , in order to be wireless all of the time, and try to skirt the problem.   

 I can ping the wireless g, and access it's setup page. I can ping my internet provider, but can't ping the associated gateway at the internet provider.

Here's what I get with "route -n" after disabling the wired port eth2:

Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
216.52.32.0 0.0.0.0 255.255.255.128 U 0 0 0 eth3
169.254.0.0 0.0.0.0 255.255.0.0 U 0 0 0 eth2
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 eth3
0.0.0.0 216.52.32.126 0.0.0.0 UG 100 0 0 eth3
0.0.0.0 0.0.0.0 0.0.0.0 U 1000 0 0 eth2

the first line is for my internet provider, but the gateway for the provider is in the next to last line, not in the same line as the internet destination (?). I don't know what 169.254.0.0. is (I think it's someone elses wireless).

Since I can ping the network provider, but not the gateway, could it be some gateway setting problem?

also, here's what I get with iwconfig and ifconfig:

..l@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

eth3      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:641   Missed beacon:0

..l@ubuntu:~$ ifconfig
eth2      Link encap:Ethernet  HWaddr 00:16:D4:DE:DB:3C  
          inet addr:216.52.32.4  Bcast:216.52.32.127  Mask:255.255.255.128
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:62705 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3701 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9783075 (9.3 MB)  TX bytes:540220 (527.5 KB)
          Interrupt:16 

eth3      Link encap:Ethernet  HWaddr 00:1C:BF:19:CF:42  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1 dropped:644 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8066 (7.8 KB)  TX bytes:6034 (5.8 KB)
          Interrupt:16 Base address:0x8000 Memory:f8200000-f8200fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:118 errors:0 dropped:0 overruns:0 frame:0
          TX packets:118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11095 (10.8 KB)  TX bytes:11095 (10.8 KB)

Anyone have any ideas; I can't afford to waste any more time on this problem.

Thanks in advance!
__________________
Edit/Delete Message

---

### Post by thomasaaron on 2007-12-03
Here's the gist of it:

1. Your /etc/network/interfaces file is hosed. You need to go to a terminal and type: sudo gedit /etc/network/interfaces and make it look like this:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
```

Once you've done that, you should connect via network manager (the icon in the upper right of your screen), not via System>Admin>Network. There should be virtually NO manual configuration involved, other than entering your WEP key.

2. Network Manager and your Wireless Router should be set up EXACTLY alike. If they are not, you'll have issues. If the router is set to "Open System / 64-bit Hex", that is how Network Manager must be set. Easily 95% of problems we have with wireless are caused by network manager being set up ALMOST EXACTLY like the router.

3. Click on the icon in the upper right of your screen and select your wirless network. (If you don't see it, it is not turned on in your router.) You will be prompted for the wep key (if you've set one up). Once you enter it, you should easily connect.

If this doesn't get you going, please give detailed information on how your wireless router is configured.

---

### Post by hodad on 2007-12-03
Tom,
I made the changes to the "interfaces" file. I then (at your  suggestion) reset the wireless router with the reset button on the back. I then hooked the laptop to one of the hardwired ports on the back of the wireless router.  The "internet" connector was hooked up to the internet modem (wireless microwave modem located outside).   After doing these, I rebooted, and was able to connect to the wireless router (in hardwired mode) and enter it's setup screen (BASIC setup tab).

At this point, I could see that the router was configured for DHCP.  I could still not connect thru firefox to the internet (though I could ping the URL of the internet provider, which meant the hardware connection was OK).

I unselected DHCP on the basic setup screen on the Wireless G, chose "static IP", and a new screen appeared asking for the IP, GW, and DNS server addresses.  I then entered the proper addresses for my ISP and tried Firefox.  The connection came up immediately,so problem solved.

Thanks for your help!

---

