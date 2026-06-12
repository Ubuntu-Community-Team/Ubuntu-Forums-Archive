---
title: "Problem while trying to use two NIC in 7.10"
date: 2008-04-28
forum: Server Platforms
---

### Post by mathieublais on 2008-04-28
I'm currently having problem trying to setup a second NIC in 7.10 ubuntu server. I tried to modify /etc/network/interfaces so it activates both NIC at start but soon both are on server doesn't respond anymore, unable to ping anything. It seems to get confused when both cards are on.

We had to get a second inet line in because we needed more bandwidth.So the main goal is to have the server in two seperate network. The services activated on server are Apache, FTP, POP and SMTP.

On one NIC, external clients needs to be able to access FTP, HTTP and POP. On the other NIC, local users would need to be able to send email thru the local SMTP.

Here's my interfaces file:
Here's my file
# The loopback network interface
auto lo eth0 eth2
iface lo inet loopback

# The primary network interface
iface eth0 inet static
address 192.168.1.8
netmask 255.255.255.0
network 192.168.1.1
broadcast 192.168.1.255
gateway 192.168.1.1
# dns-* options are implemented by the resolvconf package, if installed
# dns-nameservers 198.235.216.131

iface eth2 inet static
address 10.0.0.8
netmask 255.255.255.0
broadcast 10.0.0.255
network 10.0.0.0

---

### Post by cdtech on 2008-04-28
What do you get with:
```
ifconfig
```

---

### Post by mathieublais on 2008-04-28
eth0      Link encap:Ethernet  HWaddr 00:04:23:AE:CC:CC  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:23ff:feae:cccc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:118695240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:123035874 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:2177731715 (2.0 GiB)  TX bytes:1616370455 (1.5 GiB)
          Base address:0xecc0 Memory:dfde0000-dfe00000 

eth2      Link encap:Ethernet  HWaddr 00:04:23:AE:CC:CD  
          inet addr:10.0.0.8  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::204:23ff:feae:cccd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:311 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:2189019 (2.0 MiB)  TX bytes:75331 (73.5 KiB)
          Base address:0xec80 Memory:dfdc0000-dfde0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10164170 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10164170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3285759120 (3.0 GiB)  TX bytes:3285759120 (3.0 GiB)

---

### Post by carbm1 on 2008-04-28
Are you sure its not supposed to be eth0 and eth1.

Try changing your eth2 to eth1, restart, and see if it works.

---

