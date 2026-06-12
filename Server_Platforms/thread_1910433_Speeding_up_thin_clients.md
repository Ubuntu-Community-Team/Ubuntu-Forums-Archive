---
title: "Speeding up thin clients"
date: 2012-01-17
forum: Server Platforms
---

### Post by Happy Days on 2012-01-17
Good Day,

I am a teacher who has set up an edubuntu server running up to 8 thin clients.  I have only managed to do this in the past few months, but have wanted to do it for a long time.  

My hardware, according to the latest LTSP guide is more than sufficient for everything to work smoothly, however when everyone is running even local apps, it gets slow.  I am really hoping that somebody with more experience and knowledge than me can help me tweak the system to get the best performances.  My students are frustrated and so am I.

Here are the current specs:

Server:
Edubuntu Server 11.10
Memory 3.3 Gb
Processor  Intel Xeon CPU 3.2 GHZ x 4
Graphics VESA: MACH 64 GM
Disk 72.7 Gb SATA

Network:  
3com superspeed II dual stack Hub
Cable Cat 5E
BT Business Broadband at 24mb

Thin Clients:
Compaq DX6100
Memory 1 Gb
no HDD
onboard graphics

I am hoping there are some easy changes to make with the LDM to make things run smoothly.  I know that multimedia stuff will run slower, but the way it is now, it is like watching paint dry.

PLEASE HELP!

---

### Post by Wayne_V on 2012-01-17
running local apps requires more RAM in the clients - I suspect 1G is probably not cutting it.   I would start by monitoring swap usage on both the clients and the server -- I suspect it will be high, which will make everything painfully slow.

some analysis commands:

# swapon -s
# free
# vmsat 5 5  (take 5 samples, 5 seconds apart)
# iostat 5 5 (take 5 samples, 5 seconds apart)
# top
# iftop

---

### Post by Happy Days on 2012-01-17
Wayne V

Thanks!

Here are the results.  Thin clients were browsing google images at the time.

Server:
swapon -s
Filename				Type		Size	Used	Priority
/dev/sda5                               partition	523260	27328	-1


vmstat 5 5
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 1  0  27312 332660 164092 1032028    0    0     5    15   16   11  3  1 97  0
 1  0  27312 332064 164092 1032040    0    0     0   149 3849 2272 14  2 84  0
 1  0  27312 338844 164200 1032640    0    0     1   558 4669 2503 27  3 70  0
 3  0  27312 332396 164240 1032720    0    0     0   271 4428 2937 19  3 77  1
 2  0  27308 332792 164252 1033232    0    0     0   558 5212 3408 28  4 68  0



avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           2.69    0.05    0.54    0.22    0.00   96.49

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sda               2.86        20.48        53.38    8984959   23417968

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          83.31   10.69    4.45    0.00    0.00    1.55

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sda              11.80         8.80       143.20         44        716

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          32.02   12.66    4.90    1.20    0.00   49.22

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sda              22.40       184.00       771.20        920       3856

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          62.85    0.00    7.50    1.75    0.00   27.90

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sda              83.60       307.20      1273.60       1536       6368



top - 11:18:14 up 5 days,  1:54,  6 users,  load average: 0.26, 0.43, 0.38
Tasks: 504 total,   1 running, 503 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.0%us,  1.7%sy,  0.0%ni, 88.8%id,  0.5%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   3486904k total,  3269556k used,   217348k free,   157296k buffers
Swap:   523260k total,    27228k used,   496032k free,  1044456k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
12229 root      20   0  148m 128m 6596 S   16  3.8  22:43.55 Xorg               
 2278 callum    20   0  496m 119m  32m S   13  3.5   6:39.58 firefox            
