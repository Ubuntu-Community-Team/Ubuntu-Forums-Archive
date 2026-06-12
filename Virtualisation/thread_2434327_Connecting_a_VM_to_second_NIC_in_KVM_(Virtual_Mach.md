---
title: "Connecting a VM to second NIC in KVM (Virtual Machine Manager)"
date: 2020-01-03
forum: Virtualisation
---

### Post by rkorson on 2020-01-03
So this is a somewhat newbie question.  I have Ubuntu 19.10 running as a HTPC but it's got power to spare. I have a second NIC it and would like to connect a guest VM  (Ubuntu or CentOS) directly to this card so it's seem on my LAN; meaning it gets a DHCP address and local DNS name from my rougher while my host OS does the same from the onboard NIC.  I plan to use this for light back-up services. 

I was planning on using KVM with Virtual Machine Manager to accomplish this. My reading has got me confused. It seem like I need to set up a bridge but might be able to do some sort of hardware direct addressing. What would be best way to do this.  I feel like this is simple but some discussions and tutorials have me going in circles. 

Thanks in advance for your help!

---

### Post by QIII on 2020-01-03
When you set up the VM, you can choose its NIC directly.  Just make sure you don't use the one dedicated to your host.

I have 13 VMs on this machine with 1 spare NIC on the mobo and 3 4-port NIC cards.  One of the NICs on the mobo is dedicated to the host.

No bridge needed.

---

### Post by rkorson on 2020-01-03
Thanks, I hoped it was that easy but I am having problems:  

My ifconfig looks like this: 

[INDENT]eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500[/INDENT]
[INDENT]        inet 192.168.0.234  netmask 255.255.255.0  broadcast 192.168.0.255[/INDENT]
[INDENT]        inet6 fe80::8a17:6c08:6733:8d3c  prefixlen 64  scopeid 0x20<link>[/INDENT]
[INDENT]        ether 98:90:96:9f:89:dd  txqueuelen 1000  (Ethernet)[/INDENT]
[INDENT]        RX packets 1030474  bytes 365795691 (365.7 MB)[/INDENT]
[INDENT]        RX errors 0  dropped 0  overruns 0  frame 0[/INDENT]
[INDENT]        TX packets 1609289  bytes 1031614589 (1.0 GB)[/INDENT]
[INDENT]        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0[/INDENT]
[INDENT]        device interrupt 20  memory 0xf7f00000-f7f20000  [/INDENT]
[INDENT]
[/INDENT]
[INDENT]enp4s2: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500[/INDENT]
[INDENT]        ether 00:0a:5e:19:c2:cc  txqueuelen 1000  (Ethernet)[/INDENT]
[INDENT]        RX packets 380732  bytes 369544437 (369.5 MB)[/INDENT]
[INDENT]        RX errors 0  dropped 6123  overruns 0  frame 0[/INDENT]
[INDENT]        TX packets 96312  bytes 7663699 (7.6 MB)[/INDENT]
[INDENT]        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0[/INDENT]
[INDENT]        device interrupt 19  [/INDENT]
[INDENT]
[/INDENT]
[INDENT]lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536[/INDENT]
[INDENT]        inet 127.0.0.1  netmask 255.0.0.0[/INDENT]
[INDENT]        inet6 ::1  prefixlen 128  scopeid 0x10<host>[/INDENT]
[INDENT]        loop  txqueuelen 1000  (Local Loopback)[/INDENT]
[INDENT]        RX packets 39721  bytes 5167336 (5.1 MB)[/INDENT]
[INDENT]        RX errors 0  dropped 0  overruns 0  frame 0[/INDENT]
[INDENT]        TX packets 39721  bytes 5167336 (5.1 MB)[/INDENT]
[INDENT]        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0[/INDENT]
[INDENT]
[/INDENT]
[INDENT]virbr0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500[/INDENT]
[INDENT]        inet 192.168.122.1  netmask 255.255.255.0  broadcast 192.168.122.255[/INDENT]
[INDENT]        ether 52:54:00:68:45:9c  txqueuelen 1000  (Ethernet)[/INDENT]
[INDENT]        RX packets 0  bytes 0 (0.0 B)[/INDENT]
[INDENT]        RX errors 0  dropped 0  overruns 0  frame 0[/INDENT]
[INDENT]        TX packets 20  bytes 6090 (6.0 KB)[/INDENT]
[INDENT]        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
[/INDENT]

I am tying to use enp4s2.  When I start of new VM and the wizard ask me select s Network I can pick "Host device enp4s2: maxtap. Then ask for as source what should I select, nothing seems to work.  Thanks!

---

