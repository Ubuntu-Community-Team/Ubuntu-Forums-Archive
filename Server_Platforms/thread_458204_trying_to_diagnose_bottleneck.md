---
title: "trying to diagnose bottleneck"
date: 2007-05-29
forum: Server Platforms
---

### Post by dfreer on 2007-05-29
Hi everyone,

I recently installed a Intel PRO/1000 gigabit card in my LAN file server, and I can't seem to get consistant download speeds. At times, I get around 1000-2000 Kb/s, which is great. But most of the time I get 110 Kb/s, which isn't nearly enough to stream my video files consistently :(

Here's some of the server specs:
500 Mhz Pentium III
512 Mb's of RAM
1 - 40 GB 7200 RPM IDE seagate containing most of the OS and swap
1 - 250 GB 7200 RPM IDE seagate with my video files
1 - 160 GB 7200 ROM External USB maxtor with some more video/music
100 MB generic intel ethernet card for internet
1000 MB Intel PRO ehternet card for LAN use

The gigabit card plugs directly into a Netgear Gigabyte 8-port Switch, which is connected directly to a Netgear Wireless 54 Mb b/g router. The router is acting as the router for the entire LAN. The 100 MB card plugs directly into the wireless router. All cables are regular Cat 6 cables (I upgraded to Cat 6 thinking that this was the reason I was getting horrible bandwidth.

The client computer is my laptop, with a Intel wireless 54 Mb a/b/g card. It also has a Intel PRO/1000 Gigabyte ethernet port (I'm pretty sure I hit this bandwidth issue even using this ethernet card plugged straight into the Gigabyte switch, although I will try again just to make sure).

Anyways, I'm just not quite sure which tests to run to figure out where I'm hitting this bottleneck, whether it is a network traffic issue (maybe my windows machines are congesting the network?), a processor speed issue, hard drive I/O, or if it is my wireless card? I've been struggling with this issue for about 2 months now, any help would be appreciated. 

Mainly, just what tests should I run to diagnose the problem?

EDIT: Some screenshots while using the wireless in the same room, approx 10-15 ft away from router:
[http://www.dfreer.org/~dfreer/screenshots/nettraffic1.png](http://www.dfreer.org/~dfreer/screenshots/nettraffic1.png)
[http://www.dfreer.org/~dfreer/screenshots/nettraffic2.png](http://www.dfreer.org/~dfreer/screenshots/nettraffic2.png)

In the top left, I have ethstatus running on the server, to show the network activity of the gigabit card. Note in the first screenshot it is at 228 Kb/s, and in the second screenshot it is at zero. It does this consistantly, like water dripping on/off/on/off.
at the bottom left of the screenshots I have network monitor on my laptop. Note in both screens it reports ~120 Kb/s, and the graph shows the speed as being pretty steady.
On the right side I am running htop on the server. Note processor usage and RAM usage, it isn't doing much at all (the only thing I have it doing is moving some files between the 2 media drives).

Please help anyone? Do i need to have crossover Cat 6 cables for gigabyte networking, could that explain the "on/off" behaviour?

---

### Post by tgm4883 on 2007-05-29
> **dfreer said:**
> Hi everyone,

I recently installed a Intel PRO/1000 gigabit card in my LAN file server, and I can't seem to get consistant download speeds. **At times, I get around 1000-2000 Kb/s, which is great. But most of the time I get 110 Kb/s, which isn't nearly enough to stream my video files consistently :(**

Here's some of the server specs:
500 Mhz Pentium III
512 Mb's of RAM
1 - 40 GB 7200 RPM IDE seagate containing most of the OS and swap
1 - 250 GB 7200 RPM IDE seagate with my video files
1 - 160 GB 7200 ROM External USB maxtor with some more video/music
100 MB generic intel ethernet card for internet
1000 MB Intel PRO ehternet card for LAN use

The gigabit card plugs directly into a Netgear Gigabyte 8-port Switch, which is connected directly to a Netgear Wireless 54 Mb b/g router. The router is acting as the router for the entire LAN. The 100 MB card plugs directly into the wireless router. All cables are regular Cat 6 cables (I upgraded to Cat 6 thinking that this was the reason I was getting horrible bandwidth.

The client computer is my laptop, with a Intel wireless 54 Mb a/b/g card. It also has a Intel PRO/1000 Gigabyte ethernet port (I'm pretty sure I hit this bandwidth issue even using this ethernet card plugged straight into the Gigabyte switch, although I will try again just to make sure).

Anyways, I'm just not quite sure which tests to run to figure out where I'm hitting this bottleneck, whether it is a network traffic issue (maybe my windows machines are congesting the network?), a processor speed issue, hard drive I/O, or if it is my wireless card? I've been struggling with this issue for about 2 months now, any help would be appreciated. 

Mainly, just what tests should I run to diagnose the problem?

1000-2000 Kb/s is not great.  My gigabyte switch bit the dust so im only hooked up through my 10/100 ddwrt router, but I averaged a 9190.41 KB/s on an ftp transfer from my fileserver to my desktop even though only connected at 100Mb/s.  

Having said that, i'm not sure what the load is that it's puting on your processor, or if you run a gui or anything else.  But here are the specs on my fileserver.

Athlon XP 2000+
768MB RAM
10GB HD for OS and SWAP
150GB and 200GB HD LVM together for DVD storage
2X 300GB Software RAID for personal files and backups
All HD's are 7200RPM.  1 of the 300GB drives is on a PCI IDE controller
Gigafast NIC (Gigabyte, but currently hooked up to a wrt54G running ddwrt)

---

### Post by dfreer on 2007-05-29
> **tgm4883 said:**
> 1000-2000 Kb/s is not great.  My gigabyte switch bit the dust so im only hooked up through my 10/100 ddwrt router, but I averaged a 9190.41 KB/s on an ftp transfer from my fileserver to my desktop even though only connected at 100Mb/s.  

Having said that, i'm not sure what the load is that it's puting on your processor, or if you run a gui or anything else.  But here are the specs on my fileserver.

Athlon XP 2000+
768MB RAM
10GB HD for OS and SWAP
150GB and 200GB HD LVM together for DVD storage
2X 300GB Software RAID for personal files and backups
All HD's are 7200RPM.  1 of the 300GB drives is on a PCI IDE controller
Gigafast NIC (Gigabyte, but currently hooked up to a wrt54G running ddwrt)

I didn't think it was that great either, but it was better than 120 Kb/s! I remember using a Cat5e crossovers between my gigabyte switch to my core 2 duo laptop with gigabyte to my friends AMD64 laptop with gigabyte cards and getting something like 11 Mb/s, close to 13! Well, I'll try to hook up to it using my gigabyte ethernet port and run some tests, in the meantime anyone want to look at the screenshots I posted above?

---

### Post by tgm4883 on 2007-05-29
Your connected wirelessly, that's going to give you much lower results that 1000Mb/s.  Also, running a gui on your server is also putting a load on it.  I would have it boot to console, connect your laptop directly to the gigabyte switch (what kind of laptop?), disable your wireless on your laptop, and run the test again.

---

### Post by tgm4883 on 2007-05-29
I would also like to note that your network is transfering at around 60% of the theoretical limit of your network speed (per your posted pics).  I would conclude that your transferring via wireless and that your connection isn't that great.

:EDIT:

To add to that, my network transfers at around 80%, but I have no encryption overhead.

---

### Post by dfreer on 2007-05-29
not running a GUI on my server, sorry (only a 500 mhz processor :) ) I took the screenshots using ssh and my laptop. I just plugged in using my gigabyte ethernet port on my laptop straight into the gigabyte switch, with wireless hardware switch turned off, the results are slightly better, but still not very good at about 200 Kb/s (and that weird on/off thing is even more evident). laptop is a HP dv6000t with 2.0 Ghz core 2 duo, ubuntu feisty, IPv6 disabled (same with server, IPv6 is disabled) 1 GB RAM, btw.

screenshots up in a few seconds.

EDIT: 
[http://www.dfreer.org/~dfreer/screenshots/nettraffic3.png](http://www.dfreer.org/~dfreer/screenshots/nettraffic3.png)
[http://www.dfreer.org/~dfreer/screenshots/nettraffic4.png](http://www.dfreer.org/~dfreer/screenshots/nettraffic4.png)

Just to be a bit clearer. The server is not running a GUI, the screenshots involving htop and ethstatus were taken from the laptop over ssh. The network monitor was showing the reported network speeds over the wireless on my laptop. The NEW screenshots above show ethstatus running once again on the server over ssh, and system monitor running on my laptop using the gigabyte ethernet port on my laptop.

Thanks for the help guys!

---

### Post by tgm4883 on 2007-05-29
Have you verified that it is a problem with the server and not with the laptop?  ie, have you tried transfering to a different computer and seen the same results?

---

### Post by dfreer on 2007-05-29
> **tgm4883 said:**
> Have you verified that it is a problem with the server and not with the laptop?  ie, have you tried transfering to a different computer and seen the same results?

no more linux machines to try it with, I'll try it from one of my windows XP machines, thanks! gimme about 2 mins.
EDIT: I'm actually also wondering if it could be a routing issue... eventually i'll try swapping in another router but first things first windows machine tests!

---

### Post by dfreer on 2007-05-29
ok, my parent's windows XP machine is pretty gay, won't let me open task manager cuz it says it has been disabled by the system administrator :confused: but whatever. So i just used an http download as a speed measure... got like ~3-4 Mb/s. This is on a old XP machine with a 100 Mb/s card plugged into the switch.

So I decided to try a http download using my ubuntu laptop, instead of streaming the video file using Totem. Got like 8-9 Mb/s... over the gigabit card. hmmm. Firefox reports a steady ~9 Mb/s download, whereas System monitor shows that same on/off/on/off thing, with on being ~20 Mb/s and off being 0 kb/s.

Using totem still uses about 400 Kb/s in system monitor though. hmmm.

It seems like the network is up again, but like I said it seems like this problem will come and go, kinda like bandwidth from your ISP. Like during the day when everyone is using it you get sucky bandwidth, at night you get great bandwidth :p seems like my local LAN server is moody this way too. I'll let you know when I see it acting up again what my bandwidth speeds are like from the LAN.

---

### Post by tgm4883 on 2007-05-29
Sounds like a buffering issue

---

### Post by dfreer on 2007-05-29
> **tgm4883 said:**
> Sounds like a buffering issue

Like with totem? The only thing I've noticed is that totem refuses to buffer more than like 10 secs in the movie... which is a pointless thing to do IMO. I tried using mplayer, but it brings up this error: 

Couldn't resolve name for AF_INET6: servers_ip_address

VLC seems to work ok from wireless, about 200 Kb/s, no more on/off behaviour client side (although the server still does on/off).

Direct http download via wireless gives me about 2800 Kb/s

I guess that is acceptable for now. Thank again!

---

### Post by regomodo on 2007-06-01
Um, i'm not sure if this is of any help but i had a few ideas whilst reading this thread.

 - Is your wireless encrypted? Someone might be on your lan.
 - Are your drives set to use DMA? You say that your CPU is doing little whilst transferring so the drives probably are
 - Are your cables of decent quality? 

Those are a few things i would have checked but they are probably useless hints

---

### Post by dfreer on 2007-06-01
> **regomodo said:**
> Um, i'm not sure if this is of any help but i had a few ideas whilst reading this thread.

 - Is your wireless encrypted? Someone might be on your lan.
 - Are your drives set to use DMA? You say that your CPU is doing little whilst transferring so the drives probably are
 - Are your cables of decent quality? 

Those are a few things i would have checked but they are probably useless hints

Thanks for the info, not useless! 

In fact, it could very well be all three of those things. I haven't messed with DMA since I got my new laptop, I didn't even think about that. Also, although all of the network cables should be of decent quality (I original though this was the problem, so I replaced all the old network cables (various cat 5/e straight's and crossovers) with new Cat 6 straight-thru cables from newegg.com. 
But the IDE cables! hmmm they may be a concern, this server is basically a 500 mhz POS I picked up out of the garage... I think if they were damaged i would be having a heck of a lot more problems (umm corrupted data anyone?), but they very well may be the old 40 pin cables instead of the new 80 pins (EIDE, Ultra-IDE, something? ATA-100 ATA-133? Been so long since I've messed with hardware). 

New info: Doing some testing of the network the last couple days. Seems like some days I can get ~2-3 Mb/s from all around the house (and generally the entire day I can use that much), some days I still get around 100-400 Kb/s.... :( So the problem is not solved yet.

Ok, so back to testing!

I'll work on testing DMA and making sure it is turned on.

EDIT: oops I'm stupid, ignore that last line :D
NEW EDIT: Ok did some tests using hdparm:
I have 3 hard drives on this server, hda, hdc, sda (external USB)
I have media on all three drives, it hasn't seemed like one drive's media is slower than the rest but I'll test!

DMA Tests
```
~$ sudo hdparm /dev/hda
/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 16383/255/63, sectors = 78165360, start = 0

~$ sudo hdparm /dev/hdc
/dev/hdc:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 30401/255/63, sectors = 488397168, start = 0

~$ sudo hdparm /dev/sda
/dev/sda:
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 19929/255/63, sectors = 320173056, start = 0
```



Speed tests
```
~$ sudo hdparm -t /dev/hda
/dev/hda:
 Timing buffered disk reads:   80 MB in  3.03 seconds =  26.40 MB/sec

~$ sudo hdparm -t /dev/hda
/dev/hda:
 Timing buffered disk reads:   84 MB in  3.04 seconds =  27.63 MB/sec

~$ sudo hdparm -t /dev/hdc
/dev/hdc:
 Timing buffered disk reads:   90 MB in  3.04 seconds =  29.61 MB/sec

~$ sudo hdparm -t /dev/hdc
/dev/hdc:
 Timing buffered disk reads:   90 MB in  3.02 seconds =  29.80 MB/sec

~$ sudo hdparm -t /dev/sda
/dev/sda:
 Timing buffered disk reads:    4 MB in  4.01 seconds = 1021.45 kB/sec

~$ sudo hdparm -t /dev/sda
/dev/sda:
 Timing buffered disk reads:    4 MB in  4.04 seconds = 1013.86 kB/sec

```

For comparison, my SATA 5400 RPM laptop hard drive gets ~37.23 MB/sec :D

---

### Post by regomodo on 2007-06-01
i'll assume /dev/sda is a usb1 device then? otherwise that's one crpa drive!

Your hdparm results are as i expected. There's only 1 distro that i've tried that didn't turn on dma by default (slack).

Other than interference on your cat cable (yeah right) or a faulty NIC i have no other ideas.

Oh, the throughput for your disk seem ok so i doubt the ide cables are iffy, unless those speeds are raw speeds i.e not taking into errors/checking/correction

Soz mate no idea. Hopefully someone more knowledgeable can help?

---

### Post by dfreer on 2007-06-02
thanks for the help, I forgot about DMA. I'm thinking my old Debian box didn't turn DMA on for my DVD drive, but i digress. 
it *shouldn't* be USB 1.1, at least the drive is USB 2.0 compatible, hmm. Any ideas on how to check usb speeds?

May 28 23:26:26 myserver kernel: [ 6277.556047] usb 1-2: new full speed USB device using uhci_hcd and address 4
At least on May 28 I was using USB 2.0, if that means what I think it means.

uh oh. check this out guys:
```
~$ dmesg
[143180.046143] NETDEV WATCHDOG: eth0: transmit timed out
[143180.047539] 0000:00:10.0: tulip_stop_rxtx() failed (CSR5 0xfc06c012 CSR6 0xff974111)
[143180.048940] 0000:00:10.0: tulip_stop_rxtx() failed (CSR5 0xfc06c012 CSR6 0xff974111)
[143188.044872] NETDEV WATCHDOG: eth0: transmit timed out
[143188.046273] 0000:00:10.0: tulip_stop_rxtx() failed (CSR5 0xfc06c012 CSR6 0xff974111)
[143188.047673] 0000:00:10.0: tulip_stop_rxtx() failed (CSR5 0xfc06c012 CSR6 0xff974111)
[143192.552373] 0000:00:10.0: tulip_stop_rxtx() failed (CSR5 0xfc06c012 CSR6 0xff974111)
[143195.875492] e1000: eth1: e1000_watchdog_task: NIC Link is Up 1000 Mbps Full Duplex
[143202.444250] 0000:00:10.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[143202.444280] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[143829.714422] 0000:00:10.0: tulip_stop_rxtx() failed (CSR5 0xfc06c012 CSR6 0xff970111)
[143832.614246] e1000: eth1: e1000_watchdog_task: NIC Link is Up 1000 Mbps Full Duplex
[143839.182993] 0000:00:10.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[143839.183024] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[154331.422959] usb 1-2: USB disconnect, address 4

```

The first 3 lines are repeated from the very beginning of dmesg all the way to the bottom where I copy and pasted the code, where it abruptly changes error messages and stops. some more logs:
```
~$ /var/log/messages # trying to show only relevent info
May 27 15:20:54 myserver kernel: [   84.907313] e1000: eth1: e1000_watchdog_task: NIC Link is Up 1000 Mbps Full Duplex

#trouble starts after this point
May 28 21:12:58 myserver -- MARK --
May 28 21:20:55 myserver kernel: [29385.886115] NETDEV WATCHDOG: eth1: transmit timed out
May 28 21:21:03 myserver kernel: [29393.884773] NETDEV WATCHDOG: eth1: transmit timed out
May 28 21:21:11 myserver kernel: [29401.883513] NETDEV WATCHDOG: eth1: transmit timed out
May 28 21:21:19 myserver kernel: [29409.882234] NETDEV WATCHDOG: eth1: transmit timed out
May 28 21:21:27 myserver kernel: [29417.880959] NETDEV WATCHDOG: eth1: transmit timed out
May 28 21:21:35 myserver kernel: [29425.879691] NETDEV WATCHDOG: eth1: transmit timed out
May 28 21:21:43 myserver kernel: [29433.878435] NETDEV WATCHDOG: eth1: transmit timed out
May 28 21:21:55 myserver kernel: [29445.876510] NETDEV WATCHDOG: eth1: transmit timed out
May 28 21:22:03 myserver kernel: [29453.875235] NETDEV WATCHDOG: eth1: transmit timed out
# ...... This goes on for 2 days straight!
May 30 13:28:30 myserver kernel: [143180.046143] NETDEV WATCHDOG: eth0: transmit timed out
May 30 13:28:38 myserver kernel: [143188.044872] NETDEV WATCHDOG: eth0: transmit timed out
May 30 13:28:46 myserver kernel: [143195.875492] e1000: eth1: e1000_watchdog_task: NIC Link is Up 1000 Mbps Full Duplex
May 30 13:28:56 myserver kernel: [143202.444280] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
May 30 13:39:27 myserver kernel: [143832.614246] e1000: eth1: e1000_watchdog_task: NIC Link is Up 1000 Mbps Full Duplex
May 30 13:39:33 myserver kernel: [143839.183024] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
May 30 14:05:38 myserver -- MARK --
# From here on it simply has --MARK-- symbols, all the way to June 1 23:00:00 (present time roughly)

```

Come to think of it, I think my server has been running ok since about the time those error messages stopped.

EDIT: Also weird, at some point it changed to eth0. In fact, scrolling back through /var/log/messages there is no longer any reference to eth1... :confused:
Looking at the timeline, I posted my original post on May 29th.  Today, Jun the 1st (well, it's 12:21 pm so technically it's june the 2nd), and may 31st I don't think I had any network problems.

---

### Post by dfreer on 2007-06-02
*bump* this was posted late last night, not that many people were online to see it.

---

### Post by dfreer on 2007-06-11
Ok, I think I have found the solution, although since the problem is intermittent it is hard to test if this solves the problem. 
[http://www.ibm.com/developerworks/forums/dw_thread.jsp?message=13764179&cat=5&thread=96697&treeDisplayType=threadmode1&forum=375#13764179](http://www.ibm.com/developerworks/forums/dw_thread.jsp?message=13764179&cat=5&thread=96697&treeDisplayType=threadmode1&forum=375#13764179)
[http://lists.us.dell.com/pipermail/linux-poweredge/2005-November/023540.html](http://lists.us.dell.com/pipermail/linux-poweredge/2005-November/023540.html)

Both of these recommend running the following command on the network card in question:
```
sudo ethtool -K eth1 tso off
```
Obviously replace the eth1 with the network card you are having the error with.
I only ran this command with eth1, I may need to do it with both cards.

Anyways, I'll post back in a couple of weeks to see if this has permently solved my problem. Whew! Hoepfully it does!!

---

