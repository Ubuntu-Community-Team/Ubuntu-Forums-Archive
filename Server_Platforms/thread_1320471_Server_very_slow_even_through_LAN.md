---
title: "Server very slow even through LAN"
date: 2009-11-09
forum: Server Platforms
---

### Post by McCoy on 2009-11-09
I have a small home server with Ubuntu Server 8.04.3, located at [http://liliput.mine.nu](http://liliput.mine.nu) . It's working, but the connection is very, very slow (less than 5kb/s on average), even if I access through my local network.

First I thought it was a problem with Apache2, but I did an ApacheBench and the results were quite good, so now I'm blaming it to some network problem.

When I ping my server through the local network with a big packet size, like 1024 bytes, most of the packets time out. With 32 bytes most of them arrive OK but some still time out.

I also tried to wget some big external files to the server from the internet through SSH, like a ubuntu iso, and I get full download speed for my connection (10 mbits), so it seems the internet connection is fine, at least downstream...

My network topology is as follows:
```

Internet - [Router] - [Acces Point] - 3 computers through WiFi
              |
              |- Ubuntu Server through Ethernet cable

```
My router is a Zyxel Prestige 660HW-61, and my access point is a Linksys WRT54g with DD-WRT v24. I have 10mbit downstream and 1mbit upstream internet connection, working good from the WiFi-connected computers. The server and all the computers are in the same subnetworks.

The server is a Pentium III at 650mhz with 256MB RAM and 13GB hard disk. The network card is a Realtek RTL-8139/8139C/8139C+ (don't know which one of these exactly, and I don't want to open the case just for that :P).

Thanks for any help! :)

---

### Post by noway2 on 2009-11-09
If your problem is with Apache only, which is the impression I got from your post, then the problem is likely in the Apache configuration files.  

I recommend that you do a search on this topic as it has undoubtedly been covered on multiple occasions.  I recall previous posts on this topic listed the configuration parameters that got them in trouble.

---

### Post by Thirtysixway on 2009-11-09
Are there any error log entries for apache that could point to the issue?

---

### Post by McCoy on 2009-11-09
I don't think there's a problem with Apache2, as I said, that was my initial thought, but I ruled it out by performing some hard tests with ab (ApacheBench), which gave satisfactory results. Moreover, I didn't modify anything from Apache2 configuration, I have the default original.

Before that, I checked the error.log and I only had the typical errors of favicon.ico not found and the like, nothing special.

I really think it's some sort of network problem, seems packages are timing out a lot (tested with a simple ping with big packet size) for some reason. Images usually don't even finish downloading from the server, they don't load at all or stop in the middle. But I can't nail it down!

---

### Post by Thirtysixway on 2009-11-09
Is the CPU at full load?  Try using top or uptime to see your servers load.  Maybe there's a stray script hogging your processor or ram

---

### Post by McCoy on 2009-11-09
The CPU load is less than 1%, so it seems it's not that. You can also check general stats here [http://liliput.mine.nu/servidor/](http://liliput.mine.nu/servidor/) (if you are patient and lucky enough so they will load)

---

### Post by Thirtysixway on 2009-11-09
Hm you are right it loads very slowly.

---

### Post by McCoy on 2009-11-09
Yeah, that's what I mean, and the most strange thing is that it's that slow even accessing through my local network, which should be blazing fast. That's why I'm almost sure it's some sort of network problem, but I don't know how to diagnose it!

---

### Post by cariboo on 2009-11-10
Try iptraf to check bandwidth on your local network install iperef on the server and on a desktop. On the server run it from the prompt:

```
iperf -s
```

starts the sever, then on a desktop open a terminal and type:

```
iperf -c <server_name>
```

You should get a result that looks something like this:

```
iperf -c willy
------------------------------------------------------------
Client connecting to willy, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.103 port 34434 connected with 192.168.1.250 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec    113 MBytes  94.3 Mbits/sec
```

---

### Post by McCoy on 2009-11-10
Thanks, here are my iperf results.

