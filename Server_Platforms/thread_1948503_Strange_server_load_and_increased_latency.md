---
title: "Strange server load and increased latency"
date: 2012-03-28
forum: Server Platforms
---

### Post by nr1c0re on 2012-03-28
Hey all!

I'm using Ubuntu 10.04.1 LTS (yes, I know that there is .4 already, I will update soon for sure :) ) and has strange problem at ProLiant DL140 G3. It is encrypting router, i.e. ipsec,racoon and nothing else running there (snmpd,exim,sshd,nslcd not counting).

I notice sometimes like 1-10 times per day latency of traffic passing through this server is increased (normaly 1-2ms, but in that times it is something like 100ms-1s). And it lasts about 1 minute maximum. I catched this once, quickly logged in server and run top - found no processes take any % of cpu. So it's not processes. Also I noticed that console was like 0.5 second latency before it response to keyboard pushes.

When I was at console I catched this bug 2nd time this day later having "vmstat 1" running and found this info:

```
procs -----------memory----- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  0    120  25352 258492 535896    0    0     0     0  361   21  0  0 100  0
 0  0    120  25344 258492 535896    0    0     0     0  276   19  0  1 99  0
 0  0    120  25336 258492 535896    0    0     0    20  283   26  0  0 100  0
 0  0    120  25336 258492 535896    0    0     0     0  192   16  0  0 100  0
 0  0    120  25336 258492 535896    0    0     0     0  240   17  0  0 100  0
 0  0    120  25336 258492 535896    0    0     0     0  326   22  0  0 100  0
 0  0    120  25328 258492 535896    0    0     0     0  172   17  0 15 85  0
 0  0    120  25312 258492 535896    0    0     0     0  415   19  0 24 76  0
 1  0    120  25288 258492 535896    0    0     0     0  416   19  0 35 65  0
 1  0    120  25288 258492 535896    0    0     0     0  383   17  0 50 51  0
 0  0    120  25232 258492 535896    0    0     0     0  465   13  0 49 51  0
 1  0    120  25232 258492 535896    0    0     0     0  439   22  0 52 49  0
 0  0    120  25176 258492 535896    0    0     0     0  617   20  0 16 84  0
 0  0    120  25152 258492 535896    0    0     0     0  473   13  0 23 77  0
 0  0    120  25152 258492 535896    0    0     0     0  860   24  0  2 98  0
 0  0    120  25136 258492 535896    0    0     0     0  377   18  0  0 100  0
 0  0    120  25136 258492 535896    0    0     0     0  289   17  0 12 88  0
 0  0    120  25120 258492 535896    0    0     0     0  392   22  0 40 61  0
 0  0    120  19112 258492 537496    0    0  1580     0  747  186 12 22 58  8
 0  0    120  19104 258492 537480    0    0     0     0  415   13  0  0 100  0
 0  0    120  18980 258492 537480    0    0     0     0  480   80  0  1 99  0
 0  1    120  11604 258300 527404    0    0  7076     0 1218 1014 10 16 50 25
 0  0    120  44516 257972 512960    0    0   988  5380 1631  916  9 11 46 34
 0  0    120  44144 258004 513380    0    0     0   980  283   84  2  1 95  3
 0  0    120  49328 258004 512996    0    0     0     8 2139   49  1 11 89  0
 0  0    120  49368 258004 513016    0    0     0     0  279   13  0  1 99  0
 0  0    120  49368 258004 513016    0    0     0     0  132   24  0  0 100  0
 0  0    120  49368 258004 513016    0    0     0     0  168   19  0  0 100  0
 0  0    120  49368 258012 513008    0    0     0    96  198   91  0  0 100  0
 0  0    120  49360 258012 513016    0    0     0     0  339   47  0  1 99  0
 0  0    120  49360 258012 513016    0    0     0     0  283   21  0  0 100  0
 0  0    120  49360 258012 513016    0    0     0     0  143   19  0  1 99  0
 0  0    120  49360 258012 513016    0    0     0     0  402   24  0  0 100  0
 0  0    120  49360 258012 513016    0    0     0     0  402   15  0 13 87  0
 0  0    120  49344 258012 513016    0    0     0     0  419   15  0  1 99  0
 0  0    120  49344 258020 513016    0    0     0    12  402   27  0  4 96  0
 0  0    120  49328 258020 513016    0    0     0     0  523   21  0 19 81  0
 0  0    120  49304 258020 513016    0    0     0     0  440   20  0 37 63  0
 0  0    120  49304 258020 513016    0    0     0     0  447   25  0 22 78  0
 0  0    120  49296 258020 513016    0    0     0     0  372   16  0  7 93  0
 0  0    120  49280 258020 513016    0    0     0     0  434   13  0  0 100  0
 0  0    120  49280 258020 513016    0    0     0     0 1383   29  0  0 100  0
 0  0    120  49248 258020 513016    0    0     0     0 2482   32  0  0 100  0
 0  0    120  49248 258020 513016    0    0     0     0  429   18  0  4 96  0
 0  0    120  49240 258020 513016    0    0     0     0  321   24  0  7 93  0
 0  0    120  49224 258020 513016    0    0     0     0  545   18  0 36 64  0
 0  0    120  49192 258020 513016    0    0     0     0  925   17  0 14 86  0
 0  0    120  49176 258020 513016    0    0     0     0  213   24  0  0 100  0
 0  0    120  49176 258020 513016    0    0     0     0  334   13  0  0 100  0
 0  0    120  49176 258020 513016    0    0     0     0  372   15  0  1 99  0
 0  0    120  49168 258020 513016    0    0     0     0  587   28  0  3 97  0
 0  0    120  49168 258020 513016    0    0     0     0  174   18  0  0 100  0
 0  0    120  49160 258020 513016    0    0     0   304  354   19  0  0 100  0
 0  0    120  49160 258020 513016    0    0     0     0  275   22  0  0 100  0
 0  0    120  49160 258020 513016    0    0     0     0  279   15  0  0 100  0
 0  0    120  49160 258020 513016    0    0     0     0  199   15  0  0 100  0
 0  0    120  49160 258020 513016    0    0     0     0  382   23  0  0 100  0
 0  0    120  49160 258020 513016    0    0     0     4  296   21  0  0 100  0
 0  0    120  49160 258020 513016    0    0     0     0  211   13  0  0 100  0
 0  0    120  49152 258020 513016    0    0     0     0  265   24  0  0 100  0
 0  0    120  49152 258020 513016    0    0     0     0  674   21  0  0 100  0
 0  0    120  49152 258020 513016    0    0     0     0  308   15  0  0 100  0
 0  0    120  49152 258020 513016    0    0     0     0  321   26  0  0 100  0

```

So we see here some byte input and output and increased interrupts.
I checked with iftop in second terminal and saw nothing - it was same traffic pattern, no more then 10mbit/s. I tryed to generate tons of traffic (~1gbit/s) with iperf, system interrupts raised to 20k but everything was OK, no latency problems. So this is not likely network interrupt storm and etc.
Next I tryed to check byte i/o with cat /dev/urandom > /dev/null - "bi" or "bo" (raised to almost 100k) but everything was OK...

So looking at those vmstat part with cpu increasing I can't understand what is happening there.

I thought that some kind of profiler could help me to find something, but oprofile was a way to hard for me and I was not able to understand how should I use him and what counters to debug my problem.

I'm stuck.. Can someone give me any advises about troubleshooting this problem?


Thanks!

---

