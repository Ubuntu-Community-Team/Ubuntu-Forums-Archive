---
title: "Serval P3 drops wireless connections with 10.04"
date: 2010-06-08
forum: System76 Support
---

### Post by jdmelton on 2010-06-08
I have a Serval P3 and have performed a fresh install of 10.04 LTS i386. All updates/upgrades are applied.

The wireless connection drops after a few minutes and can not find the wireless router afterwards.

I read about this somewhere but have not found the thread again. I believe it is a problem with 10.04 and not the hardware or the router. The reason is that I can boot with the 8.04 LTS i386 CDROM and the wireless connection does not drop, ever.

With a boot from 8.04 LTS, I get 98% on signal strength and only 77% with 10.04 LTS in the same spot. My spot is about 15 feet from the wireless router with one intervening sheetrock wall.

I remember reading about a timeout issue somewhere, but can not find the thread again. I read the thread some weeks before I installed 10.04. I do not know if a fix was found.

If I run ping -i 35 xxx.xxx.xxx.xxx, the wireless does not drop. If I increase the time to 40 seconds, the wireless drops after a few minutes. The time until it drops is not consistent and varies from a couple of minutes to an hour. The one consistent aspect of the problem is that drops occur after periods of no network activity. I have not experienced any dropped connections while downloading a file or while running ssh with a keep alive setting at 20 seconds.

I did a test over a week with a CRON job that ran ping every 35 seconds and did not experience any drops. (I had the bash cron script test the return from the pings.)

No such problem has ever occured while running 8.04 LTS (i386 or AMD64). I also did not experience this problem under 9.10 i386.

The router has always been set up the same. Again, I do not consider the problem to be with my wireless router since the problem fixes itself merely by booting the 8.04 i386 CDROM. I also experience drops now at my favorite Barnes & Noble where I have been using this Serval since I bought it in late 2007.

Just before typing this post, I had left the Serval on for 3 days straight while running 8.04 and did not have any dropped connections. We had heavy thunderstorms and lightening, yet the connection did not drop and remained over 90%. I rebooted a half hour or so ago to the installed 10.04 i386 and the wireless dropped within 5 minutes of network inactivity.

Relevant return from ifconfig:
wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:6c:30:a1  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:bfff:fe6c:30a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51484 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27037 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:77739950 (77.7 MB)  TX bytes:2359121 (2.3 MB)

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: xx:xx:xx:xx:xx:xx
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=sb v2.09 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:33 memory:f0000000-f000ffff
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 02
       serial: xx:xx:xx:xx:xx:xx
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.1 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:32 memory:f8000000-f8000fff

I happen to have a Meerkat with the DLink USB wireless adapter. I plugged it in and connected it to the same wireless router. The DLink connection did not ever drop while the installed connection did. The DLink signal strength was also in the 90s.

If there is a thread with an answer to this problem, would someone please point me to it?

(I do need to update my signature for 10.04...)
Otherwise, any advice on how to fix this?

---

### Post by isantop on 2010-06-09
Make sure you have the System76-Driver installed, and that you have clicked on "Restore" under the restore tab. It should make sure you have all the drivers for your computer. We have similar issues with starlings, and doing this usually makes the problem resolve itself.

You can also try a 64-bit image. It could make a difference in how the OS interacts with the hardware, even if this is a bit unlikely.

---

### Post by thomasaaron on 2010-06-09
jdmelton,

Your wireless card (a 3945, I believe) is supported out of the box by Ubuntu. So, the problem is most likely one of two things: a flakey wireless card or a flaky wireless access point. Please try re-booting the access point (even if other computers do *not* drop the connection). Sometimes the firmware gets weirded out, and a reboot helps.

Also, can you test to see if you experience connection-dropping on a different access point? If you do, it most likely is your wireless card becoming flaky.

---

### Post by jdmelton on 2010-06-09
isantop,

I have not kept up to date on the Ssytem76 driver. My belief was that it did not support 10.04 LTS i386. Has this changed? If so, I can install it. However, I do not think it is needed. As thomasaaron noted, 10.04 seems to support this SER-P3 natively. I should add that it also natively supports the touch pad and I am able, for the first time, to disable tapping!

I have not tried 64-bit 10.04 yet. I may try that after my next full backup.


thomasaaron,

I do not leave my wireless router on all the time. I suspected it first. It has had power cycled and been rebooted many times. My Meerkat has solid connectivity all the time, whenever it is powered up. I also have a neighbor who kindly allowed me to connect with his wireless network. Same drop problem and same remedies (ping -i 35 or boot with 8.04 CDROM).

I should have went in to more detail, but I did mention that the 10.04 i386 version drops connections in my local Barnes & Noble. I have been using the Serval there since December 2007.

What is really weird to me is that booting with an 8.04 LTS i386 CDROM does not have the problem. I have experimented with that several times, as noted in my original post. Since no problems were encountered, I concluded that the wireless card was not the problem. That conclusion could be an error, of course.

I burned a 9.10 i386 CDROM and booted live from it. No dropped connections. I am not sure why no problems occur with live 8.04 and 9.10 boots yet occur readily with installed 10.04. (All i386.) I should make it clear that my boots with 8.04 and 9.10 are from the desktop i386 CDROMs and that I run the live system with them. Only 10.04 is installed on the internal hard drive.

My current work around is to run ping -i 35 xxx.xxx.xxx.xxx. So long as ping is running, the connection does not drop. If I change to ping -i 40 xxx.xxx.xxx.xxx, the connection drops in a few minutes. (xxx.xxx.xxx.xxx is the wireless router's ip address.)

In the event that my wireless card is flaky, are there any replacements available?

I will be really sad if parts start dying on my Serval. This workhorse has been my all-time favorite pet of pets.

---

### Post by thomasaaron on 2010-06-10
If you want to install the latest System76 Driver, you can go to....

[http://planet76.com/repositories](http://planet76.com/repositories)

Click the second link from the bottom. But I don't think it currently provides any support for your machine.

We don't test with the 32-bit version of 10.04, but I'd be surprised if that is the problem. Can you test with a 10.04 64-bit live CD? We've got an awful lot of systems out there with the 3945 wireless card, and I'm not hearing of any issues across the board -- although most folks probably are running 64-bit.

---

