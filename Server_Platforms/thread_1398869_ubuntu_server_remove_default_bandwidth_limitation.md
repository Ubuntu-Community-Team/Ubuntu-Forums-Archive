---
title: "ubuntu server remove default bandwidth limitation"
date: 2010-02-05
forum: Server Platforms
---

### Post by torcescubogdan on 2010-02-05
Hello!

I have Ubuntu server 9.10 x86_64 and a 1Gb/s lan connexion, 2xSSD raid0 (software).
If I using windows and I download something from specific location I download that thing with 60-80 MB/s, but with ubuntu server my speed goes down and I have only 5-8 MB/s. I have 1Gb/s in metropolitan, in other trafic I have 2.2 MB/s, and for ubuntu my speed goes down at 300-400 KB/s.
I have same speed at downoad and upload. I mention that my small server has 3 lan connections: eth0 - Internet, eth1 - local network, wlan0 - wifi.

I have verified the network card driver, it's ok, and the 1000 Mb/s uplink is working.

Hope you can help me!

PS: Sorry for my English.

---

### Post by HighCommander540 on 2010-02-05
> **torcescubogdan said:**
> Hello!

I have Ubuntu server 9.10 x86_64 and a 1Gb/s lan connexion, 2xSSD raid0 (software).
If I using windows and I download something from specific location I download that thing with 60-80 MB/s, but with ubuntu server my speed goes down and I have only 5-8 MB/s. I have 1Gb/s in metropolitan, in other trafic I have 2.2 MB/s, and for ubuntu my speed goes down at 300-400 KB/s.
I have same speed at downoad and upload. I mention that my small server has 3 lan connections: eth0 - Internet, eth1 - local network, wlan0 - wifi.

I have verified the network card driver, it's ok, and the 1000 Mb/s uplink is working.

Hope you can help me!

PS: Sorry for my English.

You do understand that 1Gb/s is 1 gigabit per second. And 7-8 MB/s is 7-8 megabytes per second?

Over a 1Gb/s connection 7-8 MB/s is about the best you are going to get. There is no limit built into Ubuntu. The system is preforming correctly.

---

### Post by torcescubogdan on 2010-02-05
> **HighCommander540 said:**
> You do understand that 1Gb/s is 1 gigabit per second. And 7-8 MB/s is 7-8 megabytes per second?

Over a 1Gb/s connection 7-8 MB/s is about the best you are going to get. There is no limit built into Ubuntu. The system is preforming correctly.
1Gb/s = 1000Mb/s = 125MB/s
1MB = 8Mb !!!
b = bit
B = byte

