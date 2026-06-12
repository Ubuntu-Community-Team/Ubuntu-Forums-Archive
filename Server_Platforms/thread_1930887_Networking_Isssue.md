---
title: "Networking Isssue"
date: 2012-02-24
forum: Server Platforms
---

### Post by paulwilson5x on 2012-02-24
Hi Im running ubuntu server 11.10, when I tried to 'sudo apt-get install vsftpd" i get the result of 
'err [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) oneiric-security/main vsftpf i386 2.3.2-3ubuntu5.1
Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/v/vsftpd/vsfptd_2.3.2-3ubuntu5.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/v/vsftpd/vsfptd_2.3.2-3ubuntu5.1_i386.deb)........................................................'

Also cannot ping [www.google.com]("http://www.google.com") = unknown host [www.google.com]("http://www.google.com")

How can I troubleshoot this network problem?

Thanks

---

### Post by roelforg on 2012-02-24
Give us the output of:
```

sudo ifconfig -a
sudo cat /etc/network/interfaces
sudo uname -a
sudo cat /etc/resolv.conf
sudo lshw -C network

```

---

### Post by spynappels on 2012-02-24
The unknown host message suggests a DNS  issue, so the 
```
cat /etc/resolv.conf
```
should have some entries in it like
```
nameserver 8.8.8.8
```
where the IP address is that of a valid DNS, the IP above is one of Google's DNS servers.

---

### Post by paulwilson5x on 2012-02-24
eth0      Link encap:Ethernet  HWaddr 08:00:27:56:61:d5
          BROADCAST MULTICAST MTU:1500 Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 08:00:27:E5:5a:43  
          inet addr:192.168.100.20  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe0e:64e2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5363 (5.3 KB)  TX bytes:944 (944 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:557 errors:0 dropped:0 overruns:0 frame:0
          TX packets:557 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:160611 (160.6 KB)  TX bytes:160611 (160.6 KB)'

"auto eth1
iface eth1 inet static
address 192.168.100.20
network 192.168.100.0
netmask 255.255.255.0
broadcast 192.168.100.255"

"Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux"

"nameserver 208.67.222.222
nameserver 208.67.220.220"

"*-network:0  DISABLED  
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 02
       serial: 08:00:27:56:61:D5
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full firmware=N/A ip=10.0.2.15 latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:10 memory:f0000000-f001ffff ioport:d010(size=8)
  *-network:1
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:00:08.0
       logical name: eth1
       version: 02
       serial: 08:00:27:e5:5a:43
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full firmware=N/A ip=192.168.100.10 latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:9 memory:f0820000-f083ffff ioport:d240(size=8)"

Sorry for the long reply time

---

### Post by roelforg on 2012-02-24
Try:
```

sudo ifup eth0

```

---

### Post by paulwilson5x on 2012-02-24
Ignoring unknown interface eth0=eth0

---

### Post by roelforg on 2012-02-24
If you're using dhcp, why are you using static ip's?

I'm curious, why aren't you using eth0 or the full speed of either nic?

---

### Post by paulwilson5x on 2012-02-24
Im not really sure to be honest, im totally new to this and just following a handout i received in college.

---

### Post by roelforg on 2012-02-24
> **paulwilson5x said:**
> Im not really sure to be honest, im totally new to this and just following a handout i received in college.
Plug the ethernet cable in the other NIC.
Or plug cables in both

---

### Post by paulwilson5x on 2012-02-24
Iv only got the 1, its a laptop

---

### Post by kevinthecomputerguy on 2012-02-24
try adding          gateway 192.168.100.1

auto eth1
iface eth1 inet static
address 192.168.100.20
network 192.168.100.0
[COLOR=Red]gateway 192.168.100.1[/COLOR]
netmask 255.255.255.0
broadcast 192.168.100.255

---

### Post by roelforg on 2012-02-24
> **paulwilson5x said:**
> Iv only got the 1, its a laptop
Then why is ubuntu seeing 2 wired nic's?

---

### Post by paulwilson5x on 2012-02-24
sorry im running it in virtual box, i have it connected to a ubuntu desktop in virtual box

---

### Post by kevinthecomputerguy on 2012-02-24
That changes everything.
Go into virtual box and change the nic to NAT and then change your config file back to DHCP.

*side note, your going to have a heck of a time trying to use ftp server behind a NAT. Look into sftp \ bridged.

---

### Post by paulwilson5x on 2012-02-24
allready have adapter 1 attached to NAT and adapter 2 attached to internal network

---

### Post by kevinthecomputerguy on 2012-02-24
switch your config file back to DHCP, virtual box will hand it a private address for you.

---

### Post by roelforg on 2012-02-24
> **paulwilson5x said:**
> allready have adapter 1 attached to NAT and adapter 2 attached to internal network
```

sudo dhclient eth0

```

and make sure the following is in /etc/network/interfaces
```

auto eth0
iface eth0 inet dhcp

```

---

### Post by paulwilson5x on 2012-02-24
great stuff thanks a million to the both of u. thats working now. thanks again

---

### Post by roelforg on 2012-02-24
> **paulwilson5x said:**
> great stuff thanks a million to the both of u. thats working now. thanks again
Sure, that's why we're here.

---