On the client:
```

iperf -c 192.168.20.50 -P 1 -i 1 -m -p 5001 -l 8K -f K -t 10 -L 5001
------------------------------------------------------------
Client connecting to 192.168.20.50, TCP port 5001
TCP window size: 8.00 KByte (default)
------------------------------------------------------------
[  3] local 192.168.20.35 port 1658 connected with 192.168.20.50 port 5001
[  3]  0.0- 1.0 sec    160 KBytes    160 KBytes/sec
[  3]  1.0- 2.0 sec    296 KBytes    296 KBytes/sec
[  3]  2.0- 3.0 sec  64.0 KBytes  64.0 KBytes/sec
[  3]  3.0- 4.0 sec  16.0 KBytes  16.0 KBytes/sec
[  3]  4.0- 5.0 sec    168 KBytes    168 KBytes/sec
[  3]  5.0- 6.0 sec    152 KBytes    152 KBytes/sec
[  3]  6.0- 7.0 sec  56.0 KBytes  56.0 KBytes/sec
[  3]  7.0- 8.0 sec  64.0 KBytes  64.0 KBytes/sec
[  3]  8.0- 9.0 sec  80.0 KBytes  80.0 KBytes/sec
[  3]  9.0-10.0 sec  56.0 KBytes  56.0 KBytes/sec
[  3]  0.0-10.2 sec  1120 KBytes    110 KBytes/sec

```

As you see, the throughtput is very irregular. Ranging from 300kb/s to 16kb/s in just 10 seconds. Very unstable!

From the server I get:
```

iperf -s -m
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  5] local 192.168.20.50 port 5001 connected with 192.168.20.35 port 1658
[  5]  0.0-10.3 sec  1.09 MBytes    889 Kbits/sec
[  5] MSS size 1452 bytes (MTU 1500 bytes, ethernet)

```
So 1mbit on average for the 10 seconds. It should be at least 30mbits (My wifi connects at around 36mbits due to distance).

So definitely there's a network problem. But, how can I know what is causing it?

---

### Post by Thirtysixway on 2009-11-10
Did it just start happening or has it always been this slow?  If it just started happening, I'd rule out it being an issue with the ethernet card or other physical hardware.

If you try maybe booting from a liveCD and installing lighttpd or apache, does that go any faster?  I know reading from CD is slow but if it goes faster than your current install you'll know it's most likely a software issue.

---

### Post by McCoy on 2009-11-10
It's a complex story, that one :P

I made the server around 3 years ago, it was sporting Ubuntu Server 6.06 and it worked flawlessly: very fast in LAN and maxing out my upload capacity when accessed through the Internet. I subsequently updated it to 6.10, 7.04 and 7.10, which was the last upgrade I performed on the server.

Then I went abroad for a year, and my father turned it off because "it made noises and was breaking the internet". At that time I didn't know what the problem was, but I was away so I couldn't check it.

I came back a week ago and decided to get it back into shape, so I turned it on again. Indeed it was making noise: the hard drive was thrashing all the time, and meanwhile the internet access was totally blocked for my whole network. If you turned it off, the internet was back. 

I decided to connect a screen to it because I couldn't even access through SSH, and it turns out it was a problem with evms and 7.10, as mentioned here: [https://bugs.launchpad.net/ubuntu/+source/evms/+bug/115616](https://bugs.launchpad.net/ubuntu/+source/evms/+bug/115616). I removed evms and it was working again! BUT, it was very slow. I updgraded to 8.04.3 to see if that would fix it, but as you can see it's still the same.

The thing is, if I wget a big external file to the server when I'm logged in through SSH, the speed is very good, 10mbits/s which is my internet download speed. And there are no communication errors reported for the Ethernet card. So it seems the hardware is OK, or at least I think so.

I might give a quick try to lighttpd just to rule out the web server once and for all, even if ApacheBench gave out good results for Apache2 performance in the computer.

---

### Post by McCoy on 2009-11-10
Maybe some network experts can assist with my problem, posted in the Server forum:

[http://ubuntuforums.org/showthread.php?t=1320471](http://ubuntuforums.org/showthread.php?t=1320471)

Thanks! :)

---

### Post by cariboo on 2009-11-10
Please don't double post on the same subject, I have merged your two threads.

---

### Post by McCoy on 2009-11-10
Sorry, just wanted to see if somebody with high network expertise could assist, that maybe doesn't check the server forum. Feel free to delete this and the previous post instead of merging, as it doesn't add anything useful to the thread, it's just a link to itself now. Wont happen again! :)

---

### Post by McCoy on 2009-11-11
Still experiencing this problem. Tried httpd and it's equally slow. Also tried to copy some files through samba and even though I could browse the directories, I could't copy files, the windows explorer would lock when trying to do so, I suspect because it waits for an answer... forever.

It's definitely an upload/upstream problem. I logged in through FTP from the server to an external server, and tried to upload some files. It was totally impossible, extremely slow. Then I downloaded some files via the same FTP session and it was fast, maxing out my internet connection.

I'm quite sure it's some network problem. Maybe I'll try to change the network card, just to start ruling out hardware issues...

---

