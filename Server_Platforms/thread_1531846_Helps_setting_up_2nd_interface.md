---
title: "Helps setting up 2nd interface"
date: 2010-07-15
forum: Server Platforms
---

### Post by ehigginsfreese on 2010-07-15
I am having trouble setting up my second network interface on Ubuntu Server 10.04 and I was hoping someone could tell me what I am doing wrong.  I am pretty much new to Linux so I bet it is easy.  When setting up the machine it did detect both cards but I only picked one to configure, and now I want to setup the second.

I went into /etc/interfaces and basically copied the settings for eth0 but changed the IP and the name to eth1.  I then restarted.  

Quite honestly it might be working! But when I run ifconfig -a I see no packets I see

> eth1      Link encap:Ethernet  HWaddr 00:0e:0c:59:af:c4
          inet addr:192.168.4.21  Bcast:192.168.4.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Now I am noob about Linux but too me it looks like it is saying it is up...isn't that what "UP BROADCAST...." line means?

So perhaps my question is how do I test my 2nd interface?  I tried using the 2nd IP with Putty (which is how I usually work on the machine) and couldn't connect.  

Thanks for any help you can provide.

Eric

---

### Post by gencha on 2010-07-15
Does your computer also have an IP address in the 192.168.4.0 network?

---

### Post by ruffEdgz on 2010-07-15
I hate to say this but... do you have an internet cable connected to your eth1 port? :lolflag:

If you only changed the IP and name in the configuration of eth1, you might want to make sure you don't have two gateways in place. For example:
```

auto eth0
iface eth0 inet static
address 192.168.4.20
netmask 255.255.255.0
gateway 192.168.4.1

auto eth1
iface eth1 inet static
address 192.168.4.21
netmask 255.255.255.0

```

Once you think you have it set up correctly, you will need to go to another computer that has the ability to communicate to the eth0 connection and try to ping or telnet (to port 22 if its open) to eth1's ip address.

If this doesn't work, maybe place the two configurations for eth0 and eth1 on there, show what you get after running the command 'netstat -rn'.

Make sure you restart your /etc/init.d/networking when you make changes to the 'interfaces' file :D

---

### Post by ehigginsfreese on 2010-07-15
Yup cable plugged in.  My machine is on a different network - this machine is on the DMZ but I can ping the eth0 interface (192.168.4.20) and cannot ping the eth1 interface (192.168.4.21)

Here is the information in interfaces and when I run ifconfig -a

> uto eth0
iface eth0 inet static
        address 192.168.4.20
        netmask 255.255.255.0
        network 192.168.4.0
        broadcast 192.168.4.255
        gateway 192.168.4.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.4.11
        dns-search crlibrary.org

auto eth1
iface eth1 inet static
        address 192.168.4.21
        netmask 255.255.255.0
        network 192.168.4.0
        broadcast 192.168.4.255
        gateway 192.168.4.1
        dns-nameservers 192.168.4.1
        dns-search crlibrary.org


and

> 
eth0      Link encap:Ethernet  HWaddr 00:11:43:30:6e:76
          inet addr:192.168.4.20  Bcast:192.168.4.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe30:6e76/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:125 errors:0 dropped:0 overruns:0 frame:0
          TX packets:109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:13108 (13.1 KB)  TX bytes:18433 (18.4 KB)
          Interrupt:28

eth1      Link encap:Ethernet  HWaddr 00:0e:0c:59:af:c4
          inet addr:192.168.4.21  Bcast:192.168.4.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)




Which log would I check to see if there were errors when I "/etc/init.d/networking restart"?  Maybe that would hold a clue, but I don't see a log called "network" or "networking" in /var/log.

---

### Post by ehigginsfreese on 2010-07-15
> **ruffEdgz said:**
> 
If this doesn't work, maybe place the two configurations for eth0 and eth1 on there, show what you get after running the command 'netstat -rn'.
 

I get

> Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.4.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
192.168.4.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.4.1     0.0.0.0         UG        0 0          0 eth0
0.0.0.0         192.168.4.1     0.0.0.0         UG        0 0          0 eth1


---

### Post by ruffEdgz on 2010-07-15
Make a backup of your interface file:
```

sudo cp -a /etc/network/interface ~/interface.bak

```

Then take this code below and replace it for your eth0 and eth1, restart your network and see if this works:
```

auto eth0
iface eth0 inet static
address 192.168.4.20
netmask 255.255.255.0
network 192.168.4.0
broadcast 192.168.4.255
gateway 192.168.4.1
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 192.168.4.11
dns-search crlibrary.org

auto eth1
iface eth1 inet static
address 192.168.4.21
netmask 255.255.255.0

```

If it doesn't, replace the edited interface file with your backup so you can always go back to the older version.

As for the logs, just check both to make sure both are recording any logs for you :D

Also, are you still able to ping your old IP with your old configuration in place?

---

### Post by ehigginsfreese on 2010-07-16
> **ruffEdgz said:**
> idea here



This worked.  Although it confuses me because why should it?  I put in t*oo much information*?  The information was all correct so why wouldn't it work? 

Anyway, thank you very much.  Now I know a bit more about Linux!

---

### Post by ruffEdgz on 2010-07-16
It wasn't that the information for the second NIC was incorrect but to much.

You really don't need the broadcast, network and DNS information (unless it was called for that is) to get a NIC to work but once you add a second NIC to your server, you can not have a GATEWAY on the second NIC.

Glad it works and have fun learning more about Ubuntu :D

---

