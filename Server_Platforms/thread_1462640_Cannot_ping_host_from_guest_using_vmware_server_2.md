---
title: "Cannot ping host from guest using vmware server 2"
date: 2010-04-25
forum: Server Platforms
---

### Post by cocotu on 2010-04-25
Not sure if this post belongs here, but here it is.

Host: Win server 2003
Guest: Ubuntu server

Host: IS able to ping guest. Firewall is OFF. NOT able to access guest (which is a web-server) at browser.
Guest: NOT able to ping host. Running a web server, you can check the website: (pegajosa.com) is running under that virtual linux server.

Problem: guest needs to access host's sql database and/or any resources.

Network: is bridged.

At the linux box ifconfig -a:
> eth0 Link encap:Ethernet HWaddr 00:0c:29:57:54:ad
inet addr:208.85.240.163 Bcast:208.85.240.175 Mask:255.255.255.240
inet6 addr: fe80::20c:29ff:fe57:54ad/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:579 errors:0 dropped:0 overruns:0 frame:0
TX packets:762 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:79319 (79.3 KB) TX bytes:745686 (745.6 KB)
Interrupt:19 Base address:0x2000

eth1 Link encap:Ethernet HWaddr 00:0c:29:57:54:b7
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:18 Base address:0x2080

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:104 errors:0 dropped:0 overruns:0 frame:0
TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:10296 (10.2 KB) TX bytes:10296 (10.2 KB)

at win 2003 server ipconfig:
> Ethernet adapter VMware Network Adapter VMnet8:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : VMware Virtual Ethernet Adapter for VMnet8
   Physical Address. . . . . . . . . : 00-50-56-C0-00-08
   DHCP Enabled. . . . . . . . . . . : No
   IP Address. . . . . . . . . . . . : 192.168.239.1
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . :
   DNS Servers . . . . . . . . . . . : 208.85.240.162

Ethernet adapter VMware Network Adapter VMnet1:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : VMware Virtual Ethernet Adapter for VMnet1
   Physical Address. . . . . . . . . : 00-50-56-C0-00-01
   DHCP Enabled. . . . . . . . . . . : No
   IP Address. . . . . . . . . . . . : 192.168.248.1
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . :

i was told to add a virtual nic for the linux server which is eth1, but it does not show the ip.  this is my interface file:
> iface eth1 inet static
        address 192.168.248.101
        netmask 255.255.255.0
i tried with default gateway 192.168.248.1 and still no luck. thanks for any help

---

### Post by iissmart on 2010-04-25
You should also have "auto eth1" in your interfaces file as well, to automatically bring up the interface. What is the output of

```
$ ifup eth1
```

---

### Post by windependence on 2010-04-26
issmart is correct, but may I make another suggestion? You should be running your SQL server as a separate guest and keep that off the host. In fact, I would be running VMware ESXi bare metal without a host at all for my virtualization. It's free (as in beer).

-Tim

---

### Post by cocotu on 2010-04-26
iissmart, thanks for your help. after running ifup eth1 the interface shows an IP address now:
> eth1      Link encap:Ethernet  HWaddr 00:0c:29:57:54:b7
          inet addr:192.168.248.101  Bcast:192.168.248.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe57:54b7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2623 (2.6 KB)  TX bytes:3615 (3.6 KB)
          Interrupt:18 Base address:0x2080
and i'm able to ping 192.168.248.1, which i could NOT before! this is starting to look good!!

---

### Post by cocotu on 2010-04-26
windependence, I will look into ESXi.  what would be the advantages? right now i don't think i have the choice of running another virtual sql server separate from the host. thanks for your help!
i still need to test if the linux server can access win 2003 server sql database.

---

### Post by spynappels on 2010-04-26
+1 for ESXi.
I have a bog standard ProLiant ML110 with 4 GB of RAM and 3 250GB HDDs with ESXi 4 on it. ESXi boots from a 4GB USB stick. I run an Asterisk (Test) PBX in one virtual machine, 3 development servers doing basic web serving and for Samba Labs as well as a dedicated OpenVPN server. No problem, and they are all sandboxed nicely.

ESXi is the interface between the virtual machines and the physical server. It takes some resources, but not nearly as many as a full blown Windows Server 2k3 install.

The major advantage is the lower overhead of resources so your VMs can use more, and ease of administration (from a Windows client unfortunately)

---

### Post by cocotu on 2010-04-26
I can ping the win server and the win server can ping the linux box. But i cannot access any resources on either of them: ssh, ftp, share folder, sql database.  is there anything else i need to configure to tell win and linux to use the ips: 192.168.248.1 and 192.168.248.101 to communicate?

---

### Post by windependence on 2010-04-28
Sounds like you have the firewall on. You need to turn the firewall off on the linux machine. Could also be SE Linux is blocking you. If you can ping the machine but can't access services on it, then the ports are probably closed for things like SSH and other services. If I were you, I would create another guest and run my SQL server on that guest instead of on the host. Running services on the host is just not a good way to do things. If a service gets hosed or runs out of control on your host machine, it would affect ALL of your guests since the host is running the guests. You may be able to use the free VMware converter to convert the host to another guest and then just uninstall Vmware on that guest so you can run your other services on the new guest. That would be quicker and easier than building a new SQL server, although I think if it was me I would build a fresh one just for the SQL server. With Ubuntu, if it's a LAMP server it's so easy to build another one with the LAMP stack already installed it should be child's play for you.

-Tim

---