31385 server    20   0  230m  76m  21m S    6  2.2   8:02.60 plugin-containe    
 2901 hamza     20   0  471m 111m  32m S    5  3.3   2:33.30 firefox            
 4928 server    20   0 83952  15m  11m S    3  0.5   0:04.31 gnome-terminal     
 1977 callum    20   0  285m  50m  25m S    2  1.5   0:04.57 unity-2d-launch    
 1934 callum    20   0  6224 2640  892 S    2  0.1   0:27.54 dbus-daemon        
 1978 callum    20   0 93056  24m  18m S    1  0.7   0:05.14 unity-2d-panel     
 6025 server    20   0  3060 1476  936 R    1  0.0   0:01.15 top                
 1969 callum    20   0 48072  13m  10m S    1  0.4   0:01.78 metacity           
 1985 callum    20   0 31360 2476 1996 S    1  0.1   0:00.22 dconf-service      
 1997 callum    20   0 51352 9352 6884 S    1  0.3   0:02.66 bamfdaemon         
 1954 callum    20   0  152m  17m  12m S    0  0.5   0:02.09 gnome-settings-    
 2073 callum    20   0 85544  17m  10m S    0  0.5   0:02.74 unity-panel-ser    
 2084 callum    20   0 88524  17m  14m S    0  0.5   0:04.16 ica

---

### Post by a2j on 2012-01-17
3com hub bottleneck?

---

### Post by Happy Days on 2012-01-17
A2J

What is and what causes a bottleneck?

I R very Noob.

---

### Post by philtrim on 2012-01-17
Make sure to double chaeck your network card speed and duplex settings, making sure they match on the switch ports and the thin clients.

---

### Post by Happy Days on 2012-01-17
Hi philtrim

Ii will take me a while to find out what duplex settings are and check all that, so I'll get back to you.  The 3com hub has three settings MDI-X MDI and MDII    Any idea which one it should be set too.  It is currently on MDI-X and the 100mbs light is on.

---

### Post by HugoSerrano on 2012-01-17
Hello!
It's really a HUB? or it's a Switch?

If it's a Hub, you got to change it to a switch!

Regards!

---

### Post by Happy Days on 2012-01-17
Its a Hub.  Does it make a difference to speed?

---

### Post by Wayne_V on 2012-01-17
It can make a huge difference in speed - due in large part to collision avoidance.

[http://www.networkclue.com/hardware/network/switches-vs-hubs.aspx](http://www.networkclue.com/hardware/network/switches-vs-hubs.aspx)

switches aren't that expensive any more so it would be a great investment.

---

### Post by HugoSerrano on 2012-01-17
I would say HUGE and not huge. :-P

You got a lot of collision, and ports speed it's probably 10Mbps.

---

### Post by a2j on 2012-01-17
> **Happy Days said:**
> Its a Hub.  Does it make a difference to speed?

yeah. convert your network to 1Gb/s, come back and let us know. ;)

---

### Post by Happy Days on 2012-01-17
Just ordered the switch.  Should be here tomorrow.  Will let you know what happens.  Thanks to all that have helped so far.

---

### Post by nsnidanko on 2012-01-19
I assume that clients connect via your broadband connection. I would check if you have sufficient upload speed on your Internet connection and monitor its utilization when your clients experience slowness. 24 is download, upload speed usually is a small fraction of that.

---

### Post by Happy Days on 2012-01-20
Ok, so I put in the switch.  Silly me bought a 10/100 instead of 1gb.  So, all that changed with this switch was that logging in was quicker.  Didn't see much else differ.  Will change it for a 1gb switch which will hopefully be here on Monday.  Tested my speeds.  Average DL is about 10mbps and UL is 1mbps.  

Do the thin clients get their graphics memory from themselves or do they get it from the server?  Anything involving graphics slows down heavily, so maybe tweaking something in the lts.conf will help?

I am also trying to install squid so that I can cache the pages the kids use.  Haven't spent much time on it, but if someone has a squid conf file that they use for school I would appreciate it.

Thanks to everyone out there helping This is a good learning experience.

---

### Post by Wayne_V on 2012-01-20
have you checked memory/swap usage on the clients (not just the server)?  Anything you can do to minimize swap usage would help as the swap must be done back to the server.  Or, if you have some old, small disks laying around you could add those the the clients just for swap.

---

### Post by Happy Days on 2012-01-20
Wayne, Should I run swapon -s on the clients and post results?  
Does the server look ok from my earlier results post?
Even of nothing else is running, two thin clients can't run Tuxmath!

