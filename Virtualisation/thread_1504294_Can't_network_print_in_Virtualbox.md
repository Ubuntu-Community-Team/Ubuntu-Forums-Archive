---
title: "Can't network print in Virtualbox"
date: 2010-06-07
forum: Virtualisation
---

### Post by ssc351 on 2010-06-07
I posted this over on the virtualbox site a couple days but no takers so maybe you guys can help:

Hey guys,

This has been driving me crazy...I upgraded to Lucid 64 bit from Jaunty 64 bit and Virtualbox V2 to the latest version 3.2.2 and now I can't get my printers working...I've deleted everything to try and start over but still no luck...Here is what I have done so far

1.) Ubuntu prints fine using Hp Photosmart c7200 printer with socket//ip.address:9100
2.) I am using NAT networking in VB
3.) I can ping the host gateway in the XP Guest "10.0.2.2"
4.) I added the printer as so "http://10.0.2.2:631/printers/HP-Photosmart-c7200" the printer model reads the same as it does in ubuntu
5.) in Ubunutu under printing --> server--> I checked "publish shared printers connected to this system" also tried checking "allow printing from internet"

What gives.. i am pretty sure I have everything right.

On the XP guest, unders printers...the printer says "cannot connect to printer server, unable to connect"

Any help? I am at a loss of what to do.

---

### Post by JKyleOKC on 2010-06-09
Have you actually tried to print anyway, despite the message?

I sometimes get that message, but find that printing still works.

If this doesn't happen in your case, try switching the VBox network adapter from NAT to Bridged, and give it a static IP that's compatible with that of your host. That is, one on the same subnet (first three numbers the same). VBox's NAT server issues addresses in the 10.x.x.x range while most private LANs are set up in the 182.168.x.x range, and this may block your communication. I have all of my VMs set up as Bridged, in the 192.168.0.x range, and printing works perfectly from them...

---

### Post by ssc351 on 2010-06-09
Yes I have tried printing anyway, and windows brings up this error saying to select another printer.  I will try bridging the connection.  But I still get internet in virtualbox, you would think that the internet wouldn't work either.

---

### Post by JKyleOKC on 2010-06-09
Getting to the internet is a very different situation. The gateway router between you and the site you're going to takes care of translating network addresses as necessary, so the same-subnet rule doesn't apply there. Between two local computers, however, it does -- and the VM is for all practical purposes a separate computer from the host even though it's in the same box and using the same hardware.

What establishes the subnet is the "netmask" that you'll be asked to specify when you bridge the VM's network adapter. A netmask of 255.255.255.0 means that the first three numbers must match before the adapter will respond to any traffic; thus you'll need to know the IP address of your host system and set the address and netmask of the VM accordingly. To get the address and mask of the host, open a terminal and type "sudo ifconfig" to get something similar to this:

```
eth0      Link encap:Ethernet  HWaddr 00:a0:cc:db:f0:cf  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:ccff:fedb:f0cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1148844 errors:2 dropped:0 overruns:0 frame:0
          TX packets:918631 errors:5 dropped:0 overruns:0 carrier:5
          collisions:0 txqueuelen:1000 
          RX bytes:777523847 (741.5 MB)  TX bytes:529896614 (505.3 MB)
          Interrupt:17 Base address:0xec00
``` which is just part of the response for the machine I'm replying on. The "inet addr" and "Mask" values are what you're after; set the VM to the same first three numbers (with the fourth one different but not either 0 or 255, which have special meanings), and to all four from the mask.

---

