---
title: "Found a bug, fixed it, build a deb. Now what?"
date: 2007-12-27
forum: Repositories &amp; Backports
---

### Post by aaargh486 on 2007-12-27
I found a bug in the ifconfig program. I apt-get'ed the source and fixed it.
Here is my normal output:

```

wlan0     Link encap:Ethernet  HWaddr 00:08:D3:05:23:0C  
          inet addr:172.19.3.3  Bcast:172.19.255.255  Mask:255.255.0.0
          inet6 addr: fe80::208:d3ff:fe05:230c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1003243 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1493049 errors:1 dropped:1 overruns:0 carrier:0
          collisions:144788 txqueuelen:1000 
          RX bytes:218446942 (208.3 **MB**)  TX bytes:1596531539 (1.4 **GB**)
          Interrupt:17 Base address:0x4000 

```

And here is the output with my fixed ifconfig

```

wlan0     Link encap:Ethernet  HWaddr 00:08:D3:05:23:0C  
          inet addr:172.19.3.3  Bcast:172.19.255.255  Mask:255.255.0.0
          inet6 addr: fe80::208:d3ff:fe05:230c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1003243 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1493049 errors:1 dropped:1 overruns:0 carrier:0
          collisions:144788 txqueuelen:1000 
          RX bytes:218446942 (208.3 **MiB**)  TX bytes:1596531539 (1.4 **GiB**)
          Interrupt:17 Base address:0x4000 

```

For more information about this: [http://en.wikipedia.org/wiki/Binary_prefix]("http://en.wikipedia.org/wiki/Binary_prefix")

Now, I build the debian package for my fix. But what do I do with it now? Is there anywhere where I can post this?
Where do I put my name? :) Can I get my fame for this? My name in a changelog somewhere?

Kasper

PS: Please don't steal this, if that is possible. It sounds so cool to have my name somewhere in Ubuntu.

---

### Post by ChameleonDave on 2008-01-04
That's not a bug.

---

### Post by steeleyuk on 2008-01-05
As far as I know, Binary Prefixes are only used in relation to disk and memory sizes. Network traffic generally doesn't 'mispresent' iteself like hard disks do...

---

### Post by aaargh486 on 2008-01-05
THe binary-prefix-problem is universal. If you put a 'K' in front f a unit, whether it are Kelvin or Volts or Amperes or bytes, you mean 1000 (one thousand) and not 1024 times that unit.

One kilobyte is one thousand bytes, If you put it on hard drives or on network traffic or the bandwidth of my spinal cord.

In any case, the ifconfig program is WRONG. Strange, I always thought  we accused Microsoft on not following standards. 
Not that it matters. The people that could have troubles ith the wrong prefixes, are smart enough not to make the mistake.

Enjoy this small bug, I'll just be the only one using this small program a bit more correctly.

No hard feelings,
Kasper

---

### Post by F-3582 on 2008-01-07
If you feel like discussing this with some devs, file it as a bug in [www.launchpad.net](www.launchpad.net) and see what happens.

---

### Post by UbuWu on 2008-01-08
[File a bug]("https://launchpad.net/ubuntu/+source/net-tools/+filebug") against the ubuntu net-tools package and attach the patch.

---

### Post by Martje_001 on 2008-01-10
aaargh486, I completely agree with you.

Btw. Since you're Dutch (your avatar), have you read that in the 'pc-active'?

---

### Post by aaargh486 on 2008-01-12
No, I just accidently found it on Wikipedia when I was clicking through links. Or it was in a book about SI units. I don't know anymore, it's been years. Sorry.

Kasper

---