PS.
They wouldn't take the switch back so I am stuck with 10/100 mbps and an upset Head Teacher.

---

### Post by Wayne_V on 2012-01-20
I think I would start with running "vmstat 5" (report every 5 seconds) on the server with all the clients off.   Then bring each one online and see what happens.   Then start tuxmath one at a time while still monitoring vmstat on the server.   Would help if you could also keep "vmstat 5" running in a terminal window on each client during this too.

Is tuxmatch very graphics intensive?   What type of graphics cards are in the clients?

---

### Post by Happy Days on 2012-01-30
Wayne_V  

Thanks for the effort you are putting in.  Last week was hectic so didn't try to fix too much.  Here are the results of the VMSTATS:



ONLY SERVER

procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----

0  0      0 2857652  53516 314536    0    0     0    28  103  174  0  0 99  1


1 client booted and logged in:
SERVER
0  0      0 2401460  60368 544664    0    0  1615    36 1023 1036  9  1 85  4
0  0      0 2395596  61404 547000    0    0   672   145  771  870  6  1 90  2
0  0      0 2402320  61412 547256    0    0    51     8  526  705  6  1 94  0
0  0      0 2406528  61420 547256    0    0     0    10  379  548  8  1 91  0

CLIENT 1
0  0      0 2134552  95604 764492    0    0     0     0  408  493  1  0 99  0
0  0      0 2134676  95612 764496    0    0     0     6  209  230  1  0 99  0


2 clients booted and logged in:
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
SERVER
0  0      0 1998596  97740 766680    0    0     0     4  219  345  2  0 98  0
0  0      0 1998596  97860 766680    0    0     0    69  185  284  1  0 98  1

CLIENT 2
0  0      0 1956408  98232 766760    0    0     0    91  194  261  0  0 98  1
0  0      0 1956408  98240 766760    0    0     0    11  178  237  1  0 99  0


3 clients booted and logged in:
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
SERVER
1  0      0 1829044 100336 770348    0    0     0    62  391  579  1  0 99  0
1  0      0 1828804 100344 770364    0    0     3     9  505  579 11  1 88  0
1  0      0 1793236 100528 770400    0    0     5   134  931  936 30  2 66  2

CLIENT 3
0  0      0 1800024 100552 770400    0    0     0     6  374  504  8  0 92  0
0  0      0 1800188 100560 770400    0    0     0     6  148  246  1  0 98  0
0  0      0 1800164 100568 770400    0    0     0    50  252  338  1  0 99  0


4 clients booted and logged in:
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
SERVER
0  0      0 1604756 103176 773912    0    0     0    84  215  299  1  0 99  0
1  0      0 1605376 103288 773912    0    0     0    79  602  750 11  1 86  1
0  0      0 1605004 103292 773912    0    0     0    17  287  479  1  0 98  0

CLIENT 4
0  0      0 1589968 102736 773576    0    0     5    46  466  514 12  1 87  0
0  0      0 1589952 102740 773576    0    0     0     8  170  287  0  0 99  0
0  0      0 1612544 102740 773576    0    0     0    18  207  294  1  0 99  0

RESULTS WITH BENEATH A STEEL SKY running on 1 client

SERVER
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 1  0      0 1546140 108380 829692    0    0    26     0 1314 2390  1  0 99  0
 0  0      0 1546172 108388 829820    0    0    26     5 1532 2390  2  0 98  0

CLIENT 1
0  0      0 1548860 108476 830236    0    0    26     6 1669 2436  1  0 99  0
0  0      0 1548744 108480 830236    0    0     0     6 1950 2365  1  0 98  0
0  0      0 1548776 108484 830236    0    0     0    26 1356 2412  1  0 99  0

RESULTS WITH BENEATH A STEEL SKY running on 2 clients

SERVER
0  0      0 1514316 109956 834100    0    0     0    12 2346 3954  4  1 95  0
0  0      0 1514068 109964 834152    0    0    10    10 2480 3854  3  1 97  0
0  0      0 1513936 109972 834216    0    0    13    10 5491 4005  7  1 91  0