Ok, my full speed bandwitch from my provider is ~125MB/s, I give you some print-screen from windows.
[http://img21.imageshack.us/img21/3747/1gb.png](http://img21.imageshack.us/img21/3747/1gb.png)
[http://img130.imageshack.us/img130/3792/22535935.png](http://img130.imageshack.us/img130/3792/22535935.png)

I spoke with my provider and he said to me that in the past he has same problem but someone do something and repair. I asking here because I think is someone who know the answare, please help!

---

### Post by HighCommander540 on 2010-02-05
> **torcescubogdan said:**
> 1Gb/s = 1000Mb/s = 125MB/s
1MB = 8Mb !!!
b = bit
B = byte

Ok, my full speed bandwitch from my provider is ~125MB/s, I give you some print-screen from windows.
[http://img21.imageshack.us/img21/3747/1gb.png](http://img21.imageshack.us/img21/3747/1gb.png)
[http://img130.imageshack.us/img130/3792/22535935.png](http://img130.imageshack.us/img130/3792/22535935.png)

I spoke with my provider and he said to me that in the past he has same problem but someone do something and repair. I asking here because I think is someone who know the answare, please help!

My bad. I read somewhere. That the max a 1gb/s connection can do is 7-8 MB/s. I didn't do the math myself. You're right it should be going at 125MB/s. Its not a Ubuntu issue though. There is no throttling. 

Also, I didn't need a explanation of bits and bytes (seeing as I proved I knew the difference). Thanks, anyway though. I have never seen an actual 125MB/s connection.

I would look at your hardware or connections or something. Especially, on the server edition. I have never seen a bandwidth limiter. I have a 100Mb/s connection and I can run at the max speed.

Questions: What type of internet do you have?
How fast is your drive write speed?

---

### Post by BkkBonanza on 2010-02-05
Where can you get 1 Gbit/s internet? I've never heard of that and it would be incredibly expensive. Probably something fishy there. You may have a gigabit connection for your LAN, and maybe a transport of 1 Gbit for internet but you won't get a full 1 Gbit internet service without paying very high rates. If someone told you otherwise they're pulling your leg. I'm assuming you're not sitting in a data center on a LAN between servers though - that is possible, but regular ISP connection? Best I've ever heard of for regular net connections is 100 Mbps and good connections are often much less than that. In the UK I read recently they're starting to roll out 50Mbps. Even if you were sitting in a data center you'd be paying hundreds $$/mo for 10-100 Mbps links.

Your 7-8MB/s is good for something like a 50 Mbps connection.

Regarding your screen images - you're confusing transport speed vs actual through put. Even on a LAN with transport of 1Gbit you won't usually reach that in actual through put unless everything is else is capable. But to get that through put on a net connection would be big bucks $$$. What you have here is a difference in the way information is reported in the status details. Do actual transfer benchmarks on Windows vs. Ubuntu and I expect you'll find little difference.

Another thing to note - if you use a dsl modem with an ethernet connection to your system then the system will report the speed as 1G even if the modem is connected to your ISP and limited to much less. This is a case where the local transport layer exceeds the actual connection limit.

---

### Post by torcescubogdan on 2010-02-05
Questions: 
What type of internet do you have?

In Romania Internet it's very fast and cheap, the providers try to offer faster and faster speed because the pupiles download a lot, especialy pirated movies, games, programs because they are expensive.
My provider have optical fibra, and using own neighborhood LAN builded on gigabit in order to forward full speed of him connexion.
He can offer:
1Gb/s up & down in metropolitan, in fact the speed is availeble with all regions from Romania, because of providers peering.
17Mb/s up & down with other countries.
For just 40 RON = 9.7 euro = 13.44$ (us) /month


How fast is your drive write speed?

I have mention that I have 2 x SSDs in RAID 0.
Here some hdd tests:
photo: [http://img21.imageshack.us/img21/8323/img2160e.jpg](http://img21.imageshack.us/img21/8323/img2160e.jpg)
write test: [http://img130.imageshack.us/img130/7239/write.png](http://img130.imageshack.us/img130/7239/write.png)
read test: [http://img237.imageshack.us/img237/4117/read.png](http://img237.imageshack.us/img237/4117/read.png)

SSD info:
Performance &#8211; enhances productivity; makes users more efficient
Innovative &#8211; 2.5" form factor; uses NAND flash memory components.
Silent &#8211; Runs silent and cool with no moving mechanical parts
Reliable &#8211; less likely to fail than a standard hard drive
Shock Resistant &#8211; No moving mechanical parts so the SSD handles rougher conditions.
Other details: [http://www.kingston.com/ssd/v-series.asp](http://www.kingston.com/ssd/v-series.asp)

YouTube - [http://www.youtube.com/results?search_query=ssd&search_type=&aq=f](http://www.youtube.com/results?search_query=ssd&search_type=&aq=f)

PS: I know that a ordinary sata hdd, can't have more that 25MB/s - 30MB/s, but here it's a diffrent story.

BkkBonaza, the download from print-screen is not from my local network, not from my provider server, it's another provider server from same city, named evolva, more exactly is it's mirror server.

---

### Post by torcescubogdan on 2010-02-05
Thank you for replaies, but I guarantee you that I have all hardware capabilities.
All of my tests show that the problem is a software limitation.

---

### Post by BkkBonanza on 2010-02-05
Are you using a router? I have a Linksys WRT54GL and it tops out at about 4-5 MB/s even though it claims to be 100 Mbps capable. I've seen Ubuntu used in gigabit router situations and have no impact on through put. If there is something in your software preventing you getting good speed then it's certainly not by default. Maybe you need to post some config details and people can see if something looks weird. I'd suggest the output of,

ifconfig eth0

for starters. Or whatever interface your'e using if not eth0. Also output of,

sudo ethtool eth0

may give some useful details. If ethtool isn't present then you'll need to apt-get install it.

For example mine gives output like,

```
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: g
	Current message level: 0x000000ff (255)
	Link detected: yes

```
Which indicates I'm capable of gigabit but negotiated 100Mbit with my router - that Linksys, which I'm replacing soon.

---

### Post by torcescubogdan on 2010-02-05
> **BkkBonaza said:**
> Are you using a router? I have a Linksys WRT54GL and it tops out at about 4-5 MB/s even though it claims to be 100 Mbps capable. I've seen Ubuntu used in gigabit router situations and have no impact on through put. If there is something in your software preventing you getting good speed then it's certainly not by default. Maybe you need to post some config details and people can see if something looks weird. I'd suggest the output of,

ifconfig eth0

for starters. Or whatever interface your'e using if not eth0. Also output of,

sudo ethtool eth0

may give some useful details. If ethtool isn't present then you'll need to apt-get install it.

For example mine gives output like,

```
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: g
	Current message level: 0x000000ff (255)
	Link detected: yes

```
Which indicates I'm capable of gigabit but negotiated 100Mbit with my router - that Linksys, which I'm replacing soon.
I alredy have verified that, my output is "Speed: 1000Mb/s", I am connected to a D-link sw, gigabit capable. The network is builded on gigabit.....
My provider uses a server (not stand-alone router) to routing the internet from optical fibra to network.

---

### Post by BkkBonanza on 2010-02-05
I'd suggest connecting to another gigabit computer and check the speed you can get. My guess is that your ISP simply doesn't provide what they say they do. But who knows... only thing I know is that Ubuntu doesn't have a "limiter" that stops you getting your hardware's speed. That would be just plain silly, wouldn't it?

Poor cabling can also affect maximum speed.

---

### Post by dragos2 on 2010-02-05
From where did you have bought Internet ? I wonder who sells 
gigabit pipes for 9$ !

Also you were guaranteed gigabit speeds in metropolitan => a maximum throughput in ideal
conditions of 128 MB/sec which never happens because of the additional overhead of the
switching equipments on the links.

You say that you should have 17-18 Mbit international => 2.12 MB/sec. Is this the same
for upload ? International uploads are usually not guaranteed as downloads and peering
is pretty expensive.

Please do a speedtest.net and please test both Romanian servers and international ones
and post the links here.

---

### Post by torcescubogdan on 2010-02-05
> **BkkBonaza said:**
> I'd suggest connecting to another gigabit computer and check the speed you can get. My guess is that your ISP simply doesn't provide what they say they do. But who knows... only thing I know is that Ubuntu doesn't have a "limiter" that stops you getting your hardware's speed. That would be just plain silly, wouldn't it?

Poor cabling can also affect maximum speed.

I alredy checked, here is my print-screen [http://img130.imageshack.us/img130/3792/22535935.png](http://img130.imageshack.us/img130/3792/22535935.png) . It's not full 120MB/s gigabit because of ftp limitation, but is better than what I have on linux.
I think is some bug, don't know...:(

The cable is ok, if wasen't the ftp download above dosen't show that speed.

---

### Post by BkkBonanza on 2010-02-05
I meant test Ubuntu on a direct connection to another computer to verify the problem is within the network stack and not somewhere else. That screen image appears to obviously be from Windows. Perhaps there is a bug but until you can test under known conditions you won't be able to figure out where it's having problems. It could be an issue with network card driver, or who knows, maybe it's not. If you connect to another computer directly and both have gigabit and Ubuntu can or cannot achieve correct speeds then that will tell you something about where the problem is.

---

### Post by torcescubogdan on 2010-02-05
> **dragos2 said:**
> From where did you have bought Internet ? I wonder who sells 
gigabit pipes for 9$ !

Also you were guaranteed gigabit speeds in metropolitan => a maximum throughput in ideal
conditions of 128 MB/sec which never happens because of the additional overhead of the
switching equipments on the links.

You say that you should have 17-18 Mbit international => 2.12 MB/sec. Is this the same
for upload ? International uploads are usually not guaranteed as downloads and peering
is pretty expensive.

Please do a speedtest.net and please test both Romanian servers and international ones
and post the links here.
The international band have same speed at download and upload.
My provider have guaranteed bandwith, he dosen't offer guaranteed band, dosen't matter for me, it's working, it's cheap and fast, it's the best offert ever seen.
I don't expect to have 128MB/s, but at least 60MB/s-80MB/s, I need this speed for my future projects.
Now I'm at work, when I get home, I will post the results, of speedtest.net.

PS:
Ufff....no solutions....any ideea?!plss.
Ty all for trying to help!

---

### Post by torcescubogdan on 2010-02-05
> **BkkBonaza said:**
> I meant test Ubuntu on a direct connection to another computer to verify the problem is within the network stack and not somewhere else. That screen image appears to obviously be from Windows. Perhaps there is a bug but until you can test under known conditions you won't be able to figure out where it's having problems. It could be an issue with network card driver, or who knows, maybe it's not. If you connect to another computer directly and both have gigabit and Ubuntu can or cannot achieve correct speeds then that will tell you something about where the problem is.

Sorry, my missunderstanding, when I geting home I will do the test, ty for ideea.

---

### Post by BkkBonanza on 2010-02-05
When you do get home to try I'd suggest using a tool like iperf to check the connections. I think it doesn't have as much overhead and may help focus in on what is causing trouble. See these two articles about measuring network performance that seem to be useful,

[http://www.enterprisenetworkingplanet.com/netos/article.php/3657236](http://www.enterprisenetworkingplanet.com/netos/article.php/3657236)
[http://www.enterprisenetworkingplanet.com/netos/article.php/3658331](http://www.enterprisenetworkingplanet.com/netos/article.php/3658331)

Also here is a thread where someone found out their cable connectors was crippling their speed to one third what it could do...

[http://lxer.com/module/forums/t/26336/](http://lxer.com/module/forums/t/26336/)

---

### Post by torcescubogdan on 2010-02-05
> **BkkBonaza said:**
> When you do get home to try I'd suggest using a tool like iperf to check the connections. I think it doesn't have as much overhead and may help focus in on what is causing trouble. See these two articles about measuring network performance that seem to be useful,

[http://www.enterprisenetworkingplanet.com/netos/article.php/3657236](http://www.enterprisenetworkingplanet.com/netos/article.php/3657236)
[http://www.enterprisenetworkingplanet.com/netos/article.php/3658331](http://www.enterprisenetworkingplanet.com/netos/article.php/3658331)

Also here is a thread where someone found out their cable connectors was crippling their speed to one third what it could do...

[http://lxer.com/module/forums/t/26336/](http://lxer.com/module/forums/t/26336/)
Done!
Results:
```
root@ns1:/tmp# iperf -c 89.33.xxx.xxx
------------------------------------------------------------
Client connecting to 89.33.xxx.xxx, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 89.33.xxx.xxx port 52675 connected with 89.33.xxx.xxx port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  1.09 GBytes    940 Mbits/sec
```

Also I do some extra tests:

Local hdd speed test, mesurated in linux:
Write:
```

root@ns1:/tmp# dd count=1k bs=1M if=/dev/zero of=/tmp/test
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 4.77045 s, 225 MB/s

```
Read:
```

root@ns1:/tmp# hdparm -Tt /dev/md1

/dev/md1:
 Timing cached reads:   3698 MB in  2.00 seconds = 1849.15 MB/sec
 Timing buffered disk reads:  666 MB in  3.01 seconds = 221.41 MB/sec

```

After that I do again download test in order to recheck band:

From linux, same thing, 5MB/s - 8MB/s.
From windows 7, with filezilla ftp client: 60MB/s and after non-SDD hdd (ordinary sata II 500GB seagate) fill cache speed goes to 30MB/s - 35MB/s. With firefox browser begin transfer from 20MB/s and grow up to 34MB/s - 35MB/s. 


So the conclusions are that the hdd is ok, network card is ok, provider offer at least 60MB/s but isn't availeble on linux from some reason, hope to find and fix that. Please correct me if I wrong!

Ty again everybody's trying to help!

---

### Post by BkkBonanza on 2010-02-05
That seems to indicate that Ubuntu can handle the speed for the LAN but is having some issue when talking to your ISP. How is that connection made? That is, how is it different to when you did the iperf test? Where is the IP 89.33.xxx.xxx located - I expect it must be another system on your LAN but that's not a typical private IP address.

---

### Post by torcescubogdan on 2010-02-05
> **BkkBonaza said:**
> That seems to indicate that Ubuntu can handle the speed for the LAN but is having some issue when talking to your ISP. How is that connection made? That is, how is it different to when you did the iperf test? Where is the IP 89.33.xxx.xxx located - I expect it must be another system on your LAN but that's not a typical private IP address.
It's public ip adress, the provider have some ip classes and he gave every client an static, routable ip, unique...Bouth pc's are in the same room in the moment of testing.
PS: The routing provider's server is on Gentoo, x86. 

How is that connection made?
Static ipv4.

Also I forgot to say that, pc with I made the test, run ubuntu live cd 9.10 x86.

---

### Post by BobVila on 2010-02-05
> **torcescubogdan said:**
> It's public ip adress, the provider have some ip classes and he gave every client an static, routable ip, unique...Bouth pc's are in the same room in the moment of testing.
PS: The routing provider's server is on Gentoo, x86. 

How is that connection made?
Static ipv4.

Also I forgot to say that, pc with I made the test, run ubuntu live cd 9.10 x86.

Comparing livecd performance against a native install isn't super-wise, but that doesn't seem capable of skewing the numbers this badly. Can you run iperf, but use UDP instead of TCP this time around?

---

### Post by BkkBonanza on 2010-02-05
When I asked how the connection is made I was looking for details about how you connect to your internet provider. eg. Your LAN port -> DSL modem -> ISP, or LAN port -> Switch -> Router -> DSL modem -> ISP. Or how?

And with your iperf test was one system just direct connected to the other or was it going thru a switch? It's hard to figure out what you're actualy doing there because you just post the bare bones info. If I don't know what you're doing then how can I even guess at what may be causing the problem.

Also you should really run the iperf test on your normal system. What you've done now just leaves more questions than answers. Maybe the LiveCD is using different drivers than the installed one, or maybe some other software installed has caused a problem that isn't present on the LiveCD.

---

### Post by torcescubogdan on 2010-02-05
> **BobVila said:**
> Comparing livecd performance against a native install isn't super-wise, but that doesn't seem capable of skewing the numbers this badly. Can you run iperf, but use UDP instead of TCP this time around?
done
```

root@ns1:~# iperf -u -c 89.33.xx.xx
------------------------------------------------------------
Client connecting to 89.33.xx.xx, UDP port 5001
Sending 1470 byte datagrams
UDP buffer size:   126 KByte (default)
------------------------------------------------------------
[  3] local 89.33.xx.xx port 40986 connected with 89.33.xx.xx port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  1.25 MBytes  1.05 Mbits/sec
[  3] Sent 893 datagrams
[  3] Server Report:
[  3]  0.0-10.0 sec  1.25 MBytes  1.05 Mbits/sec  0.015 ms    0/  893 (0%)

```

---

### Post by torcescubogdan on 2010-02-05
> **BkkBonaza said:**
> When I asked how the connection is made I was looking for details about how you connect to your internet provider. eg. Your LAN port -> DSL modem -> ISP, or LAN port -> Switch -> Router -> DSL modem -> ISP. Or how?

And with your iperf test was one system just direct connected to the other or was it going thru a switch? It's hard to figure out what you're actualy doing there because you just post the bare bones info. If I don't know what you're doing then how can I even guess at what may be causing the problem.

Also you should really run the iperf test on your normal system. What you've done now just leaves more questions than answers. Maybe the LiveCD is using different drivers than the installed one, or maybe some other software installed has caused a problem that isn't present on the LiveCD.
Auch, ok.
LAN port -> Switch -> Switch -> ISP Lan port

---

### Post by BkkBonanza on 2010-02-05
Your udp test results will be wrong because with udp you have to specify what speed you want to test at. eg. add -b 100m or -b 1000m

The default is only 1m so thats why you get very slow results there.

---

### Post by torcescubogdan on 2010-02-05
I found the problem and fix it!!!
The problem was a broken gigabit lan protection for lightning.
[http://www.3e.ro/alteimagini/13800-5409_PNET1GB.jpg](http://www.3e.ro/alteimagini/13800-5409_PNET1GB.jpg)
Now my data transfers works with 90MB/s :D

Sorry for I waisting your time, and thanks a lott for your help!

---

