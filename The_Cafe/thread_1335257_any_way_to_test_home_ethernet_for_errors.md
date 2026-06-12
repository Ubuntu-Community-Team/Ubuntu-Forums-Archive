---
title: "any way to test home ethernet for errors?"
date: 2009-11-23
forum: The Cafe
---

### Post by sdowney717 on 2009-11-23
I bought a 100 foot cable off ebay,(seller is hong kong based). I cut off 20 feet and noticed there did not seem to be any twist to any cable pairs. the cables are working, i dont see any errors when running ifconfig.
I read that the twist is needed to eliminate crosstalk which i quess can give errors. this is a 100 base network with a couple of routers.

So is there a program to run to exercise the cables or would you just copy a very large file?

---

### Post by Grenage on 2009-11-23
What, no twists at all?  Are you sure it was advertised as CAT5?

Generic 4-pair cable (such as might be used in telecoms) can work at low speeds and/or over short distances, but you really don't want to use it.  Our first LAN (going back 10 years) was run off telecoms cable because I didn't know what the hell I was doing.  It worked, somehow, but the runs were only a few metres long.

---

### Post by ice60 on 2009-11-23
i'm not a network expert, but i would have thought you could see how it's working by a traceroute and looking just at the first hop to the router and also running sudo ifconfig and looking for errors in the eth0 bit. you can ping the hell out of your router too and see if there are any dropped packets and see the times for each ping, that's the easiest thing to do i think.

edit maybe wireshark too. and i added the bit about pinging above.

---

### Post by sdowney717 on 2009-11-23
[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=400075313138&ssPageName=STRK:MEWNX:IT](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=400075313138&ssPageName=STRK:MEWNX:IT)

this is the item, if you can still view it.
the cable is a cat 5e. When i cut the cable, there were no twists evident. The bulk cable i bought at HD, had twists easily seen.

---

### Post by ice60 on 2009-11-23
well it should be twisted! if you keep it you'll have to be careful the wire doesn't get close to anything that could screw it up including getting tangled with itself i think and any other wiring.

---

### Post by Grenage on 2009-11-23
That's the cheapest patch cable I've ever seen!

---

### Post by kpholmes on 2009-11-23
> **Grenage said:**
> That's the cheapest patch cable I've ever seen!

ya thats incredibly cheap. id be kinda weary about that cable. but your spending 1.40 for 100 ft, so you dont really loose anything if it turns out to be bunk. i would of spent a little more money and gone with cat6

---

### Post by sdowney717 on 2009-11-23
i copied a file and tool a screen shot
it copied with no errors
BUT, is it really running at the 100 rated speed?
any way to test the speed? The router light is on indicating 100 mbs connection

> scott1@scott1-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:cd:62:97:c2  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:cdff:fe62:97c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2097483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1014937 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3113185008 (3.1 GB)  TX bytes:75186273 (75.1 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8009 (8.0 KB)  TX bytes:8009 (8.0 KB)



---

### Post by cariboo on 2009-11-23
Use iperf to check you bandwidth. It is in the repositories. Run an instance on both computers, one as the server:

```
iperf -s
```

and one as the client:

```
iperf -c <servername>
```

I get the following results on my system:

```
iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.1.250 port 5001 connected with 192.168.1.100 port 36487
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.1 sec    113 MBytes  94.0 Mbits/sec
```

---

### Post by Grenage on 2009-11-23
> **sdowney717 said:**
> is it really running at the 100 rated speed?

At 8.5MB/s it certainly is.

---

### Post by CharlesA on 2009-11-23
Ick @ cheap cable. The twists should be easily seen if you cut into the cable.

The cable should work ok for 100mbps networks, but if you do go for Gigabit eventually, you'd be better off getting high quality CAT5e or CAT6. I use CAT5e myself and I am glad I moved from 100mbps, I get around 50 or so MBps instead of 11MBps.

---

### Post by sdowney717 on 2009-11-23
yeah i would think so. perhaps the twists are not obvious. it is supposed to be 3 twists per inch. i discovered this when i shortened it by 25 feet. 
other than the twist issue it seems to be working ok.
someday maybe i will get gigabyte ethernet. My motherboard supports it and the other pc has a gigabyte card. so it is currently just a router needed. But, my cox cable would not benefit at all from the switch, so i doubt i will switch unless the router dies.

---

### Post by alphaniner on 2009-11-23
> **sdowney717 said:**
> yeah i would think so. perhaps the twists are not obvious. it is supposed to be 3 twists per inch. i discovered this when i shortened it by 25 feet. 
other than the twist issue it seems to be working ok.
someday maybe i will get gigabyte ethernet. My motherboard supports it and the other pc has a gigabyte card. so it is currently just a router needed. But, my cox cable would not benefit at all from the switch, so i doubt i will switch unless the router dies.

Keep an eye out for deals on gigabit switches.  It can be worth it if you transfer stuff between machines enough.

---

### Post by gn2 on 2009-11-23
My network cables are standard electrical [twin and earth]("http://www.fastlec.co.uk/images/cable/6242y.jpg"), solid, untwisted and work perfectly.

Oh almost forgot, it's a homeplug network.

---

### Post by Firestem4 on 2009-11-23
Doing things like Traceroute and ping will only verify that layer-3 is working (OSI/TCP-IP layer). Which is to say, These tests will verify IP and MAC Addressing (@ layer 2) are working correctly, and obviously if you have the cables plugged in and configured correctly. The cable, like any hardware or physical device could be functioning, correctly even, though they're not up to spec.

CAT5/e cables are rated up to 100meters but at those distances they MUST be twisted to avoid cosstalk and outside electrical interference. Even if as you say, your cables are not twisted. Depending on how short of a length of cable you are using, you may not notice any adverse effects from them being untwisted. Keep the cables away from any electrical component that could cause interference, and keep the cable lenghts short.

If you're concerned about the quality of signal, you can only verify the physical media (cables) by using testing equipment like Tone Generators, and Cable Traces, however this equipment is expensive and you'd be better off buying a replacement cable.

---

### Post by Grenage on 2009-11-24
> **CharlesA said:**
> The cable should work ok for 100mbps networks, but if you do go for Gigabit eventually, you'd be better off getting high quality CAT5e or CAT6. I use CAT5e myself and I am glad I moved from 100mbps, I get around 50 or so MBps instead of 11MBps.

I don't think anyone has made CAT5 for years, it's pretty much all CAT5e these days (whether it says so or not).  I am sure 'some' still exists somewhere.

---

### Post by 3rdalbum on 2009-11-24
> **gn2 said:**
> My network cables are standard electrical [twin and earth]("http://www.fastlec.co.uk/images/cable/6242y.jpg"), solid, untwisted and work perfectly.

Oh almost forgot, it's a homeplug network.

Hahaha, yeah! Homeplug is good, but I bet I wouldn't get interference on Cat6 cable when someone in the kitchen turns on a stick mixer...

---

### Post by CharlesA on 2009-11-24
> **Grenage said:**
> I don't think anyone has made CAT5 for years, it's pretty much all CAT5e these days (whether it says so or not).  I am sure 'some' still exists somewhere.

Didn't say it wasn't CAT5e. ;-)

If I had to redo my cable runs now, I'd be going with CAT6.

[size=1]Of course my cable "runs" are running along the floor soo... :P[/size]

---

### Post by Grenage on 2009-11-24
Aye, all our new runs are CAT6, it probably won't be long till it's CAT7!

---

