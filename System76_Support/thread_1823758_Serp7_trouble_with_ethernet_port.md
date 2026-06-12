---
title: "Serp7 trouble with ethernet port"
date: 2011-08-12
forum: System76 Support
---

### Post by kotoro on 2011-08-12
Wireless works just fine, but in places without wireless, (my lab at school), I am forced to use ethernet. The serp7 ethernet port does not appear to be working at all. The device can't seem to differentiate whether the plug is in or out and cannot achieve a useful connection over the line.

I have set my system up as Ubuntu / Windows 7 dual boot, I'm going to test it in windows and see if I still have an issue or if it is driver related. (I suspect it to be driver related as my device is still quite new and I don't expect it to be defective or damaged.)

When posting, please include...

    your System76 model number (the System76 Driver will tell you what it is).
---its a serval pro 7
    the version of Ubuntu are you using.
---Natty Narwhal
    the symptoms you are seeing (and instructions for replicating them if necessary).
---Auto Eth0 is impotent. Repeatedly attempts to connect with no useful outcome.
    the logs.tar file which can be created by the System76 driver (only if your problem is freeze related).
---Problem is not freeze related
    if you are attaching logs, the time indicated on your computer's clock when the problem occurred (which will help us identify the appropriate section in your logs).
---I could attempt to grab logs, but I'm not sure where to get them. I'm not a complete newbie at linux but I don't often deal with hardware drivers or OS internals.

---

### Post by kotoro on 2011-08-12
port works perfectly fine in Windows 7 64 bit. Restarting and testing in linux again just to be sure.

And nope, no dice. Something is amiss with the system76 Ethernet drivers in ubuntu

---

### Post by Furball588 on 2011-08-13
I'd probably just be more interested in the results of an ifconfig right now.

---

### Post by isantop on 2011-08-18
Sorry about the slow response here. Out of the box, the ethernet will have issues working, and can cause system instability. Go ahead and establish a wireless ethernet connection, then open the System76 Driver application. Open the "Install Drivers" tab and then click on Install. Once it's finished, reboot your computer and the problem should be resolved.

---

### Post by aranaea on 2011-08-22
I'm having similar problems though I don't dual boot so I don't know if the hardware works under other OSes.  I do see this in the dmesg log:

> eth0: Link is up at ANed: 100 Mbps, Full-Duplex, MDI.

but Network Manager can't seem to enable it and it never gets an IP4 address from dhcp.  Here are the results of ifconfig:

> eth0      Link encap:Ethernet  HWaddr 00:90:f5:b5:9c:19  
          inet6 addr: fe80::290:f5ff:feb5:9c19/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2154 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:245495 (245.4 KB)  TX bytes:3151 (3.1 KB)
          Interrupt:49 

Another clue to this problem was that if I bypass Network Manager and manually assign an IP addres I seem to be able to ping other hosts.  I used:

> sudo ifconfig eth0 192.168.10.54

and could ping other hosts by IP.

This is also on a serp7, currently running 10.10.

---

### Post by isantop on 2011-08-25
Make sure you have the latest System76 Driver installed, and that it has been run. There are some Ethernet issues that we fix in the driver.

---