CLIENT 2
0  0      0 1528936 109556 833196    0    0    39    12 4303 3674  3  1 96  0
0  0      0 1528664 109564 833196    0    0     0    13 4035 3653  3  1 96  0
0  0      0 1528540 109572 833392    0    0    39    10 5352 3941  4  1 95  0

RESULTS WITH BENEATH A STEEL SKY running on 3 clients

SERVER
0  0      0 1495084 110716 835108    0    0     0    22 4770 5336  6  1 92  0
0  0      0 1498500 110716 835304    0    0    38    19 4482 5384  6  1 93  0
0  0      0 1498624 110720 835308    0    0     0    43 3137 5581  4  1 95  0

CLIENT 3
1  0      0 1497880 110760 835320    0    0     0    14 5541 5480  6  2 92  0
0  0      0 1497252 110764 835320    0    0     0    22 5830 5221  8  2 90  0



The thin client graphics cards:
Intel®  82915G Express Chipset  onboard obviously.

What am I looking for on these stat tables?

---

### Post by Happy Days on 2012-01-30
Here are my network card info results:

*-network:0
       description: Ethernet interface
       product: 82541GI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:04:03.0
       logical name: eth1
       version: 05
       serial: 00:0e:0c:6a:15:1e
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full firmware=N/A ip=192.168.0.254 latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:defa0000-defbffff ioport:ec00(size=64)
  *-network:1
       description: Ethernet interface
       product: IC Plus IP100A Integrated 10/100 Ethernet MAC + PHY
       vendor: Sundance Technology Inc / IC Plus Corp
       physical id: 4
       bus info: pci@0000:04:04.0
       logical name: eth2
       version: 31
       serial: 00:27:19:f0:82:e3
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sundance driverversion=1.2 duplex=full ip=192.168.1.86 latency=64 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100Mbit/s
       resources: irq:21 ioport:e480(size=128) memory:deffec00-deffedff memory:defe0000-defeffff

See anything wrong??

---

### Post by Wayne_V on 2012-01-30
reformatted output below - makes it a little easier to read.   I was expecting to see high swap usage but no, everything looks fine.   

