---
title: "Speed of my Ubuntu Server?"
date: 2012-11-25
forum: Server Platforms
---

### Post by BStrizzy on 2012-11-25
Hey guys, I am trying to find out how I can boost the speed of my ubuntu home server edition. I am currently running ubuntu 10.04 server edition on an old desk top (2007) Compaq Presario SR1810NX.

I have 1 gig of ram in it and I am curious if I get a couple extra sticks, if this will boost my speeds in relation to my streaming. 
I want to have pretty much buffer free streaming to my devices in the house when I am watching movies or playing music. Also i would like to increase the download/upload speeds when I am transfering to and from the server. 

for instance:  I am transfering from my sever to my External HDD mybook usb3.0 which is connected, and the transfer is a total of 41 gigs, the eta is said to be like 13 hrs and is downloading at just about 950 kb/sec and rising little by little and then decreasing little by little. How do I increase this? Also, according to htop, durring this transfer cpu: fluctuates from 3-10%

FYI :

Cable/dsl: Xfinity "says" I am getting 54mpbs, not sure if it is true or not
HTOP: when I run this program I have a total of 935mb and I am currently using 70

advice?

---

### Post by sandyd on 2012-11-25
**moved to server platforms**

---

### Post by BStrizzy on 2012-11-25
> **sandyd said:**
> **moved to server platforms**

Thanks, I wasn't sure where this belonged.

---

### Post by sandyd on 2012-11-25
> **BStrizzy said:**
> Hey guys, I am trying to find out how I can boost the speed of my ubuntu home server edition. I am currently running ubuntu 10.04 server edition on an old desk top (2007) Compaq Presario SR1810NX.

I have 1 gig of ram in it and I am curious if I get a couple extra sticks, if this will boost my speeds in relation to my streaming. 
I want to have pretty much buffer free streaming to my devices in the house when I am watching movies or playing music. Also i would like to increase the download/upload speeds when I am transfering to and from the server. 

for instance:  I am transfering from my sever to my External HDD mybook usb3.0 which is connected, and the transfer is a total of 41 gigs, the eta is said to be like 13 hrs and is downloading at just about 950 kb/sec and rising little by little. How do I increase this?

FYI :

Cable/dsl: Xfinity "says" I am getting 54mpbs, not sure if it is true or not
HTOP: when I run this program I have a total of 935mb and I am currently using 70

advice?
I don't think the bottleneck is at the RAM, since it says 70 mb ram used.

Anyways, I believe that the computer only has USB1/2 ports. Have you checked what USB Version your Mybook is connected to?

Also, can you install pastebinit (its hard to post text from a server...)
```

sudo apt-get install pastebinit
```
and post the output of
```

ifconfig | pastebinit
```

```

lspci | pastebinit
```

---

### Post by BStrizzy on 2012-11-25
> **sandyd said:**
> I don't think the bottleneck is at the RAM, since it says 70 mb ram used.

Anyways, I believe that the computer only has USB1/2 ports. Have you checked what USB Version your Mybook is connected to?

Also, can you install pastebinit (its hard to post text from a server...)
```

sudo apt-get install pastebinit
```and post the output of
```

ifconfig | pastebinit
``````

lspci | pastebinit
```

ok I installed and got: 

