---
title: "Slow raid5 using mdadm"
date: 2010-11-02
forum: Server Platforms
---

### Post by dluthcke on 2010-11-02
I have ubuntu server 10.04 on a server with 2.8ghz 1gb ddr2 with the os on a 2gb cf card attached to the IDE channel and a software raid5 with 4 x 750gb drives. On a samba share using these drives I am only getting around 5 MB/s connected via wireless N at 216mbps and my router and server both having gigabit ports.  Is a raid 5 supposed to be that slow? I was seeing speeds of anywhere from 20-50MB/s from other people and am just wondering what i am doing wrong to be so far below that.

---

### Post by BobVila on 2010-11-02
802.11N is often not as speedy in practice as it is in theory. Try an iperf test from your wireless machine to the server and see what you're getting for throughput. I doubt that the md is at fault here.

---

### Post by dluthcke on 2010-11-02
when i try the iperf i get a connection refused error. When i get home i will try to do figure that problem out as well as connect directly. In the mean time, is there any way to test remotely? I am on the 5 ghz wireless n band if that makes any difference.

---

### Post by rubylaser on 2010-11-03
I imagine you're seeing numbers from people quoted in Mbps rather than MB/s.  You need to divide their number by 8 to be working with the same units.  Wireless N theoretical max speed is 300 Mbps or 37.5 MB/s. In reality, if you see a third of that speed you've got one of the better wireless n devices currently available (so around 13 MB/s or less).

To test your array, connect your laptop to the server via a gigabit network cable or if you only have a 10/100 network use that.  With 10/100 you should be able to get between 10 and 12 MB/s, or with gigabit, something greater than that.  Although, with IDE drives sharing channels, you're not going to have a super fast array.

I'd try to get iperf working to test your wireless max speed and then use hdparm to benchmark the disk speed.  Here's an example from my 5 disk Western Digital RE4 array at home.

```
root@fileserver:~# hdparm -Tt /dev/md0

/dev/md0:
 Timing cached reads:   5580 MB in  2.00 seconds = 2792.36 MB/sec
 Timing buffered disk reads:  778 MB in  3.00 seconds = 259.12 MB/sec
```

So, mdadm can be VERY fast, but the way you're connecting to it is often the thing that slows it down.

Hope that helps.

---

### Post by BobVila on 2010-11-04
You have to disable the firewall or open some ports before iperf will work. The post above hit it spot on, though.

---

