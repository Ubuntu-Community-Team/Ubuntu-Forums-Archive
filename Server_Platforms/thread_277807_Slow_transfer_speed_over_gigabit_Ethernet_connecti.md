---
title: "Slow transfer speed over gigabit Ethernet connection"
date: 2006-10-15
forum: Server Platforms
---

### Post by autosuggested on 2006-10-15
Hi there,

I'm having problems with the gigabit Ethernet connection on my Ubuntu server - transfer speeds are generally under 100 Mb/s. As an example, I connect a five metre Cat5e crossover cable between my laptop and my server. Immediately I'm informed by Windows (running on my laptop) that my Local Area Connection is up and running at a speed of 1 Gbps. I log into the Samba share on my server and transfer a 757 MB file over to my laptop. How long does it take? 72 seconds, working out at a transfer rate of ~ 10.5 MB/s or 84 Mb/s. Now, taking Samba overhead into account, I'd expect that kind of speed from a 100 Mb/s connection, not a 1000 Mb/s connection! Anyway, I ssh into the server and pull out a few details about the connection.

First, an ifconfig

```
autosuggested@ubuntubox:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:38:05:01
          inet addr:192.168.0.130  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe38:501/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13410841 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17053553 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3662672625 (3.4 GiB)  TX bytes:1788777688 (1.6 GiB)
          Interrupt:233 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5306 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5306 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:345222 (337.1 KiB)  TX bytes:345222 (337.1 KiB)

```

Second, an ethtool output for eth0

```

autosuggested@ubuntubox:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 9
        Transceiver: external
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Link detected: yes

```

Lastly, the lspci -vv output about my Ethernet controller

```

0000:00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (250ns min, 5000ns max)
        Interrupt: pin A routed to IRQ 233
        Region 0: Memory at da000000 (32-bit, non-prefetchable) [size=4K]
        Region 1: I/O ports at b000 [size=8]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable+ DSel=0 DScale=0 PME-

```

Has anybody any ideas? I've deliberately used a simple example above, but I have a gigabit switch and a few different computers with gigabit NICs that I want to network up pretty soon and it's annoying me that I'm running at fast Ethernet speeds.

Thanks,
// autosuggested

---