bstrizzy@nova:~$ ifconfig | pastebinit
[http://pastebin.com/rZAzewna](http://pastebin.com/rZAzewna)
bstrizzy@nova:~$ lspci | pastebin
pastebin: command not found
bstrizzy@nova:~$ lspci | pastebinit
[http://pastebin.com/Kxxeburd](http://pastebin.com/Kxxeburd)

and  i have not checked usb versions, not sure how to
ive never used this software before

---

### Post by sandyd on 2012-11-25
Ok, so you have two usb1 controllers, and one usb2 controller.

Try plugging the mybook into a different usb port, the one that the mybook is plugged in might be the USB1 one

---

### Post by BStrizzy on 2012-11-25
> **sandyd said:**
> Ok, so you have two usb1 controllers, and one usb2 controller.

Try plugging the mybook into a different usb port, the one that the mybook is plugged in might be the USB1 one

Ok, I will try that after this 23hr transfer it is now saying haha. I didn't get this far for nothing! 

Is there a way we can check through my ssh what version I am using?

---

### Post by zero2xiii on 2012-11-25
Yea easy,

lsusb:

```

_**Bus 001** Device 001: ID 1d6b:0002 Linux Foundation **2.0 root hub**_
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001** Device 003: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 002 Device 002: ID 04f3:0103 Elan Microelectronics Corp. 
Bus 003 Device 002: ID 062a:0252 Creative Labs Emerge Uni-retractable Laser Mouse
**Bus 001** Device 005: ID 058f:6254 Alcor Micro Corp. USB Hub
**Bus 001** Device 011: ID 0819:0101 eLicenser License Management and Copy Protection
**Bus 001** Device 012: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 64MB QDI U2 DISK

```

See the bolded text.

In my example, everything on bus 001 will be connected to a 2.0 usb port.

Regards

---

### Post by BStrizzy on 2012-11-25
> **zero2xiii said:**
> Yea easy,

lsusb:

```

_**Bus 001** Device 001: ID 1d6b:0002 Linux Foundation **2.0 root hub**_
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001** Device 003: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 002 Device 002: ID 04f3:0103 Elan Microelectronics Corp. 
Bus 003 Device 002: ID 062a:0252 Creative Labs Emerge Uni-retractable Laser Mouse
**Bus 001** Device 005: ID 058f:6254 Alcor Micro Corp. USB Hub
**Bus 001** Device 011: ID 0819:0101 eLicenser License Management and Copy Protection
**Bus 001** Device 012: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 64MB QDI U2 DISK

```See the bolded text.

In my example, everything on bus 001 will be connected to a 2.0 usb port.

Regards

bstrizzy@nova:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1058:1140 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
bstrizzy@nova:~$ 

is this the correct setup?

---

### Post by SeijiSensei on 2012-11-26
Since you have a USB 3.0 device, why not install a USB 3.0 adapter like [this one](http://www.neweggbusiness.com/Product/Product.aspx?Item=N82E16816115105&nm_mc=KNC-GoogleBiz&cm_mmc=KNC-GoogleBiz-_-pla-_-NA-_-NA&gclid=CPa2j8is7bMCFQqk4Aod0QIA1w)?

---

### Post by BStrizzy on 2012-11-26
> **SeijiSensei said:**
> Since you have a USB 3.0 device, why not install a USB 3.0 adapter like [this one]("http://www.neweggbusiness.com/Product/Product.aspx?Item=N82E16816115105&nm_mc=KNC-GoogleBiz&cm_mmc=KNC-GoogleBiz-_-pla-_-NA-_-NA&gclid=CPa2j8is7bMCFQqk4Aod0QIA1w")?

awsome man, I will look into that first thing spring semester. Recently got a job at my university  as a help desk tech so i will have all sorts of time to try to add an adapter

---

### Post by CharlesA on 2012-11-26
> **SeijiSensei said:**
> Since you have a USB 3.0 device, why not install a USB 3.0 adapter like [this one](http://www.neweggbusiness.com/Product/Product.aspx?Item=N82E16816115105&nm_mc=KNC-GoogleBiz&cm_mmc=KNC-GoogleBiz-_-pla-_-NA-_-NA&gclid=CPa2j8is7bMCFQqk4Aod0QIA1w)?

Huge +1. I added a PCIex1 card to my old server and it helped when doing huge data transfers.

> **BStrizzy said:**
> awsome man, I will look into that first thing spring semester. Recently got a job at my university  as a help desk tech so i will have all sorts of time to try to add an adapter

It's not that hard - shutdown the box, pop the case open, install card and boot it back up. ;)

---

### Post by BStrizzy on 2012-11-26
> **CharlesA said:**
> Huge +1. I added a PCIex1 card to my old server and it helped when doing huge data transfers.



It's not that hard - shutdown the box, pop the case open, install card and boot it back up. ;)


ahhhhhh i know man, i would really rather not try to mess this thing up and start from scratch, [SIZE=1](even tho it would be good practice)[/SIZE] [SIZE=2]and besides now that I will h[SIZE=2]ave a first [SIZE=2]decent job i can afford [SIZE=2]stuff now :)[SIZE=2] no ramen:P

by the way can you check this thread for me, I am h[SIZE=2]aving a lil bit of trouble 
[SIZE=2]http://ubuntuforums.org/showthread.php?t=2088568[/SIZE]
[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]

---

