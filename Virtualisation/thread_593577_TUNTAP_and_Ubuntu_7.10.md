---
title: "TUN/TAP and Ubuntu 7.10"
date: 2007-10-27
forum: Virtualisation
---

### Post by gazambuja on 2007-10-27
Hi, i installed Qemu in my Ubuntu 7.10 x64, but TUN/TAP not work:

 sudo qemu -hda disco.img -net nic,vlan=0 -net tap,vlan=0
 /etc/qemu-ifup: could not launch network script
 Could not initialize device 'tap'

I too install bridge-utils and vtun, but not work.

gustavo@LMC:~$ ls /dev/net/tun -lh
crw-rw---- 1 root root 10, 200 2007-10-14 21:44 /dev/net/tun


Any help?

---

### Post by bodhi.zazen on 2007-10-27
You need to configure the device.

Here is the script I use : (add these lines to /etc/rc.local)

> # For Network Bridging/TAP

# Set permissions of tun device
chown root.users /dev/net/tun **#If you like you can make a group "qemusers" and use "root.qemusers" **
chmod g+rw /dev/net/tun

#Add a bridge, add eth0
brctl addbr br0
ifconfig eth0 0.0.0.0 promisc
brctl addif br0 eth0
dhclient br0

# Create tap1
tunctl -t tap1 -u <user> **#Be sure to change "<user>" to your user name**

# Enable tap1
brctl addif br0 tap1
ifconfig tap1 up

Then, enter this command :

```
sudo /etc/rc.local
```

If you do not use dhcp, you will need to set a static ip

---

### Post by gazambuja on 2007-10-27
ok, i have question?
i change this line:
 ifconfig eth1 0.0.0.0 promisc
to:
 ifconfig eth0 0.0.0.0 promisc

(i not have eth1), but if i have eth0 with connection pppoe, this line, its fine for me?

My ifconfig now is:

gustavo@LMC:~$ ifconfig 
eth0       Encapsulamento do Link: Ethernet  Endereço de HW 00:1A:92:7C:0B:85  
          endereço inet6: fe80::21a:92ff:fe7c:b85/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:895462 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:964223 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:694405261 (662.2 MB) TX bytes:233050832 (222.2 MB)
          IRQ:23 Endereço de E/S:0xc000 
ppp0       Encapsulamento do Link: Protocolo Ponto-a-Ponto  
          inet end.: 201.95.112.43  P-a-P:200.204.210.246  Masc:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Métrica:1
          pacotes RX:895124 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:963879 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:3 
          RX bytes:674692077 (643.4 MB) TX bytes:207967694 (198.3 MB)

---

### Post by bodhi.zazen on 2007-10-27
Ooops ;redface:

I editied my script back to eth0.

Your output looks OK to me ...

Now you need to add a bridge and tap (your internet access will go down during those steps)

---

