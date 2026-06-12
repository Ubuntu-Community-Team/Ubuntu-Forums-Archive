---
title: "Need Help With Asrock 939NF4G-SATA2 Motherboard - Networking"
date: 2006-06-29
forum: The Cafe
---

### Post by OffHand on 2006-06-29
Hi all
I just bought a new computer.
Works fine except for the fact I cannot get my networking to work.
I have tried installing the nvidia nforce drivers but I get an error when I try to install. I'm using the standard i386/32 bits now. I do not know how to compile forcedeth (which I heard can solve this issue.

These are my system specs:

AMD Athlon 64 3500+ socket 939 with silent cooling.
Asrock 939NF4G-SATA2 with NVidia NV44 chipset
1024 MB DDR PC3200 Memory
DVD-ROM LG 16x
160 GB Maxtor Diamond Max 10 SATA
Geforce 6100 128MB
6 kanaals audio on board
10/100Mbit LAN on board
6 USB poorten (2 aan voorkant kast)
Silent 420W PSU

Thanks in advance

---

### Post by OffHand on 2006-06-29
some more info after managing to install the nforce drivers from nvidia.

eth0      
Link encap:Ethernet  HWaddr 00:13:8F:A2:E1:7D         
inet6 addr: fe80::213:8fff:fea2:e17d/64 Scope:Link         
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 RX packets:81 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:7 overruns:0 carrier:0 collisions:0 txqueuelen:1000 RX bytes:29594 (28.9 KiB) TX bytes:0 (0.0 b)
Interrupt:217 Base address:0xa000


$ lsmod | grep nvnet 

nvnet                  69924  0

I got cable internet and my isp identifies me with the mac address of my ethernetcard

---

### Post by John.Michael.Kane on 2006-06-29
I have the same 6100/410 chipset t-force board that i'm still working on. so i cant say for sure if i will have this same issue or not. dapper's kernel should have support for this chipset.
I found this hope this helps some.[Latest NVIDIA drivers](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)


sidenote:If your isp see's the mac address of the ethernetcard. I would think that your eth0 is fine. are you able to get any kind of signal. can you do a ping?

---

### Post by OffHand on 2006-06-29
[QUOTE=SD-Plissken]I have the same 6100/410 chipset t-force board that i'm still working on. so i cant say for sure if i will have this same issue or not. dapper's kernel should have support for this chipset.
I found this hope this helps some.[Latest NVIDIA drivers](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)


sidenote:If your isp see's the mac address of the ethernetcard. I would think that your eth0 is fine. are you able to get any kind of signal. can you do a ping?[/QUOTE]
The card is functioning 'cause I am using it in XP. Just need the dam thing to work in Ubuntu and then I'm a happy man again. 90% of the stuff I do with my compu I have to use the internet.

---

### Post by OffHand on 2006-06-29
I found a 'solution' on the internet. 

```

So, if you're using the stock 2.6.15-23-386, you can try replacing the forcedeth.ko file at /lib/modules/2.6.15-23-386/kernel/drivers/net/forcedeth.ko with this one: http://brianmercer.com/forcedeth.ko which is patched to version 0.54. (Change the name of the old one to keep as a backup, of course)


Tried this, and it works when I manually "modprobe forcedeth" once it has booted. Unfortunately, on booting it seems to somehow still use the old version, despite the fact it is no longer in /lib/modules/2.6.15-23-386/kernel/drivers/net/. Running "dmesg | grep forcedeth" shows it is still version 0.48.

Anyone have any ideas why it is loading a file that no longer exists?

***UPDATE***

Found the solution. After copying the file, you have to run:
sudo dpkg-reconfigure linux-image-`uname -r`
And reboot.

```

but ```
sudo dpkg-reconfigure linux-image-`uname -r`
``` says it cannot find the image or something like that.

---

### Post by OffHand on 2006-06-29
ok , decided I couldn't be arsed to get this working. Installed an old ethernetcard I had laying around. Worked without hassle. 

/happycamper

posting this from ubuntu
=D>

---

### Post by John.Michael.Kane on 2006-06-29
subsonic_shadow  i'm sorry i could not find a answer to your problem. I know my board has the same chipset, and when i finally get it running i guess i'm going to have to figure out a work around for it  even though i thought dapper had the drivers for this board.. One thing though that i did find which may not be what you want to hear is that FC5 seems to work with this chipset with out hassle how true that is i don't know. I'm glad however that you did find a solution though not the one you want.

---

### Post by gingermark on 2006-06-29
Hey there. Just to say, I am using the exact same motherboard, and my networking worked straight out of the box with Dapper.

I know that doesn't help, but just to say that it **should** have worked! :)

---

### Post by John.Michael.Kane on 2006-06-29
gingermark is that using the default kernel? i know the drivers on nvidia's homepage list this chipset as fully supported ect, and dappers kernel should have support for it from i have seen. that's why it's strange that the OP is having netcard issues.

---

### Post by OffHand on 2006-06-29
Sometimes computers act in mysterious ways... I give tech support at an isp, computers don't make sense.

---

### Post by gingermark on 2006-06-29
[QUOTE=SD-Plissken]gingermark is that using the default kernel?[/QUOTE]
Yep, using both the 386 & k7 kernels. Even in Breezy (when I had to load the nForce audio drivers myself) the network worked fine.

---

