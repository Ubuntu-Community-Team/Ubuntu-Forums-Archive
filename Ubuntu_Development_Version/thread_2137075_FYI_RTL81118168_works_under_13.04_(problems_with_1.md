---
title: "FYI: RTL8111/8168 works under 13.04 (problems with 12.10)"
date: 2013-04-19
forum: Ubuntu Development Version
---

### Post by sanderj on 2013-04-19
FYI / For The Record:

The 

25:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller (rev 06)

works automatigally under Ubuntu 13.04 (tested with 64-bit).

Relevant messages from dmesg:

```
ubuntu@ubuntu:~$ dmesg | grep -i eth | grep -vi ipv6 | grep -vi bluetooth
[    5.937789] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    5.938277] r8169 0000:25:00.0 eth0: RTL8168e/8111e at 0xffffc9000067e000, 2c:41:38:09:9c:bc, XID 0c200000 IRQ 45
[    5.938340] r8169 0000:25:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[   25.536183] r8169 0000:25:00.0 eth0: link down
[   25.536197] r8169 0000:25:00.0 eth0: link down
[   27.726757] r8169 0000:25:00.0 eth0: link up
ubuntu@ubuntu:~$ 
```

I get linespeed on my 300/300 Mbps Internet connection:

```
ubuntu@ubuntu:~$ wget -4 http://ftp.belnet.be/ubuntu.com/ubuntu/releases/precise/ubuntu-12.04.2-desktop-i386.iso -O /dev/null
--2013-04-19 17:53:43--  http://ftp.belnet.be/ubuntu.com/ubuntu/releases/precise/ubuntu-12.04.2-desktop-i386.iso
Resolving ftp.belnet.be (ftp.belnet.be)... 193.190.67.98
Connecting to ftp.belnet.be (ftp.belnet.be)|193.190.67.98|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 726970368 (693M) [application/x-iso9660-image]
Saving to: ‘/dev/null’

10% [===>                                   ] 76,738,837  30.3MB/s             
47% [=================>                     ] 346,957,357 35.1MB/s  eta 13s    
100%[======================================>] 726,970,368 37.9MB/s   in 22s    

2013-04-19 17:54:05 (31.0 MB/s) - ‘/dev/null’ saved [726970368/726970368]

ubuntu@ubuntu:~$ 
```


With 12.10 the GigE interface did not work, and I got a lot of ugly info in dmesg.

EDIT:

```
sander@hapee:~$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: RTL8111/8168 PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:25:00.0
       logical name: eth0
       version: 06
       serial: 2c:41:38:09:9c:bc
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.0.100 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:45 ioport:2000(size=256) memory:d4404000-d4404fff memory:d4400000-d4403fff
sander@hapee:~$
```

and:

```
sander@hapee:~$ lsmod | grep r8
r8169                  67446  0 
sander@hapee:~$ 
```

---

### Post by rtalcott on 2013-04-20
FYI.... just installed 13.04...clean new install on a working 12.04 machine (8111/8168) and and I have no wired connection...any clues on how to go about finding out why?

---

### Post by cariboo on 2013-04-20
> **rtalcott said:**
> FYI.... just installed 13.04...clean new install on a working 12.04 machine (8111/8168) and and I have no wired connection...any clues on how to go about finding out why?

Check to see if the driver is loaded using either:

```
lsmod | grep r8
```

or

```
lshw -C network
```

the first command will tell you if the driver is loaded, and the second command will give all the information about your network device, including what driver it is using.

---

### Post by rtalcott on 2013-04-21
First...Thank You for the response...I should know how to do this tuff by now but I guess I don't...I should learn something now (I hope!)

rtalcott@evga:~$ lsmod | grep r8
r8712u                189948  0 
r8169                  68680  0 

r8712u is the usb wireless I have connected.  so it looks like the r8168 driver is not there and it's not on my 12.04 installs on hardware that have a RTL8111/8168B hardware.

sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       product: RTL8111/8168 PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:bc:03:b9:67
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=no multicast=yes port=MII speed=100Mbit/s
       resources: irq:0 ioport:8c00(size=256) memory:fd8ff000-fd8fffff memory:fd7f0000-fd7fffff memory:fd700000-fd71ffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:3.4.4
       logical name: wlan0
       serial: 00:1a:ef:1b:ee:d3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u ip=192.168.1.117 multicast=yes wireless=IEEE 802.11bg

I see *-network disabled....not a good sign and this is the result of a clean install....

A kick in the correct direction would be greatly appreciated!
rt

---

### Post by sanderj on 2013-04-21
My lshw at capabilities says "firmware=rtl_nic/rtl8168e-2.fw". Yours doesn't.

I checked:

```

sander@hapee:~$ locate rtl8168e-2.fw
/lib/firmware/rtl_nic/rtl8168e-2.fw

sander@hapee:~$ dpkg -S rtl8168e-2.fw
linux-firmware: /lib/firmware/rtl_nic/rtl8168e-2.fw
sander@hapee:~$ 


```

... so can you run that command?

---

### Post by rtalcott on 2013-04-21
Looks like I get your result..


rtalcott@evga:~$ locate rtl8168e-2.fw
/lib/firmware/rtl_nic/rtl8168e-2.fw
rtalcott@evga:~$ dpkg -S rtl8168e-2.fw
linux-firmware: /lib/firmware/rtl_nic/rtl8168e-2.fw

---

### Post by sanderj on 2013-04-21
> **rtalcott said:**
> Looks like I get your result..


rtalcott@evga:~$ locate rtl8168e-2.fw
/lib/firmware/rtl_nic/rtl8168e-2.fw
rtalcott@evga:~$ dpkg -S rtl8168e-2.fw
linux-firmware: /lib/firmware/rtl_nic/rtl8168e-2.fw

... so why isn't it loaded? I have no idea. You could grep /var/log/* for 'firmware' and 'rtl'. Maybe that reveals something?

---

### Post by rtalcott on 2013-04-21
I don't see anything...I would suspect that I did something stupid but this is a clean standard install...and I let it go and do its thing....nothing but standard input from me.  I may have to install an Ethernet card...

---

### Post by rtalcott on 2013-04-21
Maybe later today I'll try to boot a livecd of 12.04 and see if I have the wired network connection.

---

### Post by rtalcott on 2013-04-21
same machine running a liveCD from 12.04...I have a wired connection:

ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:bc:03:b9:67
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.116 latency=0 multicast=yes port=MII speed=100Mbit/s
       resources: irq:40 ioport:8c00(size=256) memory:fd8ff000-fd8fffff memory:fd7f0000-fd7fffff memory:fd700000-fd71ffff
  *-network
       description: Wireless interface
       physical id: 3
       bus info: usb@2:3.3.4
       logical name: wlan0
       serial: 00:1a:ef:1b:ee:d3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u multicast=yes wireless=unassociated

---

### Post by rtalcott on 2013-04-21
13.04 gives me this:
sudo lshw -C network
*-network DISABLED
description: Ethernet interface
product: RTL8111/8168 PCI Express Gigabit Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.

12.04 this:
lshw -C network
WARNING: you should run this program as super-user.
*-network
description: Ethernet interface
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.

8168 vs. 8168B...any significance here?

---

### Post by cariboo on 2013-04-21
The output shows that the driver isn't loaded. I don't have that chipset, so I'm not sure what driver you need.

---

### Post by rtalcott on 2013-04-21
Weird (to me anyway)...works fine with 12.04 and not with 13.04....cannot remember if I tried 12.10 on this machine.  I did get the same 13.04 result with 3.8 and 3.9...

Maybe it will sort out as time goes by but then again maybe not.

---

### Post by cariboo on 2013-04-21
If you still have a working 12.04 installation, you can check it to see what driver the network card uses.

---

### Post by clearski on 2013-04-21
> **rtalcott said:**
> Weird (to me anyway)...works fine with 12.04 and not with 13.04....cannot remember if I tried 12.10 on this machine.  I did get the same 13.04 result with 3.8 and 3.9...

Maybe it will sort out as time goes by but then again maybe not.

I confirm that RTL811/8168 works perfectly with 13.04, it was instantly recognized when I installed.

---

### Post by rtalcott on 2013-04-21
From my 12.04 output...complete output on the previous page:

capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.116 latency=0 multicast=yes port=MII speed=100Mbit/s
resources: irq:40 ioport:8c00(size=256) memory:fd8ff000-fd8fffff memory:fd7f0000-fd7fffff memory:fd700000-fd71ffff

---

### Post by cariboo on 2013-04-21
> **rtalcott said:**
> From my 12.04 output...complete output on the previous page:

capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.116 latency=0 multicast=yes port=MII speed=100Mbit/s
resources: irq:40 ioport:8c00(size=256) memory:fd8ff000-fd8fffff memory:fd7f0000-fd7fffff memory:fd700000-fd71ffff

That's the driver I thought you needed, you can try loading that driver using the following command:

```
sudo modprobe r8169
```

with a bit of luck, networking should start working right away, if not use the following command:

```
sudo service networking restart
```

If that doesn't work, just reboot.

---

### Post by rtalcott on 2013-04-21
No cigar...if I modprobe and then restart networking it locks up....if I modprobe and then reboot it's no change (no wired Ethernet).  I'd be willing to say I had a hardware problem if it was not for the fact that it runs 12.04 fine...maybe I should download another daily and reinstall and hope....

---

### Post by cariboo on 2013-04-21
Have you checked to see if the module (driver) exists in /lib/modules/3.8.0-19-generic/kernel/drivers/net/ethernet/realtek. You should see the following in that directory:

```
ls -l
total 224
-rw-r--r-- 1 root root  43208 Apr 17 11:48 8139cp.ko
-rw-r--r-- 1 root root  52632 Apr 17 11:48 8139too.ko
-rw-r--r-- 1 root root  22228 Apr 17 11:42 atp.ko
-rw-r--r-- 1 root root 103356 Apr 17 11:42 r8169.ko
```

---

### Post by rtalcott on 2013-04-21
rtalcott@evga:/lib/modules/3.8.0-19-generic/kernel/drivers/net/ethernet/realtek$ ls -l
total 224
-rw-r--r-- 1 root root  43208 Apr 17 12:48 8139cp.ko
-rw-r--r-- 1 root root  52632 Apr 17 12:48 8139too.ko
-rw-r--r-- 1 root root  22228 Apr 17 12:42 atp.ko
-rw-r--r-- 1 root root 103356 Apr 17 12:42 r8169.ko

uname -a
Linux evga 3.9.0-030900rc7-generic #201304171402 SMP Wed Apr 17 18:04:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

edit:  I went through all the steps with the 3.8 kernel...same result.

---

### Post by rtalcott on 2013-04-25
FWIW I am doing an install using 13.04 and I now have wired Ethernet for the first time with 13.04....I have no clue why I had problems before but it appears to be working properly now.

---

### Post by Blodofferion on 2013-04-30
I have  Realtek 8111F which never worked under Ubuntu 12.10, so I always had to manually install r8168 driver from the Realtek website. After updating from 12.10 to 13.04 I get no wired connection and the drivers from Realtek won't install either (I get lots of errors). What should I do? At some point I remember unistalling r8189 on Ubuntu 12.10 if that matters.

---

### Post by quantumfoam on 2013-05-11
Hi,

I just installed Ubuntu 13.04 64bit Server on a Gigabyte H61N-D2V used as NAS, the onboard network adapter is a
```

Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller (rev 06)

```

After installation out of the box the adapter was named 'p4p1' which confuses the networking scripts that expect the interface to be named 'eth*'.

I tried to install the r8168 driver from [http://code.google.com/p/r8168/](http://code.google.com/p/r8168/) after stumbling upon [http://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/](http://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/), but you only get it to compile after removing the '__devinit's in src/r8168_n.c.

Anyway, after googling around I found out that the r8169 diver actually works, adding '"biosdevname=0' to the kernel options in /etc/default/grub
```

GRUB_CMDLINE_LINUX_DEFAULT="biosdevname=0"

```
fixed the problem and after a reboot the device was named eth0 and is working.

So if 
```

ifconfig -a

```
shows something like 'p4p1' you may want to try this.

---

### Post by cariboo on 2013-05-11
> **quantumfoam said:**
> Hi,

I just installed Ubuntu 13.04 64bit Server on a Gigabyte H61N-D2V used as NAS, the onboard network adapter is a
```

Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller (rev 06)

```

After installation out of the box the adapter was named 'p4p1' which confuses the networking scripts that expect the interface to be named 'eth*'.

I tried to install the r8168 driver from [http://code.google.com/p/r8168/](http://code.google.com/p/r8168/) after stumbling upon [http://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/](http://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/), but you only get it to compile after removing the '__devinit's in src/r8168_n.c.

Anyway, after googling around I found out that the r8169 diver actually works, adding '"biosdevname=0' to the kernel options in /etc/default/grub
```

GRUB_CMDLINE_LINUX_DEFAULT="biosdevname=0"

```
fixed the problem and after a reboot the device was named eth0 and is working.

So if 
```

ifconfig -a

```
shows something like 'p4p1' you may want to try this.

Does this fix also work in Saucy?

---