Does the 82915G card use the i810 driver (do 'lsmod | grep i810' and/or 'dmesg | grep i810')?   If so, is the performance problem only with graphics?   I built a system for my mother several years ago that only had i810 graphics and the performance was miserable - games were impossible and videos were barely watchable.  Maybe that is the issue?   Try running glxgears and see what kind of results you get (it's not a great graphics baseline tool but should give you a rough idea - especially if you have a "working" system you can compare to.

I would also check "ifconfig -a" quick and see if there are any packet errors/drops/overruns/etc on the NIC.

```
ONLY	SERVER

	procs		-----------memory----------	---swap--	-----io----	-system--	----cpu----
	r	b	swpd	free	buff	cache	si	so	bi	bo	in	cs	us	sy	id	wa
	0	0	0	2857652	53516	314536	0	0	0	28	103	174	0	0	99	1


1	client	booted	and	logged	in:
SERVER
	procs		-----------memory----------	---swap--	-----io----	-system--	----cpu----
	r	b	swpd	free	buff	cache	si	so	bi	bo	in	cs	us	sy	id	wa
	0	0	0	2401460	60368	544664	0	0	1615	36	1023	1036	9	1	85	4
	0	0	0	2395596	61404	547000	0	0	672	145	771	870	6	1	90	2
	0	0	0	2402320	61412	547256	0	0	51	8	526	705	6	1	94	0
	0	0	0	2406528	61420	547256	0	0	0	10	379	548	8	1	91	0

CLIENT	1
	0	0	0	2134552	95604	764492	0	0	0	0	408	493	1	0	99	0
	0	0	0	2134676	95612	764496	0	0	0	6	209	230	1	0	99	0


2	clients	booted	and	logged	in:
	procs		-----------memory----------	---swap--	-----io----	-system--	----cpu----
	r	b	swpd	free	buff	cache	si	so	bi	bo	in	cs	us	sy	id	wa
SERVER
	0	0	0	1998596	97740	766680	0	0	0	4	219	345	2	0	98	0
	0	0	0	1998596	97860	766680	0	0	0	69	185	284	1	0	98	1

CLIENT	2
	0	0	0	1956408	98232	766760	0	0	0	91	194	261	0	0	98	1
	0	0	0	1956408	98240	766760	0	0	0	11	178	237	1	0	99	0


3	clients	booted	and	logged	in:
	procs		-----------memory----------	---swap--	-----io----	-system--	----cpu----
	r	b	swpd	free	buff	cache	si	so	bi	bo	in	cs	us	sy	id	wa
SERVER
	1	0	0	1829044	100336	770348	0	0	0	62	391	579	1	0	99	0
	1	0	0	1828804	100344	770364	0	0	3	9	505	579	11	1	88	0
	1	0	0	1793236	100528	770400	0	0	5	134	931	936	30	2	66	2

CLIENT	3
	0	0	0	1800024	100552	770400	0	0	0	6	374	504	8	0	92	0
	0	0	0	1800188	100560	770400	0	0	0	6	148	246	1	0	98	0
	0	0	0	1800164	100568	770400	0	0	0	50	252	338	1	0	99	0


4	clients	booted	and	logged	in:
	procs		-----------memory----------	---swap--	-----io----	-system--	----cpu----
	r	b	swpd	free	buff	cache	si	so	bi	bo	in	cs	us	sy	id	wa
SERVER
	0	0	0	1604756	103176	773912	0	0	0	84	215	299	1	0	99	0
	1	0	0	1605376	103288	773912	0	0	0	79	602	750	11	1	86	1
	0	0	0	1605004	103292	773912	0	0	0	17	287	479	1	0	98	0

CLIENT	4
	0	0	0	1589968	102736	773576	0	0	5	46	466	514	12	1	87	0
	0	0	0	1589952	102740	773576	0	0	0	8	170	287	0	0	99	0
	0	0	0	1612544	102740	773576	0	0	0	18	207	294	1	0	99	0

RESULTS	WITH	BENEATH	A	STEEL	SKY	running	on	1	client

SERVER
	procs		-----------memory----------	---swap--	-----io----	-system--	----cpu----
	r	b	swpd	free	buff	cache	si	so	bi	bo	in	cs	us	sy	id	wa
	1	0	0	1546140	108380	829692	0	0	26	0	1314	2390	1	0	99	0
	0	0	0	1546172	108388	829820	0	0	26	5	1532	2390	2	0	98	0

CLIENT	1
	0	0	0	1548860	108476	830236	0	0	26	6	1669	2436	1	0	99	0
	0	0	0	1548744	108480	830236	0	0	0	6	1950	2365	1	0	98	0
	0	0	0	1548776	108484	830236	0	0	0	26	1356	2412	1	0	99	0

RESULTS	WITH	BENEATH	A	STEEL	SKY	running	on	2	clients

SERVER
	0	0	0	1514316	109956	834100	0	0	0	12	2346	3954	4	1	95	0
	0	0	0	1514068	109964	834152	0	0	10	10	2480	3854	3	1	97	0
	0	0	0	1513936	109972	834216	0	0	13	10	5491	4005	7	1	91	0

CLIENT	2
	0	0	0	1528936	109556	833196	0	0	39	12	4303	3674	3	1	96	0
	0	0	0	1528664	109564	833196	0	0	0	13	4035	3653	3	1	96	0
	0	0	0	1528540	109572	833392	0	0	39	10	5352	3941	4	1	95	0

RESULTS	WITH	BENEATH	A	STEEL	SKY	running	on	3	clients

SERVER
	r	b	swpd	free	buff	cache	si	so	bi	bo	in	cs	us	sy	id	wa
	0	0	0	1495084	110716	835108	0	0	0	22	4770	5336	6	1	92	0
	0	0	0	1498500	110716	835304	0	0	38	19	4482	5384	6	1	93	0
	0	0	0	1498624	110720	835308	0	0	0	43	3137	5581	4	1	95	0

CLIENT	3
	1	0	0	1497880	110760	835320	0	0	0	14	5541	5480	6	2	92	0
	0	0	0	1497252	110764	835320	0	0	0	22	5830	5221	8	2	90	0
```

---

### Post by HugoSerrano on 2012-01-30
Do you got any laptop you can boot via PXE? That way you can check if it's a graphical problem, or not, assuming that your laptop won't have that problem.

Also, the Bandwidth test that you did, was to the internet? As 10Mbps/1Mbps it's really low on a 10/100 LAN, but it's ok on a Internet connection.

Best Regards!

---

### Post by Happy Days on 2012-01-30
Wayne, will do the checks tomorrow and repost - thanks again.

Hugo, also will check a laptop boot tomorrow.  Yes, the Bandwidth test was internet.

---

### Post by Happy Days on 2012-01-31
Morning Guys.

Laptop had exactly the same issues as desktop thin clients.  Why would it make any difference?  They both should have semi-decent onboard graphics.  

Ran glxgears with some interesting results.  
Running on 1 client: 32.7 fps
Running on 2 client  16 fps
Running on 3 client  10 fps

You can imagine if five clients were running the small graphic vid.

Is the RAM on clients and server being shared out and begins to slow everything down.  When I wanted to load via PXE on the 3rd thin client, I had to sotp glxgears on the 2 others before it would boot.  I clearly have some seriuos problems here.

---

### Post by Wayne_V on 2012-01-31
are you running the apps on the client or the server?   I think local apps would be better - check out these links:

[https://wiki.ubuntu.com/ltsp-localapps](https://wiki.ubuntu.com/ltsp-localapps)


[https://wiki.ubuntu.com/LTSPLocalAppSetup](https://wiki.ubuntu.com/LTSPLocalAppSetup)

---

### Post by TheFu on 2012-02-01
Hi Happy Days,

The first thing you need to do is to start monitoring your server and at least 2 of the clients. Without real data, we are just guessing what the issues are.  With real performance data, you will **know** what the issue are.

Monitoring doesn't have to be hard.  There's a simple little tool, SysUsage, that builds performance graphs over time and stores them in HTML pages that you can view with or without a web server.
SysUsage setup is 5 minutes the first time.
Get it here: [http://sysusage.darold.net/](http://sysusage.darold.net/)
 tar zxvf SysUsage-Sar-5.*.tar.gz;  cd SysU*;   sudo apt-get install sysstat rrdtool librrds-perl ;  perl Makefile.PL;  make ;  sudo make install ;  sudo crontab -e

Add these lines:
*/1 * * * * /usr/local/sysusage/bin/sysusage > /dev/null 2>&1
*/5 * * * * /usr/local/sysusage/bin/sysusagegraph > /dev/null 2>&1

Let it run for a week.  Do the same on 2 client machines, if you can. 

Performance bottle necks come down to 4 areas.
* disk
* network
* CPU
* RAM

Slow HDDs will kill performance too, especially if you are memory constrained and swapping happens.
You are already trying to address the network. GigE will make that go away, but **everything** on your network needs to be GigE. Switch, server network adapters and all client adapters.  The client adapters will help, but even if only the server and switch are GigE that will make a HUGE difference.

CPU probably isn't the issue, but without data, you'll never **know**. 

RAM can be used up as more and more clients connect. That will lead to swapping and swapping will kill performance. Adding RAM - if you need it - is pretty easy.

So, your first step needs to be data gathering and learning what the data tells you about the performance.

Facts and data must come first.

---

### Post by Happy Days on 2012-02-01
Thanks Thefu.  To all - thank you.  I have ventured on, toward fat clients.  I have managed to get the build done and thin clients loading.  Just trying to sort out internet share through to the network.  Should I be going this route?

---

### Post by Wayne_V on 2012-02-01
It sounds like fat clients are what you want - anything more than the simplest app is going to be too much for a thin client.   TheFu's recommendation of SysUsage is not a bad idea either ...

---

### Post by TheFu on 2012-02-01
You still need to add performance monitoring on your server.  Having multiple months of data will come in handy at some point if this is a "production server".

---