### Post by gazambuja on 2007-10-27
:-( i want have internet too (i use iptables for forwarding intenet to my guest).

---

### Post by bodhi.zazen on 2007-10-27
LOL

Your internet will come back up once the bridge and tap are configured.

I am warning you that during the configuration process your internet connection will go down.

---

### Post by gazambuja on 2007-10-28
Hello, well, yesterday i install Ubuntu 7.10 x32 and for my sorprise, qemu and TUN/TAP work fine without any extrange configuration (only install and run)... But not all is good, today, i turn on my computer and qemu not work!!! the same error!

gustavo@LMC:~$ lsmod |grep tun
tun                    12288  0
qemu kuboIT.img -net nic,vlan=0 -net tap,vlan=0,script=/etc/qemu-ifup
SIOCSIFADDR: Não há tal dispositivo
/etc/qemu-ifup:: ERRO ao obter marcadores da interface: Não há tal dispositivo
/etc/qemu-ifup: could not launch network script
Could not initialize device 'tap'

i not understand, i never add a bridge manualy :-(

---

### Post by bodhi.zazen on 2007-10-28
I assume you re-booted and my guess is you need to add a tap device again.

If this is the case, add the appropriate commands to /etc/rc.local and you will make a tap at boot.

---

### Post by Powderhound on 2007-11-09
Hi, I have followed all the instructions in here to setup tap to allow access to the local network and Internet but I am unable to do so.
Could someone please look at my config and hopefully point me inthe right direction.

rc.local

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# For Network Bridging/TAP

# Set permissions of tun device
chown root.users /dev/net/tun #If you like you can make a group "qemusers" and use "root.qemusers"
chmod g+rw /dev/net/tun

#Add a bridge, add eth0
brctl addbr br0
ifconfig eth0 0.0.0.0 promisc
brctl addif br0 eth0
dhclient br0

# Create tap1
tunctl -t tap1 -u currans #Be sure to change "<user>" to your user name

# Enable tap1
brctl addif br0 tap1
ifconfig tap1 up

exit 0

================

ifconfig

currans@currans-desktop:~$ ifconfig
br0       Link encap:Ethernet  HWaddr 00:02:A5:8F:82:C1  
          inet addr:10.238.38.20  Bcast:10.238.38.255  Mask:255.255.255.0
          inet6 addr: fe80::202:a5ff:fe8f:82c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3582 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2555368 (2.4 MB)  TX bytes:404937 (395.4 KB)

eth0      Link encap:Ethernet  HWaddr 00:02:A5:8F:82:C1  
          inet6 addr: fe80::202:a5ff:fe8f:82c1/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:14322 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3616 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1 txqueuelen:1000 
          RX bytes:2782373 (2.6 MB)  TX bytes:409806 (400.2 KB)

qtap0     Link encap:Ethernet  HWaddr 00:FF:B9:4F:28:3E  
          inet addr:10.111.111.254  Bcast:10.111.111.255  Mask:255.255.255.0
          inet6 addr: fe80::2ff:b9ff:fe4f:283e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:53 (53.0 b)  TX bytes:3601 (3.5 KB)

tap0      Link encap:Ethernet  HWaddr 00:FF:66:CE:96:A5  
          inet addr:172.20.0.1  Bcast:172.20.255.255  Mask:255.255.0.0
          inet6 addr: fe80::2ff:66ff:fece:96a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:7644 (7.4 KB)  TX bytes:3888 (3.7 KB)

tap1      Link encap:Ethernet  HWaddr 00:FF:A9:AB:16:31  
          inet6 addr: fe80::2ff:a9ff:feab:1631/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:10374 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


ipconfig on the windows 98 virtual machine

dhcp enabled
IP address 10.0.2.15
default gateway 10.0.2.2
dhcp server 10.0.2.2

I also don't know where to disable the Qemu dhcp server, if I need to to prevent it picking up a dhcp address

Thanks for any assistance you can offer :-)

---

### Post by shogun1234 on 2008-08-03
I follow the script and save that script as setup_qemu_network.sh. The content is as follow:

```

sudo /sbin/brctl addbr br0
sudo /sbin/ifconfig wlan0 0.0.0.0 promisc
sudo /sbin/brctl addif br0 wlan0
sudo /sbin/dhclient br0

/bin/tunctl -t tap1 -u `whoami`

sudo /sbin/brctl addif br0 tap1
sudo /sbin/ifconfig tap1 up

```

Its output shows:
```

device br0 already exists; can't create bridge with the same name
device wlan0 is already a member of a bridge; can't enslave it to bridge br0.
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/br0/00:1f:3b:21:25:13
Sending on   LPF/br0/00:1f:3b:21:25:13
Sending on   Socket/fallback
DHCPREQUEST on br0 to 255.255.255.255 port 67
DHCPREQUEST on br0 to 255.255.255.255 port 67
DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.1.254
DHCPREQUEST on br0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.254
bound to 192.168.1.68 -- renewal in 1364 seconds.
Set 'tap1' persistent and owned by uid 1000
device tap1 is already a member of a bridge; can't enslave it to bridge br0.

```
Then I startup qemu with following code:
```

qemu -hda c.img -m 512 -net nic -net tap -localtime

```
but it returns 
```

warning: could not configure /dev/net/tun: no virtual network emulation
Could not initialize device 'tap'

```
How to solve this problem?

Thank you very much,



> **bodhi.zazen said:**
> You need to configure the device.

Here is the script I use : (add these lines to /etc/rc.local)



Then, enter this command :

```
sudo /etc/rc.local
```

If you do not use dhcp, you will need to set a static ip

---

### Post by bodhi.zazen on 2008-08-03
This is a bit of an old thread, what I do now is outlined on the KVM wiki page.

This script works as a wrapper for KVM and can easily be adapted for qemu or other bridging

See : [https://help.ubuntu.com/community/KVM#Bridged%20Networking](https://help.ubuntu.com/community/KVM#Bridged%20Networking)

Scroll up to the bridging section to set up a bridge in /etc/network/interfaces

---

### Post by An_Evil_Penguin on 2010-12-09
Hi there,
 
Well its almost 2011 and I thought I'd let you know that this thread was an absolute godsend in getting Qemu configured! I've referenced this thread very heavily in a howto I posted on my main forum at the moment and was hoping that this would be alright with you? The post in qestion is at [http://readynas.com/forum/viewtopic.php?f=35&t=30963&p=277472#p277472](http://readynas.com/forum/viewtopic.php?f=35&t=30963&p=277472#p277472)

---

### Post by bodhi.zazen on 2010-12-09
> **An_Evil_Penguin said:**
> Hi there,
 
Well its almost 2011 and I thought I'd let you know that this thread was an absolute godsend in getting Qemu configured! I've referenced this thread very heavily in a howto I posted on my main forum at the moment and was hoping that this would be alright with you? The post in qestion is at [http://readynas.com/forum/viewtopic.php?f=35&t=30963&p=277472#p277472](http://readynas.com/forum/viewtopic.php?f=35&t=30963&p=277472#p277472)

Nice post EP

I have a bit of information on my blog re: KVM if you wish.

Here is one:

[http://blog.bodhizazen.net/linux/improve-kvm-performance/](http://blog.bodhizazen.net/linux/improve-kvm-performance/)

most of what is in the blog under kvm also applies to qemu.

Enjoy

/me reads EP how-to

---

