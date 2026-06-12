---
title: "Internal gigabit network copies files to and from Ubuntu very slowly"
date: 2018-03-28
forum: Server Platforms
---

### Post by a-dougk1 on 2018-03-28
Within the last month, the Ubuntu file server I built has gradually started transferring files at an incredibly slow rate (~700 KBs). The server and its clients are all on a single gigabit wired network. The computer uses a built-in RAID 5 array using eight 4TB drives. The hard drive controller says everything is fine with the RAID array, so it doesn't appear to be hardware related. 

I'm using this server to stream video to clients using Plex. The transfer rate has become so slow that I can't even stream 720p movies without them constantly buffering. And, like I said above, just copying a new file to the server takes forever @ 700 KBs.

However, if I run a speed test for the Internet, the download speed is 91.11 Mbit/s and the upload speed is 56.14 Mbit/s. 

I'm copying files from a Windows 7 machine to the server, and the server is streaming the video to TVs running WebOS (just in case that might be part of the problem). Also, I'm only using the command line on Ubuntu - no UI is running on the machine.

Any idea what's causing the transfer rates on my internal network to run so slowly?

Note that when I first built the machine and set it up, the transfer rates were ~10 MBs. It's just gotten slower and slower over time.

---

### Post by wildmanne39 on 2018-03-28
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by volkswagner on 2018-03-29
To help narrow down the issue, you should try other protocols like ssh, scp, rsync, etc. to copy over the network.

Also try using samba copy internal to the machine to eliminate network wire.

Do you have any drives on the server that are not part of the array? You can try copy
from the array to local drive.

Also use hdparm and dd to test your array speed.

```
hdparm -tT /dev/md1

/dev/md1:
 Timing cached reads:   8416 MB in  2.00 seconds = 4210.96 MB/sec
 Timing buffered disk reads: 632 MB in  3.00 seconds = 210.45 MB/sec
```

The following creates a 470MB file. You can adjust the block size and count to your liking.
```
root@kvm:/home/eric# cd /tmp
root@kvm:/tmp# dd if=/dev/zero of=./output.img bs=8k count=56k
57344+0 records in
57344+0 records out
469762048 bytes (470 MB) copied, 0.475607 s, 988 MB/s
```

The above results are from (4) 1 TB drives in software mdadm RAID 10, Toshiba 5400RPM 2.5"

---

### Post by a-dougk1 on 2018-03-31
I've tried transferring a file from my windows machine to Ubuntu using pscp in Putty. The transfer rate was ~130KBs. 

Transferring from my windows machine to Ubuntu using scp - took about 20 minutes to transfer a 1.3 GB file (didn't tell me the transfer rate). 

Also, transferring a file tonight from Ubuntu to Windows in File Explorer, the transfer rate was ~500KBs. Slower than ever.

```
hdparm -tT /de/sda3

/dev/sda3:
 Timing cached reads:   2128 MB in 2.00 seconds = 1063.41 MB/sec
 Timing buffered disk reads: 654 MB in  3.00 seconds = 217.92 MB/sec
```

```
dd if=/dev/zero of=./output.img bs=8k count=56k
57344+0 records in
57344+0 records out
469762048 bytes (470 MB) copied, 1.12462 s, 418 MB/s
```

That's all I had time for tonight.

Does that tell you anything?

Doug

---

### Post by volkswagner on 2018-03-31
Well, to me it seems the network has an issue.

What's the output of:
```
lspci | grep Ethernet
```

Replace the following with your actual ethernet adapter
```
ethtool eth0
```

---

### Post by a-dougk1 on 2018-03-31
lspci | grep Ethernet
```
0d:00.0 Ethernet controller: Intel Corporation 82573E Gigabit Ethernet Controller (Copper) (rev 03)
0e:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
```

ethtool eth0
```
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: off (auto)
Cannot get wake-on-lan settings: Operation not permitted
	Current message level: 0x00000007 (7)
                               drv probe link
	Link detected: yes
```

I'm pretty sure the network itself doesn't have a problem. I just copied and pasted a 1 GB file from one Windows machine to another, and the transfer rate was ~7.5 MBs. I took the same file and pasted it to the Ubuntu machine, and the transfer rate was ~700KBs.

However, I won't say it isn't the network - it could be the network setup on Ubuntu. I've just run out of my "expertise" on Linux networking ;)

---

### Post by a-dougk1 on 2018-03-31
Found the problem. It was the router.

The computer is in another room with various other computers (that I haven't been running for a while). I thought there might be a problem with the router when this first began, so I replaced it - with no change. And with only one computer running on the router at this time, I left it at that. My mistake.

I took the network cable coming in to the router and plugged it directly into the computer's network plug. Suddenly, the network now copies files at ~96Mbs.

So, it looks like the problem was one old bad router, and one new bad router.

I've never had good luck with routers. They always seem to go gradually bad over time. But this one was bad from the beginning.

Live and learn... :redface:

---

### Post by volkswagner on 2018-03-31
I'm glad you found a solution.

Are you sure it's a defective router? Are you putting routers in series, ie: are you creating double NAT?

Are you actually on a gigabit network? 96Mbs seems kinda of slow if you are on gigabit, but perfectly normal
if you are on 100 Megabit network. 

On gigabit you should see ~900Mbs or ~90-110MBs (Megabytes per second) provided your CPU and disk array can handle it.

We can all have fun with little "b" and capital "B" (bits vs Bytes)
:)

---

### Post by a-dougk1 on 2018-03-31
You are right - it is ~96MBytes/second. 

Well, it is a Windows machine I'm typing this on. They've never been a stickler for capitalization before :P

---

### Post by volkswagner on 2018-04-01
That's funny!

Please mark the thread solved, using the "thread tools" menu at the top of this thread.

Cheers!

---

