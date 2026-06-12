---
title: "Can't find wifi networks from 16.04 live USB"
date: 2016-07-09
forum: Ubuntu Studio
---

### Post by Haven_McClure on 2016-07-09
In reading the instructions for installing Ubuntu Studio 16.04 from an USB boot, it strongly recommended that I connect to the Internet first before installing 16.04 from the boot disc.  Problem is, when I run 16.04 from the USB on my Lenovo Z40-70 laptop, it doesn't recognize the wifi networks even though my installed version of 14.04 has no problem running them.  When I create a new connection from scratch, I noticed that I am allowed to enter the name and the WPA2 password of the connection.  But even after doing so, it still won't show the network, and when I go back to edit the connection, the Z40-70 won't show the option for a WPA password--just the WEP passwprds. 

So I can't connect to the network from live mode.  i could connect and install via ethernet cable but i fear not being able to connect to the internet once the new system is installed.  Any thoughts on  how to proceed from here?  

Haven

---

### Post by jejeman on 2016-07-09
Give
```
lshw -numeric -c network
```

---

### Post by Haven_McClure on 2016-07-12
Okay, here's what I get. 

```
haven@haven-Lenovo-Z40-70:~$ lshw -numeric -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10EC:8168]
       vendor: Realtek Semiconductor Co., Ltd. [10EC]
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 10
       serial: 68:f7:28:28:8d:00
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:61 ioport:4000(size=256) memory:c3504000-c3504fff memory:c3500000-c3503fff
  *-network
       description: Wireless interface
       product: BCM43142 802.11b/g/n [14E4:4365]
       vendor: Broadcom Corporation [14E4]
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 38:b1:db:d1:2a:59
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=192.168.1.7 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:19 memory:c3400000-c3407fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
haven@haven-Lenovo-Z40-70:~$ 
```

This is what I run from 14.04.  Should I try this with the 16.04 USB?

---

### Post by Haven_McClure on 2016-07-16
bump

---

### Post by wildmanne39 on 2016-07-17
Your wifi should work in ubuntu 16.04 but it might take some tweaking because broadcom drivers have been having issues with secure boot, if you have secure boot. 

You do not want to be connected to wifi when you install you aways want to use an ethernet connection because the wifi driver usually gets updated and it will knock you offline and that is why you use an ethernet connection when installing or upgrading.

---

### Post by lhb1142 on 2016-07-29
> **Haven_McClure said:**
> In reading the instructions for installing Ubuntu Studio 16.04 from an USB boot, it strongly recommended that I connect to the Internet first before installing 16.04 from the boot disc.  Problem is, when I run 16.04 from the USB on my Lenovo Z40-70 laptop, it doesn't recognize the wifi networks even though my installed version of 14.04 has no problem running them.  When I create a new connection from scratch, I noticed that I am allowed to enter the name and the WPA2 password of the connection.  But even after doing so, it still won't show the network, and when I go back to edit the connection, the Z40-70 won't show the option for a WPA password--just the WEP passwprds. 

So I can't connect to the network from live mode.  i could connect and install via ethernet cable but i fear not being able to connect to the internet once the new system is installed.  Any thoughts on  how to proceed from here?  

Haven

I had a similar problem with an Alienware 17 R3. The live 16.04 DVD would not recognize my Wi-Fi network though, like you, I could connect to the Internet via an Ethernet cable. The problem was with the new "Killer" Wi-Fi network connector (NIC) installed on this computer.

I did some investigating and discovered that newer drivers for this and some other network connectors were to be made available with the 16.04.1 installation disc via a kernel update included with that file.

To make a long story short, I waited until July 21, downloaded the new 16.04.1 ISO file, burned it to a disc, and installed the operating system.

It works perfectly. (I didn't even bother to try the "Live DVD" option first, I was that confident!) You could also install the system via a USB thumb drive if you prefer. Just get the new v. 16.04.1 and I'm sure all will be well.

If you're not confident, just investigate the compatibility of your NIC with the newest version of Ubuntu Studio. I'm fairly certain that your network card will now be recognized.

I should mention that I installed Ubuntu Studio 16.04.1 with both UEFI and Secure Boot *activated*. There have been no problems at all with either the installation or the running of the system.

I hope that this is helpful to you.

---