### Post by autosuggested on 2006-10-15
Hmmm strange. I try the same transfer over NFS (to the same laptop, but this time it's running Ubuntu) and I get speeds between 150 Mb/s and 200 Mb/s, so the connection is definitely faster than fast Ethernet. I also ran iperf on the laptop and got lightning speeds between it and the server (192.168.0.130)!

```

autosuggested@ubuntulaptop:~$ iperf -c 192.168.0.130
------------------------------------------------------------
Client connecting to 192.168.0.130, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.0.132 port 37378 connected with 192.168.0.130 port 5001
[  3]  0.0-10.0 sec  1.02 GBytes    880 Mbits/sec

```

Samba speeds still stay around 75-90 Mb/s between the laptop and server, even when running Linux on both. Anyone got any clues as to where I could find the bottleneck as it doesn't seem to be the NICs?

Thanks,
// autosuggested

---

### Post by autosuggested on 2006-10-15
The bottleneck isn't the hard drive anyway.

```

autosuggested@ubuntubox:~$ sudo hdparm -Tt /dev/md4

/dev/md4:
 Timing cached reads:   3176 MB in  2.00 seconds = 1588.00 MB/sec
 Timing buffered disk reads:  236 MB in  3.01 seconds =  78.41 MB/sec

```

---

### Post by zachdenton on 2006-10-29
just to let you know... gigabit ethernet doesn't mean 1000mb/s, it means 1000mbps. mb/s is megabytes per second, mbps is megabits per second. 1 bit is about a tenth of a byte, so 10mbps would only mean 1mb/s.

---

### Post by unless on 2006-10-30
> **zachdenton said:**
> just to let you know... gigabit ethernet doesn't mean 1000mb/s, it means 1000mbps. mb/s is megabytes per second, mbps is megabits per second. 1 bit is about a tenth of a byte, so 10mbps would only mean 1mb/s.

Actually, the difference between bit and byte, in terms of abbreviations, is whether it's lowercase or uppercase. b=bit, B=byte. 

Slash and 'p' both mean the same thing in this context: 'per'. The choice of one over the other varies from application to application, and source to source, although 'p' appears to be preferred by most. autosuggested used the abbreviations properly: 

> working out at a transfer rate of ~ 10.5 MB/s or 84 Mb/s

There are tons of sources to confirm this. To name a few:
[http://en.wikipedia.org/wiki/Byte](http://en.wikipedia.org/wiki/Byte)
[http://www.romulus2.com/articles/guides/misc/bitsbytes.shtml](http://www.romulus2.com/articles/guides/misc/bitsbytes.shtml)
[http://www.myorderdesk.com/Abbreviations.asp?Provider_ID=15509](http://www.myorderdesk.com/Abbreviations.asp?Provider_ID=15509)
[http://www.spawar.navy.mil/sti/publications/pubs/td/1064/td1064appb.html](http://www.spawar.navy.mil/sti/publications/pubs/td/1064/td1064appb.html)

Now, back to the topic:

autosuggested, my guess is that maybe everything is working as best as it can. A guy in my local Linux user's group explained a few weeks ago that for frames up to about 500 bytes, the advantage of Gigabit ethernet over Fast ethernet is very weak: Frames smaller than 500 bytes are completed (while for Fast ethernet and 10M ethernet, it's 64 bytes). So if you're using a protocol that uses relatively small frames, there's going to be a lot of fluff transferred over your Gbit connection. 

I don't know how SMB frame sizes compare to NFS, but this may likely be the source of the large difference in transfer rates that you've observed.

Please let me know if my explanation isn't clear; upon re-reading it, I'm having doubts.

---

### Post by JLTB on 2006-11-01
Hmm ... I'm having a similar issue as well, a touch different though.

My 2 severs are connected via crossover cable and seem to constantly misnegotiate the gigabit link, hooking up at 100Mbps.  I don't think it's the crossover cable (I tested it in my lab and it was able to sustain faster speeds).

Some people have told me that using a switch instead of a crossover will solve my problems ... but I don't want to invest in the hardware if it's unecessary.  I will only have 2 servers hooked into the thing after all.

Regarding NFS versus SMB, I'm not a protocol guru, but I seem to remember that SMB has a bit more overhead than NFS.  Also, NFS is a tuned kernel daemon.  Isn't the SMB server user-land?  This might cause some performance loss (but it should still be able to sustain faster transfer speeds).

Maybe there are some throttling options in the SMB conf getting in the way?  It's been a while since I set up SMB.

---

### Post by dannyboy79 on 2006-11-02
> **unless said:**
> Actually, the difference between bit and byte, in terms of abbreviations, is whether it's lowercase or uppercase. b=bit, B=byte. 

Slash and 'p' both mean the same thing in this context: 'per'. The choice of one over the other varies from application to application, and source to source, although 'p' appears to be preferred by most. autosuggested used the abbreviations properly: 



There are tons of sources to confirm this. To name a few:
[http://en.wikipedia.org/wiki/Byte](http://en.wikipedia.org/wiki/Byte)
[http://www.romulus2.com/articles/guides/misc/bitsbytes.shtml](http://www.romulus2.com/articles/guides/misc/bitsbytes.shtml)
[http://www.myorderdesk.com/Abbreviations.asp?Provider_ID=15509](http://www.myorderdesk.com/Abbreviations.asp?Provider_ID=15509)
[http://www.spawar.navy.mil/sti/publications/pubs/td/1064/td1064appb.html](http://www.spawar.navy.mil/sti/publications/pubs/td/1064/td1064appb.html)

Now, back to the topic:

autosuggested, my guess is that maybe everything is working as best as it can. A guy in my local Linux user's group explained a few weeks ago that for frames up to about 500 bytes, the advantage of Gigabit ethernet over Fast ethernet is very weak: Frames smaller than 500 bytes are completed (while for Fast ethernet and 10M ethernet, it's 64 bytes). So if you're using a protocol that uses relatively small frames, there's going to be a lot of fluff transferred over your Gbit connection. 

I don't know how SMB frame sizes compare to NFS, but this may likely be the source of the large difference in transfer rates that you've observed.

Please let me know if my explanation isn't clear; upon re-reading it, I'm having doubts.

well you have quoted enough sites about how the conversion works but you fail to understand it yourself. What you have in your computers are Gigabit Ethernet Adapters, they supposedly transfer data at 1 gigabit per second. When you convert that to what files are measured in, (megabytes, in this case your video file I am assuming since it was around 750) that would make your ethernet adapter be able to transfer, AT IT'S BEST, 128 megabytes per second. You stated that you had a 7XX megabyte file transfer in 70 some seconds, well you even told us that that equalled around 80 some megebytes per second. To me there appears to be nothing wrong. It transfered as fast as it could. You have to keep in mind overhead, the cable may have imperfections, hell the adapters may have flaws. So everything sounds ok to me! also, if you have firewalls and what not, that would slow the packets down I would think, I am no expect but this sounds logical?

Actually, if you don't believe me, than read this test done by Intel, [http://www.intel.com/network/connectivity/resources/doc_library/documents/pdf/gig_eth_chip_review.pdf](http://www.intel.com/network/connectivity/resources/doc_library/documents/pdf/gig_eth_chip_review.pdf)

---

### Post by Child of Wonder on 2006-11-03
I have the same trouble with my server.  I'm running a D-Link 1Gbps NIC and my network is run through a D-Link Gb 24 port switch.

Speeds over Samba are typically about 20 Megabytes per second vs. 9 Megabytes per second when I use the onboard 100Mbps NIC.

Still a nice speed increase but I had hoped for more.  My NF4 motherboard with onboard Gb can do 45 Megabytes per second when connected to my other NF4 motherboard.

---

### Post by dannyboy79 on 2006-11-03
> **Child of Wonder said:**
> I have the same trouble with my server.  I'm running a D-Link 1Gbps NIC and my network is run through a D-Link Gb 24 port switch.

Speeds over Samba are typically about 20 Megabytes per second vs. 9 Megabytes per second when I use the onboard 100Mbps NIC.

Still a nice speed increase but I had hoped for more.  My NF4 motherboard with onboard Gb can do 45 Megabytes per second when connected to my other NF4 motherboard.

if you ase using a cross over cable and hooking each NF4 box to one another than you DO have a problem, if nothing else is running and there are no other packets on the line, 20 mb/s is way to slow. According to Intels test, 85 or right around there is the highest gigabit ethernet can achieve so you're at about 1/4 of it's potential.

---

### Post by autosuggested on 2006-11-09
> **dannyboy79 said:**
> well you have quoted enough sites about how the conversion works but you fail to understand it yourself. What you have in your computers are Gigabit Ethernet Adapters, they supposedly transfer data at 1 gigabit per second. When you convert that to what files are measured in, (megabytes, in this case your video file I am assuming since it was around 750) that would make your ethernet adapter be able to transfer, AT IT'S BEST, 128 megabytes per second. You stated that you had a 7XX megabyte file transfer in 70 some seconds, well you even told us that that equalled around 80 some megebytes per second. To me there appears to be nothing wrong. It transfered as fast as it could. You have to keep in mind overhead, the cable may have imperfections, hell the adapters may have flaws. So everything sounds ok to me! also, if you have firewalls and what not, that would slow the packets down I would think, I am no expect but this sounds logical?

Actually, if you don't believe me, than read this test done by Intel, [http://www.intel.com/network/connectivity/resources/doc_library/documents/pdf/gig_eth_chip_review.pdf](http://www.intel.com/network/connectivity/resources/doc_library/documents/pdf/gig_eth_chip_review.pdf)

Errr... some quick maths: a 700 MB (MegaByte) file in 70 seconds equates to 10 MegaBytes per second (MB/s or MBps). 10 MegaBytes per second is 10*8 = 80 Megabits per second (Mb/s or Mbps).

Gigabit Ethernet (1 Gbps, 1 Gb/s) = 1024 Megabits per second (1024 Mbps, 1024 Mb/s) = 128 MegaBytes per second (128 MB/s)

But I'm getting off topic

> **unless said:**
> 
autosuggested, my guess is that maybe everything is working as best as it can. A guy in my local Linux user's group explained a few weeks ago that for frames up to about 500 bytes, the advantage of Gigabit ethernet over Fast ethernet is very weak: Frames smaller than 500 bytes are completed (while for Fast ethernet and 10M ethernet, it's 64 bytes). So if you're using a protocol that uses relatively small frames, there's going to be a lot of fluff transferred over your Gbit connection.

I don't know how SMB frame sizes compare to NFS, but this may likely be the source of the large difference in transfer rates that you've observed.

Please let me know if my explanation isn't clear; upon re-reading it, I'm having doubts.


Thanks for the input, unless. I think I might post to the Samba and NFS mailing lists to see what they have to say about it as I haven't a notion what size NFS and SMB frames are.

Thanks,
// autosuggested

---

### Post by TSMJ on 2006-11-09
Disable IPv6. It should help if not solve the problem completely.
[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)

You could also try this afterwards:
[http://doc.gwos.org/index.php/Faster_Network_File_Transfers](http://doc.gwos.org/index.php/Faster_Network_File_Transfers)

TJ

---

### Post by zasf on 2006-12-10
Very interesting thread. I have the very same problem but with lower hardware. My server (old box built for testing purposes) has a 100 Mbit/s NIC, the client has a 1000 Mbit/s NIC (or 1Gigabit/s) and in the middle there is a Dlink DSL-G604T wich should support up to 100 Mbit/s connections.

Well, if I transfer via samba, I get 1246 KByte/s = 9968 Kbit/s = almost 10 Mbit/s

There is a long way between them: 50 meters cable wich goes from the basement to the top of the house, could that be the problem? How do i troubleshoot if there is some data loss?

Thanks,

---

### Post by blueCommand on 2006-12-10
> **autosuggested said:**
> 
Gigabit Ethernet (1 Gbps, 1 Gb/s) = 1024 Megabits per second (1024 Mbps, 1024 Mb/s) = 128 MegaBytes per second (128 MB/s)


Not to be picky but..

1Gbps = 1000Mbps
1GB   = 1000MB
1GiB  = 1024MiB

Which would make 1Gbit -> 125MiB/s which is about correct

---

### Post by PanzerMKZ on 2006-12-11
Maybe I am missing the point here.  80meg per second is darn good.  I am running 100base and I am very happy with my 9meg per second.  On my local network I have crap switch I can only get about 5.5meg per second.  I am just now getting into gbit gear and would love to get 80meg per second.


Panzer

---

### Post by technodigifreak on 2006-12-11
A couple of items for consideration.  

SMB does have more overhead.  NFS has much less overhead.  SMB is less tolerant of possibly flaky hardware.  

There are two things I would suggest.  
1.  Create an md5 of that 757mb file, upload it to your server from the client. Then download it again to a different directory.  Then check the md5.  If it doesn't match you either have dropped packets (which shouldn't be an issue on a crossover link) or you have faulty hardware.  This could be a faulty NIC, RAM, or even a bad sector on an HDD.  Don't laugh, I've seen stuff like this before.

2.  The other would be to connect another machine (assuming you have one) and check the speed of the connection with the new machine to the client, and then to the server.  If there is a wide variation, you may have just found the one with the issue and further troubleshooting will be easier.  


Also if you wouldn't mind posting your network settings and route's for both machines, that may help.  This could be a simple routing issue.

I hope this helped.  Let us know how it progesses!

---

### Post by thornomad on 2006-12-13
Neat thread everyone; I am trying to piece together a Ubuntu File Server for my home network and wanted info like this ... I am still confused over the gigabit, gigabyte, megabit, megabyte thing but what is important is know which is faster: SMB or NFS (or AFP).  Sounds like NFS would be the way to go with a Mac/Ubuntu network. 

Everyone is quoting different network transfer speeds but are these speeds measured with a stopwatch or is there a linux CLI command that can test the speed or transfer speed of a file easily?

Ta

---

### Post by Rizado on 2006-12-30
You could measure real network speed (No drives at all) by running a few netcat commands.

First you need netcat on both client and server. ```
sudo apt-get install netcat
```
Next you need to run a few commands.

1st computer. (The Server)
```
nc -v -v -l -n -p 5096 >/dev/null
```
This will listen on port 5096.

2nd computer. (The Client)
```
time yes|nc -v -v -n 192.168.1.1 5096 >/dev/null
```
Make sure you change the ip to your server ip.

Go find a calculator and enter what you get at rcvd on the server. Multiply by 8 and divide by the time you see on your client.
Also can the drive manage a higher speed than 80MB/s? If not you will never achive higher speeds than 80!

---

### Post by Supersaiyan.IV on 2007-02-16
It Seems NOBODY (a few exceptions) understands the difference between Mbit and Mbps (Mb/s) over here.. and here I thought linux users had a higher IQ level than blowdows users..

eg.

512kbit connection has a max transfer of (512 / 8 = 64 Kb/s).
Thus 512kbit is 64kbps.

thus, 
8bit = 1 byte 
8Mbit = 1 MegaByte
8Gbit = 1 GigaByte

The ratio is 8. You do the rest of the maths.

Sorry for going off topic.. but it just ticks me off when people think they know, while displaying no knowledge at all.

---

### Post by wshawn on 2007-02-26
I believe this is my first post in the Ubunut Forums, but I am far from a newb and administer 4 different operating system families for my clients.

I understand the frustration some people have when reading forums or other technical data.

Simple things like the correct designation of unit sizes can cause a lot of assumptions and misinformation, but usually are a distraction.

I'll resist the temptation to make a jerk out of myself and tell everyone who chose to argue correct unit measurement designations (instead of helping the original poster with his issue) a few things.  Trust me, I more than understand.  Twenty five years of playing with these toys -- trust me i REALLY understand.

Guys, try to keep it on topic.

I also have this same chipset.  I run samba shares for the xp boxes and use rsync to move massive amounts of information around ( think half a terabyte at a shot).

In any case I am currently getting 27 Mbs (that's aprroximately 3 Megs) on a gigabit network running rsync from a fedora 6 file server to a ubunutu 6.1
 amd 64 machine with high end SATA2 drives a 2 gigs of matched gaming RAM.

Everything else on the network is shutdown (cept for the 24 port gigabit switch, the file server. and the ubuntu box).

I have read and tested the following ideas:[LIST]
[*]BIOS is the latest version (sheesh need a new board this one is a year old :rolleyes:)
[*]IPv6 has nothing to do with rsync speeds, (especially using a ssh tunnel to an IP address -- I guess I could setup IP6 to test that out :lolflag:)
[*]Network indicates full Gb connection at the end of each wire (CAT 5e / 6)
[*]Cards in each system have full duplex and speed set to 1Gb
[*]WIres were snatched and new ones made and tested, old ones were fine too
[*]Network is less than 50 meters in length; far below the max for the standard
[*]10 / 100 is actually FASTER than 1000Gb on this network
[*]Wireless is actually FASTER TOO on the same network
[*]Fedora 6 on this same machine two weeks ago did not have this issue
[*]Currently moving 132 gigs of data via the network and in hour 14.  When I put the data there with FC6 it took under two hours[/LIST]I am not a troll.  I switched my laptop and main system to Ubuntu a couple weeks ago, because I spent to much time writing articles on how to get FC6 setup and usuable, and not enough actually using it.  I was able to rip corporate (and commercial) DVD's an hour after DBAN finished and with Ubuntu installed.

That's more like it!

My relevant settings:

sudo lspci -vv
> 
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7185
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (250ns min, 5000ns max)
        Interrupt: pin A routed to IRQ 217
        Region 0: Memory at fe029000 (32-bit, non-prefetchable) [size=4K]
        Region 1: I/O ports at f000 [size=8]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable+ DSel=0 DScale=0 PME-
sudo ethtool eth0
> 
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: external
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Link detected: yes
dmesg:
> 
NET: Registered protocol family 16 ; af_netlink
NET: Registered protocol family 2   ; ipv4
NET: Registered protocol family 1   ; unix
NET: Registered protocol family 8   ; atm
NET: Registered protocol family 20 ; atm
NET: Registered protocol family 17 ; af_packet
NET: Registered protocol family 10 ; ipv6
NET: Registered protocol family 31 ;  bluetooth 

device eth0 left promiscuous mode
bridge-eth0: disabled promiscuous mode
eth0: Promiscuous mode enabled.
device eth0 entered promiscuous mode
/dev/vmnet: port on hub 0 successfully opened
/dev/vmmon[20847]: host clock rate change request 83 -> 19
device eth0 left promiscuous mode
audit(1172512887.107:19): dev=eth0 prom=0 old_prom=256 auid=4294967295
bridge-eth0: disabled promiscuous mode
/dev/vmmon[20836]: host clock rate change request 19 -> 0
vmmon: Had to deallocate locked 173122 pages from vm driver d44f2000
vmmon: Had to deallocate AWE 3275 pages from vm driver d44f2000
bridge-eth0: down
bridge-eth0: detached
iftop uses obsolete (PF_INET,SOCK_PACKET)
I see this in and out of promiscuous mode multiple times during a boot up.
I also have vmware running some virtual machines at times...


Once  I get the data transfered I will remove ipv6 from the /etc/modprobe.d/aliases just for grins to see what happens...


I'll keep digging for more info an dlook forward to people that have a fully working CK804 config to throw in some ideas.

---

### Post by slowcoach on 2007-08-22
This problem still persists in Gutsy, Gigabit LAN slow, appears to be actually running at Half Duplex as there are slight pauses in the transfers as if it's waiting for the acknowledgement, tried forcing Full Duplex etc. but no difference.
No problem when running Debian.

---

### Post by al108 on 2007-08-31
It seems to me that some NICs affected more than others Realtek is the most offending one. As everybody noticed it mostly affects samba. Also look at these posts:

[http://ubuntuforums.org/showthread.php?t=424063](http://ubuntuforums.org/showthread.php?t=424063)
[http://ubuntuforums.org/showthread.php?t=143982](http://ubuntuforums.org/showthread.php?t=143982)
and there are many more with similar problems.
[URL="https://bugs.launchpad.net/ubuntu/+source/samba/+bug/84782"]
There's also bug filed against samba[/URL], but it doesn't look like it's been very active. Or maybe the bug needs to be filed against RTL driver...


I have NF4 mobo too and whatever it has (don't remember now) was also giving me lots of grief.

On the other hand, I think speeds ~200Mbps (Megabit per second - to avoid the confusion on this thread) is normal for two Gigabit cards without further tweaking - like increasing MTUs over 1500 or something.

---

### Post by 1800Zeta on 2007-09-03
> **al108 said:**
> On the other hand, I think speeds ~200Mbps (Megabit per second - to avoid the confusion on this thread) is normal for two Gigabit cards without further tweaking - like increasing MTUs over 1500 or something.

You are correct, nobody on here has mentioned "Jumbo Frames", i.e. setting the MTU as 9000 (usually).  The switch, network hardware and drivers have to support sending information via Jumbo frames.  Without the jumbo frames being enabled you hit the maximum of approx 200Mbps.

I am looking into Jumbo Frames on the Cisco kit we use, but something cisco mention puts me off enabling it but thats not for here

---

### Post by al108 on 2007-09-03
I've tried jumbo frames a couple of years ago. I ran into a problem where computers on the same network have to have same settings, and if I remember I had problem with Internet too so having two NICs probably a must with jumboframes

---

### Post by MrGando on 2007-09-06
Hi guys, I am planning on installing ubuntu for a home server, but I will need Gbit Lan ... is it really working bad for samba transfers ???


I read trough the whole post, but at first a user reports 80 Mbytes / sec , which is really good for Gbit lan.

Any input ?

---

### Post by CyberCod on 2007-09-09
> **Rizado said:**
> You could measure real network speed (No drives at all) by running a few netcat commands.

First you need netcat on both client and server. ```
sudo apt-get install netcat
```
Next you need to run a few commands.

1st computer. (The Server)
```
nc -v -v -l -n -p 5096 >/dev/null
```
This will listen on port 5096.

2nd computer. (The Client)
```
time yes|nc -v -v -n 192.168.1.1 5096 >/dev/null
```
Make sure you change the ip to your server ip.

Go find a calculator and enter what you get at rcvd on the server. Multiply by 8 and divide by the time you see on your client.
Also can the drive manage a higher speed than 80MB/s? If not you will never achive higher speeds than 80!


Is this supposed to finish by itself?  How long does it take?
I ended up hitting Ctrl+C to stop it


I just did this and got some numbers that don't make any sense.

for rcvd I got 4217960
and for the time i got 42.106 seconds

4217960 * 8 = 33743680

33743680 / 42.106 = 801398.375528428

now I'm guessing thats bits?
so divide by 1024 to get Mbits... right?

782.615601102 Mbits / second

divide by 8 to get MBytes

97.826950138 MBytes / second

right?

yet, my NFS transfer is going so slow I could walk to the next state and back before it is done.

Go figure.


Is there any easier way to see transfer speed on this stuff? this is really annoying.

If you're going to post a little trick like this, you should explain it a little better.

---

### Post by viktor.ilijasic on 2007-09-16
Well, here is a mini howto...

[COLOR="Red"][SIZE="6"]**How to properly measure your bandwidth/throughput/network speed**[/SIZE][/COLOR]

You need two machines on a network. For instance 192.168.0.1 and 192.168.0.2.

If you are running Ubuntu/Debian, open one terminal, maximize it and type:

```
$ sudo apt-get install **netperf**
```

on both machines. That should install and start netperf daemon. If it didn't start you can type:

```
$ sudo /etc/init.d/netperf start
```

If that didn't start the daemon, you're on your own. :)

Optionally open one more terminal, set it always on top (and not maximized), move it so you see it, but it doesn't block the first terminal and type

```
$ sudo apt-get install ethstatus
$ ethstatus -i **ethX**
```

where **ethX** is the interface you are trying to measure. This terminal will give you real-time speed measurements with graph.

Return to first terminal.

Then from 192.168.0.1 type

```
$ netperf -H 192.168.0.2
```

and from 192.168.0.2 type

```
$ netperf -H 192.168.0.1
```

If you need real measured mbits/s, you are going to look at the last column of the results.

Keep in mind that I haven't tested netperf on a gigabit network, but I probably will, and very soon.

This is the end of the howto. :D

If you are going to republish it anywhere, feel free, but give and include the link to original thread where you found the howto. That would be this thread, and the link would be this: [http://ubuntuforums.org/showpost.php?p=3377815&postcount=26](http://ubuntuforums.org/showpost.php?p=3377815&postcount=26)
I keep the right to republish it anywhere without the link to original thread.
:)

Why am I here? Well, I have the same problems...

Samba transfers are varying from 3-6 megaBytes/s on my network. I tried 3 switches, 3 computers, 2 versions of Ubuntu, and 2 versions of Mint. One machine is debian woody/sarge, but I didn't test samba, just throughput (that would be 192.168.55.1).

Here are netperf results from my machines:

from 192.168.55.21:
```
$ netperf -H 192.168.55.1
TCP STREAM TEST from 0.0.0.0 (0.0.0.0) port 0 AF_INET to 192.168.55.1 (192.168.55.1) port 0 AF_INET
Recv   Send    Send                          
Socket Socket  Message  Elapsed              
Size   Size    Size     Time     Throughput  
bytes  bytes   bytes    secs.    10^6bits/sec  

 87380  16384  16384    10.01      93.65
$ netperf -H 192.168.55.31
TCP STREAM TEST from 0.0.0.0 (0.0.0.0) port 0 AF_INET to 192.168.55.31 (192.168.55.31) port 0 AF_INET
Recv   Send    Send                          
Socket Socket  Message  Elapsed              
Size   Size    Size     Time     Throughput  
bytes  bytes   bytes    secs.    10^6bits/sec  

 87380  16384  16384    10.06      94.14
$ netperf -H 192.168.55.5
TCP STREAM TEST from 0.0.0.0 (0.0.0.0) port 0 AF_INET to 192.168.55.5 (192.168.55.5) port 0 AF_INET
Recv   Send    Send                          
Socket Socket  Message  Elapsed              
Size   Size    Size     Time     Throughput  
bytes  bytes   bytes    secs.    10^6bits/sec  

 87380  16384  16384    10.02      93.99  
```

from 192.168.55.31:
```
$ netperf -H 192.168.55.1
TCP STREAM TEST from 0.0.0.0 (0.0.0.0) port 0 AF_INET to 192.168.55.1 (192.168.55.1) port 0 AF_INET
Recv   Send    Send                          
Socket Socket  Message  Elapsed              
Size   Size    Size     Time     Throughput  
bytes  bytes   bytes    secs.    10^6bits/sec  

 87380  16384  16384    10.01      89.01
$ netperf -H 192.168.55.21
TCP STREAM TEST from 0.0.0.0 (0.0.0.0) port 0 AF_INET to 192.168.55.21 (192.168.55.21) port 0 AF_INET
Recv   Send    Send                          
Socket Socket  Message  Elapsed              
Size   Size    Size     Time     Throughput  
bytes  bytes   bytes    secs.    10^6bits/sec  

 87380  16384  16384    10.06      89.18   
$ netperf -H 192.168.55.5
TCP STREAM TEST from 0.0.0.0 (0.0.0.0) port 0 AF_INET to 192.168.55.5 (192.168.55.5) port 0 AF_INET
Recv   Send    Send                          
Socket Socket  Message  Elapsed              
Size   Size    Size     Time     Throughput  
bytes  bytes   bytes    secs.    10^6bits/sec  

 87380  16384  16384    10.02      89.22
```

from 192.168.55.5:
```
$ netperf -H 192.168.55.1
TCP STREAM TEST from 0.0.0.0 (0.0.0.0) port 0 AF_INET to 192.168.55.1 (192.168.55.1) port 0 AF_INET
Recv   Send    Send                          
Socket Socket  Message  Elapsed              
Size   Size    Size     Time     Throughput  
bytes  bytes   bytes    secs.    10^6bits/sec  

 87380  16384  16384    10.01      93.79   
$ netperf -H 192.168.55.21
TCP STREAM TEST from 0.0.0.0 (0.0.0.0) port 0 AF_INET to 192.168.55.21 (192.168.55.21) port 0 AF_INET
Recv   Send    Send                          
Socket Socket  Message  Elapsed              
Size   Size    Size     Time     Throughput  
bytes  bytes   bytes    secs.    10^6bits/sec  

 87380  16384  16384    10.01      93.83   
$ netperf -H 192.168.55.31
TCP STREAM TEST from 0.0.0.0 (0.0.0.0) port 0 AF_INET to 192.168.55.31 (192.168.55.31) port 0 AF_INET
Recv   Send    Send                          
Socket Socket  Message  Elapsed              
Size   Size    Size     Time     Throughput  
bytes  bytes   bytes    secs.    10^6bits/sec  

 87380  16384  16384    10.01      93.75
```

from 192.168.55.1 (it has some older version of netperf):
```
$ netperf -H 192.168.55.5
TCP STREAM TEST to 192.168.55.5
Recv   Send    Send                          
Socket Socket  Message  Elapsed              
Size   Size    Size     Time     Throughput  
bytes  bytes   bytes    secs.    10^6bits/sec  

 87380  16384  16384    10.01      93.95   
$ netperf -H 192.168.55.21
TCP STREAM TEST to 192.168.55.21
Recv   Send    Send                          
Socket Socket  Message  Elapsed              
Size   Size    Size     Time     Throughput  
bytes  bytes   bytes    secs.    10^6bits/sec  

 87380  16384  16384    10.01      93.12   
$ netperf -H 192.168.55.31
TCP STREAM TEST to 192.168.55.31
Recv   Send    Send                          
Socket Socket  Message  Elapsed              
Size   Size    Size     Time     Throughput  
bytes  bytes   bytes    secs.    10^6bits/sec  

 87380  16384  16384    10.01      93.98
```

Between any and any other of my computers there could be from 1 up to 3 switches. All machines have either 100mbit/s NICs, and one has 1gbit/s NIC. Switches are 100 mbit/s and one is 1gbit/s.

If anyone is still calculating mbits/s to mBytes/s, these results are roughly 11-12 megaBYTES/s. The optional terminal with ethstatus is clearly showing those numbers. So, the nework CAN go a LOT faster, but SAMBA is slow.

At this point it becomes almost unimportant what NIC, or what drivers we are using. The problem is either Ubuntu based (kernel or whatever) or Samba based.

I should probably test samba transfer to and from debian machine. If anyone asks me to do so, I shall gladly do it.

Hope my guide helps someone out there. :D

Viktor Ilijasic

---

### Post by viktor.ilijasic on 2007-09-21
I have made some more testing....

And I am starting to wonder if this is the right place to post these informations. Does anyone know where are the developers? Where IS the bug? WHAT is causing this? I am wiling to help pinpointing the cause of all this, if anyone out there is listening... :-|

Samba isn't the cause of all this, because SSH is suffering the same thing... If You are at all interested, read on...

I connected:

- Ubuntu samba server (booted from LiveCD and upgraded with latest samba)
```
$ uname -a
Linux ubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

$ sudo lspci -vv
...
00:06.0 Ethernet controller: D-Link System Inc DGE-528T Gigabit Ethernet Adapter (rev 10)
        Subsystem: D-Link System Inc DGE-528T Gigabit Ethernet Adapter
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (8000ns min, 16000ns max), Cache Line Size: 128 bytes
        Interrupt: pin A routed to IRQ 19
        Region 0: I/O ports at fc00 [size=256]
        Region 1: Memory at fdfff000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at 40080000 [disabled] [size=128K]
        Capabilities: [dc] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable+ DSel=0 DScale=0 PME-
...

$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:xy:zu:dy:dx:cx  
          inet addr:192.168.55.23  Bcast:192.168.55.255  Mask:255.255.255.0
          inet6 addr: abcd::efg:hij:klm:nop/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21251610 errors:0 dropped:4282 overruns:0 frame:0
          TX packets:20792212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3610217845 (3.3 GiB)  TX bytes:458561937 (437.3 MiB)
          Interrupt:19

$ sudo ethtool eth1
Settings for eth1:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes

$ smbd -V
Version 3.0.24

```

with

- Linux Mint (samba) Client
```
$ uname -a
Linux kinderei 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux

$ sudo lspci -vv
...
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
        Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10d4
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (250ns min, 5000ns max)
        Interrupt: pin A routed to IRQ 19
        Region 0: Memory at c0007000 (32-bit, non-prefetchable) [size=4K]
        Region 1: I/O ports at 30b8 [size=8]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable+ DSel=0 DScale=0 PME-
...

$ ifconfig
eth0      Link encap:Ethernet  HWaddr ab:cd:00:11:21:31  
          inet addr:192.168.55.21  Bcast:192.168.55.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27646456 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28191280 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2331639484 (2.1 GiB)  TX bytes:451962121 (431.0 MiB)
          Interrupt:19 Base address:0xc000 

$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: external
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Link detected: yes

$ smbclient -V
Version 3.0.24


```

They are connected directly and only through D-Link DGS-1008D (gigabit switch).

The best results so far over samba are 6.7-8.7 megabytes/s download (initiated from client to download data from server) and 6.5-7.8 megabytes/s upload (initiated from client to upload to server). I got that with
```
socket options = TCP_NODELAY SO_RCVBUF=32768 SO_SNDBUF=32768
``` set in /etc/samba/smb.conf
That's not bad for a 100mbit network...

**[COLOR="Red"]I wonder why I have brand new gigabit then...[/COLOR]**

SSH transfers are getting slightly worse results - about 0.5 mb slower. Havent tried FTP and NFS yet. But that is the next step...

So, here are the real capabilities of the network:

From Ubuntu server:
```
$ netperf -v 2 -H 192.168.55.21
TCP STREAM TEST from 0.0.0.0 (0.0.0.0) port 0 AF_INET to 192.168.55.21 (192.168.55.21) port 0 AF_INET
Recv   Send    Send                          
Socket Socket  Message  Elapsed              
Size   Size    Size     Time     Throughput  
bytes  bytes   bytes    secs.    10^6bits/sec  

 87380  16384  16384    10.01     562.02   

Alignment      Offset         Bytes    Bytes       Sends   Bytes    Recvs
Local  Remote  Local  Remote  Xfered   Per                 Per
Send   Recv    Send   Recv             Send (avg)          Recv (avg)
    8       8      0       0 7.036e+08  16384.00     42942   3373.96 208527

Maximum
Segment
Size (bytes)
  1448
```

From Mint client:
```
$ netperf -v 2 -H 192.168.55.23
TCP STREAM TEST from 0.0.0.0 (0.0.0.0) port 0 AF_INET to 192.168.55.23 (192.168.55.23) port 0 AF_INET
Recv   Send    Send                          
Socket Socket  Message  Elapsed              
Size   Size    Size     Time     Throughput  
bytes  bytes   bytes    secs.    10^6bits/sec  

 87380  16384  16384    10.09     645.08   

Alignment      Offset         Bytes    Bytes       Sends   Bytes    Recvs
Local  Remote  Local  Remote  Xfered   Per                 Per
Send   Recv    Send   Recv             Send (avg)          Recv (avg)
    8       8      0       0 8.137e+08  16384.27     49664   1616.17 503479

Maximum
Segment
Size (bytes)
  1448
```

ethstatus is readily displaying these (tremendous) speeds and calculates them as numbers up to 89.39 megabytes/s.

I am gonna test some more, as this is unacceptable until I make it go at least 50 MB/s as a normal thing.

Oh, yes, disks in both computers are SATA or SATA2, and one computer (server) is (Desktop) P4 2.8 GHz, with 1 GB ram, the other (client) is (Laptop) AMD Turion 64 X2 TL-56 (2x1.8) with 2 GB RAM... so no bottleneck there. They can both read and write many MB/s...

Ok, the results...

Client (Laptop):
```
$ dd if=/dev/zero of=temp bs=1M count=3096
3096+0 records in
3096+0 records out
3246391296 bytes (3.2 GB) copied, 161.586 seconds, 20.1 MB/s
$ dd if=temp of=/dev/null
6340608+0 records in
6340608+0 records out
3246391296 bytes (3.2 GB) copied, 136.239 seconds, 23.8 MB/s

```
That was on a system/swap disk, and I watched a movie at the same time. It was boring to wait this to finish. :)

Desktop:
```
$ dd if=/dev/zero of=temp bs=1M count=1024
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 15.3394 seconds, 70.0 MB/s
$ ls -al -R
[wait a minute, ctrl+c]
$ dd if=temp of=/dev/null
2097152+0 records in
2097152+0 records out
1073741824 bytes (1.1 GB) copied, 13.4359 seconds, 79.9 MB/s

```
Viktor

---

### Post by matsondawson on 2007-10-10
I have exactly the same problem with 7.10 and an RTL8169 PCI network card.  I was getting about 200kb/s transfer from a WinXP machine, unless there was also a connection back from the windows machine I was copying from via something like VNC.
Note:  All cards are showing 1Gb connections, as well as the switch.
If there was a seperate return connection it would go up to 80Mb/s.
Also if I started browsing the internet that would make the speed go up.

After much poking around I found increasing the MTU on windows to 9044 (only 1 of 2 size options I had) and setting the MTU on the RTL8169 to 4522, that the speed would run consitently at 70Mb/s.

I tried using matching MTU's of 4022, but that had the same issues.

My thoughts are that maybe there's an IRQ problem, as I've had problems like this before where say, my video card wouldn'y update unless I kept moving the mouse :)  I thought I'd try and change the IRQ for the card tonight and see if that helps.

I've seen people in other places on the net complaining about this exact same issue.

*** Hmm after reading my post I just notice I'm only getting 80Mb/s on a Gb lan... so I must double check my values.  as that sounds like 100Mb speed :)  I've screwed something up there.  I was doing it at 2am this morning so not surprising. 
*** I also noted setting the windows machine to 100mb full duplex has the same effect.


EDIT >>>>>>>>>>

OK, I've retested it, and the MTU change seems to fix it.
If I do an smbget instead of using the filemanager I get 250Mbits (even though stupid smbget was using b for byte not B). 
When using the filemanager I get 70Mbits, which is just plain strange. (interestingly if i copy 2 files at once this doubles, but doesnt get any faster for 3 or more)
I guess I don't get 750Mbit as my hdd can't keep up after 250Mbit.

EDIT >>>

Replaced the RTL8169 with a DynaLink DGE530-T, now no problems at all.
Goes to 320Mbit when copying files, still 100Mbit with file browser, but I'd say that's a File Manager issue.
My advice is, don't buy a GB card with a RealTech chipset, until the drivers get fixed.

EDIT >>

Use CIFs if you want fast file transfers in nautalis.

---

### Post by regomodo on 2007-10-17
i don't know if this has been solved but this link should explain/help the issue

[http://wiki.archlinux.org/index.php/Nfs](http://wiki.archlinux.org/index.php/Nfs)

---

### Post by viktor.ilijasic on 2007-11-27
Thanks for the NFS link but I still haven't tried that yet.

However, i solved my problems.

Take a look here:

[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

Since I'm not using windows anymore, this is great. I get average 20-25 mBytes/s transfers, but that's probably "sluggish" disk(s) in my laptop. :)

But I have no idea how to easily share files with friends who use windows...

Anyone have any idea how to enable that without setting up (slow) samba? Ok, that's a bit offtopic. :)

Viktor

---

### Post by thavinci on 2008-06-09
Anyone know where the problem lies?

I just converted from FreeBSD to ubuntu only to find out nothing worked out for me.

Same slow speeds issue here.

Using DGE-528T

---

