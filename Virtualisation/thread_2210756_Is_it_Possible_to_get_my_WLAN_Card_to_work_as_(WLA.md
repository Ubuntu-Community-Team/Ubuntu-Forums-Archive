---
title: "Is it Possible to get my WLAN Card to work as (WLAN0) Virtualbox - Ubuntu 12.04?"
date: 2014-03-12
forum: Virtualisation
---

### Post by scrypt on 2014-03-12
Hello.

I have ubuntu 12.04 LTS installed in Virtualbox (v4.3.8 r92456)
On my Dell Inspiron 15R SE 7520 with an internal Intel Centrino N-2230 WLAN (WIFI) Card.
I want to  to use my WLAN card as WLAN0. but i have not been able to do this after everything i have tried.
I am newly back to Ubuntu, i must admit it feels like starting again.
I have read up various topics on this issue i am having and apparently it is possible, with the correct configuration.
this is the basis of my post.

I have tried all the various network adapter settings:

NAT
NAT Network
Bridged Adapter

I have not been able to get my card working as WLAN0 in any of these settings.
i think ive installed extension pack correctly also.

Here is my ifconfig output

VirtualBox:~$ ifconfig
eth8      Link encap:Ethernet  HWaddr 08:00:27:0d:2b:dc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1296 (1.2 KB)  TX bytes:1296 (1.2 KB)

can anyone help me to correctly configure my WLAN card (internal Intel Centrino N-2230) to be able to work as (WLAN0) ?
I am a relative beginner to Ubuntu and i really want to learn how to get this to work in virtualbox.

I look froward to any replies.

Thanks.

---

### Post by ajgreeny on 2014-03-12
In a VM using Virtualbox I think the guest runs using the connection of the host as if it were a hard wired connection from the host, so I do not think it will be possible to get it showing as if it's wireless.  Do you get any connection when running the guest or is it not connecting to the web?

I do not run VB on a wireless connected machine so can not check that, but in your guest run ```
sudo lshw -c network
``` which may show you some information that helps us understand the way it is working.

---

### Post by scrypt on 2014-03-12
hello ajgreeny

here is my

 sudo lshw -c network 

output:

VirtualBox:~$ sudo lshw -c network
[sudo] password for modus: 
  *-network:0             
       description: Ethernet interface
       product: 82543GC Gigabit Ethernet Controller (Copper)
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth8
       version: 02
       serial: 08:00:27:0d:2b:dc
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full ip=10.0.2.15 latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:19 memory:f0000000-f001ffff ioport:d010(size=8)
  *-network:1
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:00:08.0
       logical name: eth7
       version: 02
       serial: 08:00:27:ac:f7:67
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full ip=192.168.1.68 latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:16 memory:f0820000-f083ffff ioport:d240(size=8)
VirtualBox:~$

---

### Post by lukeiamyourfather on 2014-03-12
VirtualBox emulates certain hardware devices, as far as I know there are no wireless devices that it will emulate. The "ethX" devices in VirtualBox guests are by default Intel gigabit Ethernet adapters. Probably because the Intel adapters have ubiquitous operating system support.

---

### Post by lukeiamyourfather on 2014-03-12
I should've clarified that previous post more. As long as the host operating system has a network connection that's all that matters. The guest will see the Intel gigabit adapter and use that for it's network connection. That then goes through NAT and to the host network adapter (be that wireless or something else). In other words, it doesn't matter whether or not the guest sees your wireless connection because it doesn't care what the host uses to connect to the network.

---

### Post by scrypt on 2014-03-12
hello lukeiayf
okay  understand that much.
i would like to use my wifi card for pentest'g through VB.
Am i right in thinking that the only way i could get this to work would be to boot ubuntu live USB make a full HDD/Partition install

Or is it possible to do this using Ubuntu on VB ?
if it is can you please explain to me how i can configure VB - Ubuntu to allow my Laptops internal WiFi card to allow this

Would it be possible using and USB connected WIFI Adapter ?

---

### Post by CharlesA on 2014-03-13
You would need a USB wifi card. We do not support pen testing applications here, so just an FYI.

---

### Post by lukeiamyourfather on 2014-03-13
Regardless of what the application does, if it needs direct access to the hardware a virtual machine won't cut it. Live booting is one option, dual booting is another, also check out Knoppix or BackTrack if you haven't already which maybe more suited to your needs than Ubuntu.

---

