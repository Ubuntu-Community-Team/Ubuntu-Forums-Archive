---
title: "ISP blocks ports"
date: 2011-07-17
forum: Virtualisation
---

### Post by rafaelvidal on 2011-07-17
I have hosted a server and it's blocking SSH connections.

port: 22 blocked
      3306 blocked

Also many others services aren't working due the high security setted on it.

I have no idea on how to enable my services.

I tried to stop all firewalls, but something still blocking the services.


Virtual Machine OS: Debian Etch (4.0)
Host Machine: Windows Webserver 2008

---

### Post by CharlesA on 2011-07-18
Change it to a high numbered port and go to canyouseeme.org and see if it can see it.

Also check your port forwarding.

What VM software are you using? Is networking set to 'bridged' ?

---

### Post by rafaelvidal on 2011-07-18
I'm using VMware Workstation 7.1

I'm using NAT.
The host don't supports bridged network.

I tried to change the SSH to the port 25 and 3389 which are enabled...but still don't works...
2222 is blocked too

---

### Post by CharlesA on 2011-07-18
It doesn't support bridged?

If it's using NAT, you won't be able to connect host --> guest.

---

### Post by rafaelvidal on 2011-07-18
It uses NAT and I can connect through SSH, but only in the Host machine.

At my personal computer I can't, it says "connection refused".

---

### Post by psusi on 2011-07-18
Then disable the firewall on the host.

---

### Post by rafaelvidal on 2011-07-18
> **rafaelvidal said:**
> 
I tried to stop all firewalls, but something still blocking the services.

I closed all firewalls...but still can't connect through SSH.

---

### Post by CharlesA on 2011-07-18
> **rafaelvidal said:**
> I closed all firewalls...but still can't connect through SSH.

That's probably because you are using NAT.

You can configure bridged networking by following the instructions [here]("http://www.vmware.com/support/ws55/doc/ws_net_configurations_changing_bridged_windows.html").

---

### Post by rafaelvidal on 2011-07-18
I asked the Dedicated Host ([www.server4you.com](www.server4you.com)) today and they said the opposite.

They said I wasn't able to connect through SSH because I was probably using bridged, wich isn't supported.


Original Message: "Dear Rafael,

In that case I can only assume you elected to use bridged networking, which will not work here. You can only use a form of networking which can be routed (like HostOnly for VMWare, or NAT)."

So I'm using NAT...it should works.

Maybe watching the error personally you can help.
you can see by remote control. What you think?

---

### Post by psusi on 2011-07-18
If the VM is using NAT and not briding, then they have to explicitly configure the VM to forward specific ports to your guest.  They obviously can't do that for well known ports since they can only go to one machine.

---

### Post by rafaelvidal on 2011-07-18
so it's my dedicated host fault? they have to fix it for me?

---

### Post by rafaelvidal on 2011-07-18
Add: when I try to connect trhough SSH from my personal computer it says:
Network error: connection timed out.

---

### Post by psusi on 2011-07-18
What are you trying to connect to?  If your server is a guest in a vm that is using NAT and not briding, then the guest has a non routable IP address ( 192.168.x.x? ) which can not be seen by other hosts.  The only way to reach it is through the IP address of the host, which has to know it needs to forward the connection to your guest.

---

### Post by rafaelvidal on 2011-07-18
there are "two machines":
1- The host one with Windows Webserver 2008.
2- The virtual one with VMware and Debian Etch OS.

I want to connect through SSH on the VM one at my personal computer.
I'm using NAT.

---

### Post by psusi on 2011-07-19
Yes, and the problem is that based on what you say about the VM not supporting briding, #1 and #2 share a single IP address, so you can not connect to #2 without #1 being configured to forward the connection to #2.

---

### Post by rafaelvidal on 2011-07-19
Since it's NAT, it's working.
It has internet access and I can connect trhough SSH from the Host (Windows 2008 ) machine, but I can't do that from my personal computer.

---

### Post by psusi on 2011-07-19
Using what port and address?  As I said before, the guest is borrowing the host's IP address, so to reach the guest, the host must be configured to forward that port to the guest, and you must connect to the host's IP address.

---

### Post by rafaelvidal on 2011-07-19
192.168.91.128 Port: 22

by my personal computer it doesn't work.

I try the host IP
example:
188.16.163.14 Port: 22

---

### Post by psusi on 2011-07-19
> **rafaelvidal said:**
> 192.168.91.128 Port: 22

by my personal computer it doesn't work.

That is because 192.168.x.x addresses are local only addresses; they can not be accessed over the Internet.

> **rafaelvidal said:**
> I try the host IP
example:
188.16.163.14 Port: 22

That wasn't a complete sentence.  Did you try this?  Did it work?  If not, then your host is not configured to forward port 22 to your guest.  Presumably there are other guests that also want to use port 22, so this probably will not be possible, so you will have to have the host forward some other port instead.

---

### Post by doas777 on 2011-07-19
> **rafaelvidal said:**
> Since it's NAT, it's working.
It has internet access and I can connect trhough SSH from the Host (Windows 2008 ) machine, but I can't do that from my personal computer.
what we are trying to tell you, is that NAT won't work, unless you:
1) run your virtual service on a port that is not in use by the host (eg, since the host runs ssh on 22, you cannot use 22 on your guest).
2) you must forward the port on your VM nat to the guest:
(VirtualBox)
[http://www.aviransplace.com/2008/06/12/virtualbox-configuring-port-forwarding-with-nat/](http://www.aviransplace.com/2008/06/12/virtualbox-configuring-port-forwarding-with-nat/)
(VMWare)
[http://www.conetrix.com/Blog/post/Port-Forward-in-VMware-Workstation-when-using-NAT.aspx](http://www.conetrix.com/Blog/post/Port-Forward-in-VMware-Workstation-when-using-NAT.aspx)

---

### Post by rafaelvidal on 2011-07-19
doas...this way is hard to talk to you.

Can we talk at msn, gtalk or anything else?

Port 22 is not used by the host (windows webeserver 2008 ).
It's free.

---

### Post by psusi on 2011-07-19
Then the host needs to be configured to forward port 22 to your guest.

---

### Post by rafaelvidal on 2011-07-19
> **psusi said:**
> Then the host needs to be configured to forward port 22 to your guest.

I already did.

---

### Post by doas777 on 2011-07-19
ok, then we need some config info. from the guest run:
```

ifconfig -a
netstat -ntlup
sudo ufw status
route

```

from the host, run PowerShell as admin and run:
```

ipconfig /all
route print
netstat -abno | FINDSTR "LIST"
netsh firewall show

```
and post these back.

---

### Post by psusi on 2011-07-19
If you ssh to 188.16.163.14 on the host, are you connected to the guest?  If not then it seems your port forward is not set up correctly.

---

### Post by rafaelvidal on 2011-07-19
Here goes the asked information.
I don't have sudo installed, should I install?

[CENTER]**DEBIAN ETCH**[/CENTER]

**#ifconfig -a**
```
eth0      Link encap:Ethernet  HWaddr 00:0C:29:CB:BB:73
          inet addr:192.168.211.128  Bcast:192.168.211.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fecb:bb73/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:217975 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36777 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:174262386 (166.1 MiB)  TX bytes:2584142 (2.4 MiB)
          Interrupt:59 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:873 errors:0 dropped:0 overruns:0 frame:0
          TX packets:873 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:74169 (72.4 KiB)  TX bytes:74169 (72.4 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

**#netstat -ntlup**
```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN     4204/mysqld
tcp        0      0 192.168.211.128:53      0.0.0.0:*               LISTEN     3364/named
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN     3364/named
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN     3364/named
tcp6       0      0 :::53                   :::*                    LISTEN     3364/named
tcp6       0      0 :::22                   :::*                    LISTEN     3596/sshd
tcp6       0      0 ::1:953                 :::*                    LISTEN     3364/named
udp        0      0 0.0.0.0:32768           0.0.0.0:*                          3364/named
udp        0      0 192.168.211.128:53      0.0.0.0:*                          3364/named
udp        0      0 127.0.0.1:53            0.0.0.0:*                          3364/named
udp        0      0 0.0.0.0:68              0.0.0.0:*                          3262/dhclient3
udp6       0      0 :::32769                :::*                               3364/named
udp6       0      0 :::53                   :::*                               3364/named
```

**#route**
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.211.0   *               255.255.255.0   U     0      0        0 eth0
default         192.168.211.2   0.0.0.0         UG    0      0        0 eth0
```


[CENTER]**WINDOWS WEBSERVER 2008**[/CENTER]

**IPCONFIG /ALL**
```
   Host Name . . . . . . . . . . . . : luna531
   Primary Dns Suffix  . . . . . . . : startdedicated.com
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : startdedicated.com

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Broadcom NetLink (TM) Gigabit Ethernet
   Physical Address. . . . . . . . . : 00-19-99-A7-AD-7F
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv4 Address. . . . . . . . . . . : 85.25.100.203(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 85.25.100.1
   DNS Servers . . . . . . . . . . . : 85.25.128.10
                                       85.25.255.10
   NetBIOS over Tcpip. . . . . . . . : Enabled

Ethernet adapter VMware Network Adapter VMnet1:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : VMware Virtual Ethernet Adapter for VMnet1
   Physical Address. . . . . . . . . : 00-50-56-C0-00-01
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv4 Address. . . . . . . . . . . : 192.168.163.1(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . :
   NetBIOS over Tcpip. . . . . . . . : Enabled

Ethernet adapter VMware Network Adapter VMnet8:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : VMware Virtual Ethernet Adapter for VMnet8
   Physical Address. . . . . . . . . : 00-50-56-C0-00-08
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv4 Address. . . . . . . . . . . : 192.168.211.1(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . :
   NetBIOS over Tcpip. . . . . . . . : Enabled

```

**ROUTE PRINT**
```
===========================================================================
Interface List
 11...00 19 99 a7 ad 7f ......Broadcom NetLink (TM) Gigabit Ethernet
 17...00 50 56 c0 00 01 ......VMware Virtual Ethernet Adapter for VMnet1
 18...00 50 56 c0 00 08 ......VMware Virtual Ethernet Adapter for VMnet8
  1...........................Software Loopback Interface 1
===========================================================================

IPv4 Route Table
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0      85.25.100.1    85.25.100.203     21
      85.25.100.0    255.255.255.0         On-link     85.25.100.203    276
    85.25.100.203  255.255.255.255         On-link     85.25.100.203    276
    85.25.100.255  255.255.255.255         On-link     85.25.100.203    276
        127.0.0.0        255.0.0.0         On-link         127.0.0.1    306
        127.0.0.1  255.255.255.255         On-link         127.0.0.1    306
  127.255.255.255  255.255.255.255         On-link         127.0.0.1    306
    192.168.163.0    255.255.255.0         On-link     192.168.163.1    276
    192.168.163.1  255.255.255.255         On-link     192.168.163.1    276
  192.168.163.255  255.255.255.255         On-link     192.168.163.1    276
    192.168.211.0    255.255.255.0         On-link     192.168.211.1    276
    192.168.211.1  255.255.255.255         On-link     192.168.211.1    276
  192.168.211.255  255.255.255.255         On-link     192.168.211.1    276
        224.0.0.0        240.0.0.0         On-link         127.0.0.1    306
        224.0.0.0        240.0.0.0         On-link     85.25.100.203    276
        224.0.0.0        240.0.0.0         On-link     192.168.163.1    276
        224.0.0.0        240.0.0.0         On-link     192.168.211.1    276
  255.255.255.255  255.255.255.255         On-link         127.0.0.1    306
  255.255.255.255  255.255.255.255         On-link     85.25.100.203    276
  255.255.255.255  255.255.255.255         On-link     192.168.163.1    276
  255.255.255.255  255.255.255.255         On-link     192.168.211.1    276
===========================================================================
Persistent Routes:
  Network Address          Netmask  Gateway Address  Metric
          0.0.0.0          0.0.0.0      85.25.100.1       1
===========================================================================

IPv6 Route Table
===========================================================================
Active Routes:
 If Metric Network Destination      Gateway
  1    306 ::1/128                  On-link
  1    306 ff00::/8                 On-link
===========================================================================
Persistent Routes:
  None
```

**netstat -abno | FINDSTR "LISTS"**
```
TCP    0.0.0.0:25             0.0.0.0:0              LISTENING       1428
TCP    0.0.0.0:80             0.0.0.0:0              LISTENING       4
TCP    0.0.0.0:110            0.0.0.0:0              LISTENING       1408
TCP    0.0.0.0:135            0.0.0.0:0              LISTENING       648
TCP    0.0.0.0:143            0.0.0.0:0              LISTENING       1288
TCP    0.0.0.0:445            0.0.0.0:0              LISTENING       4
TCP    0.0.0.0:912            0.0.0.0:0              LISTENING       5368
TCP    0.0.0.0:1433           0.0.0.0:0              LISTENING       1696
TCP    0.0.0.0:2103           0.0.0.0:0              LISTENING       5144
TCP    0.0.0.0:2105           0.0.0.0:0              LISTENING       5144
TCP    0.0.0.0:2107           0.0.0.0:0              LISTENING       5144
TCP    0.0.0.0:3306           0.0.0.0:0              LISTENING       1156
TCP    0.0.0.0:3389           0.0.0.0:0              LISTENING       3236
TCP    0.0.0.0:8306           0.0.0.0:0              LISTENING       2356
TCP    0.0.0.0:8443           0.0.0.0:0              LISTENING       4
TCP    0.0.0.0:8880           0.0.0.0:0              LISTENING       4
TCP    0.0.0.0:47001          0.0.0.0:0              LISTENING       4
TCP    0.0.0.0:49152          0.0.0.0:0              LISTENING       372
TCP    0.0.0.0:49153          0.0.0.0:0              LISTENING       716
TCP    0.0.0.0:49154          0.0.0.0:0              LISTENING       792
TCP    0.0.0.0:49155          0.0.0.0:0              LISTENING       468
TCP    0.0.0.0:49157          0.0.0.0:0              LISTENING       460
TCP    0.0.0.0:49158          0.0.0.0:0              LISTENING       3272
TCP    0.0.0.0:49789          0.0.0.0:0              LISTENING       1544
TCP    0.0.0.0:50399          0.0.0.0:0              LISTENING       5144
TCP    85.25.100.203:53       0.0.0.0:0              LISTENING       1812
TCP    85.25.100.203:139      0.0.0.0:0              LISTENING       4
TCP    85.25.100.203:1801     0.0.0.0:0              LISTENING       5144
TCP    127.0.0.1:53           0.0.0.0:0              LISTENING       1812
TCP    127.0.0.1:953          0.0.0.0:0              LISTENING       1812
TCP    127.0.0.1:8106         0.0.0.0:0              LISTENING       2852
TCP    127.0.0.1:50797        0.0.0.0:0              LISTENING       1596
TCP    192.168.163.1:53       0.0.0.0:0              LISTENING       1812
TCP    192.168.163.1:139      0.0.0.0:0              LISTENING       4
TCP    192.168.163.1:1801     0.0.0.0:0              LISTENING       5144
TCP    192.168.211.1:53       0.0.0.0:0              LISTENING       1812
TCP    192.168.211.1:139      0.0.0.0:0              LISTENING       4
TCP    192.168.211.1:1801     0.0.0.0:0              LISTENING       5144
TCP    [::]:25                [::]:0                 LISTENING       1428
TCP    [::]:80                [::]:0                 LISTENING       4
TCP    [::]:110               [::]:0                 LISTENING       1408
TCP    [::]:135               [::]:0                 LISTENING       648
TCP    [::]:143               [::]:0                 LISTENING       1288
TCP    [::]:445               [::]:0                 LISTENING       4
TCP    [::]:1433              [::]:0                 LISTENING       1696
TCP    [::]:2103              [::]:0                 LISTENING       5144
TCP    [::]:2105              [::]:0                 LISTENING       5144
TCP    [::]:2107              [::]:0                 LISTENING       5144
TCP    [::]:3389              [::]:0                 LISTENING       3236
TCP    [::]:8443              [::]:0                 LISTENING       4
TCP    [::]:8880              [::]:0                 LISTENING       4
TCP    [::]:47001             [::]:0                 LISTENING       4
TCP    [::]:49152             [::]:0                 LISTENING       372
TCP    [::]:49153             [::]:0                 LISTENING       716
TCP    [::]:49154             [::]:0                 LISTENING       792
TCP    [::]:49155             [::]:0                 LISTENING       468
TCP    [::]:49157             [::]:0                 LISTENING       460
TCP    [::]:49158             [::]:0                 LISTENING       3272
TCP    [::]:49789             [::]:0                 LISTENING       1544
TCP    [::]:50399             [::]:0                 LISTENING       5144
TCP    [::1]:953              [::]:0                 LISTENING       1812
TCP    [::1]:1801             [::]:0                 LISTENING       5144
```

**NETSH FIREWALL SHOW**
```
The following commands are available:
```

---

### Post by doas777 on 2011-07-19
no, if you already have root powers, sudo is not needed. sorry, those instructions were more tailored to ubuntu or a sudoing distro. 

ok, nothing appears to be wrong, there, but we can dig deeper if needbe.

you said you could ssh in to the windows box, right?
there doesn't appear to be an ssh service on the windows box, so it does look like the port is being forwarded. if you can connect to ssh, that solves the issue, right?

if you don;t know which host you are remoted into, simply enter 
```
hostname
``` to see which one you are connected to.

when you are connecting to a NATted system, then you call the exterior address of the nat, rather than the local address of the guest machine.

---

### Post by CharlesA on 2011-07-19
> **doas777 said:**
> what we are trying to tell you, is that NAT won't work, unless you:
1) run your virtual service on a port that is not in use by the host (eg, since the host runs ssh on 22, you cannot use 22 on your guest).
2) you must forward the port on your VM nat to the guest:
(VirtualBox)
[http://www.aviransplace.com/2008/06/12/virtualbox-configuring-port-forwarding-with-nat/](http://www.aviransplace.com/2008/06/12/virtualbox-configuring-port-forwarding-with-nat/)
(VMWare)
[http://www.conetrix.com/Blog/post/Port-Forward-in-VMware-Workstation-when-using-NAT.aspx](http://www.conetrix.com/Blog/post/Port-Forward-in-VMware-Workstation-when-using-NAT.aspx)

Thanks for that, I didn't know you could do that.

> **rafaelvidal said:**
> Here goes the asked information.
I don't have sudo installed, should I install?


sudo is only used to run that command as root.

ufw is just a frontend for iptables so post this please (run it as root, if you need to):

```
iptables -L
```

---

### Post by rafaelvidal on 2011-07-19
> **doas777 said:**
> no, if you already have root powers, sudo is not needed. sorry, those instructions were more tailored to ubuntu or a sudoing distro. 

ok, nothing appears to be wrong, there, but we can dig deeper if needbe.

you said you could ssh in to the windows box, right?
there doesn't appear to be an ssh service on the windows box, so it does look like the port is being forwarded. if you can connect to ssh, that solves the issue, right?

if you don;t know which host you are remoted into, simply enter 
```
hostname
``` to see which one you are connected to.

when you are connecting to a NATted system, then you call the exterior address of the nat, rather than the local address of the guest machine.

From the dedicated server I can connect through SSH.

From my personal computer I can't...I want to connect from personal computer.

---

### Post by doas777 on 2011-07-19
> **rafaelvidal said:**
> From the dedicated server I can connect through SSH.

From my personal computer I can't...I want to connect from personal computer.
ok. what command are you using to ssh to the guest from within the host, exactly?

From the server, go to [http://www.canyouseeme.org/](http://www.canyouseeme.org/) and put in 22. can it see you?

if not, then your port forwarding is not working.

did you follow directions like these for forwarding the vmware nat to port 22?
[http://www.howtogeek.com/howto/vmware/allow-access-to-a-vmware-virtual-machinenat-from-another-computer/](http://www.howtogeek.com/howto/vmware/allow-access-to-a-vmware-virtual-machinenat-from-another-computer/)

---

### Post by rafaelvidal on 2011-07-19
I'm using putty.

I did the Port Forward thing.

open ports: 22, 3306, 9997, 9998, 9999.

---

### Post by doas777 on 2011-07-19
> **rafaelvidal said:**
> I'm using putty.
I just need to know which interface on the host server you are hitting to connect, the private (192.168.211.128 ) or the public (85.25.100.203). 

can you see 22 open on canyouseeme?

---

### Post by rafaelvidal on 2011-07-19
Inside the dedicated server (Windows Webserver 2008), I can connect trhough Putty on VM machine by the IP: 192.168.211.128.

From my personal computer I use the public IP and it says connection refused.

---

### Post by doas777 on 2011-07-19
if your port doesn't show up on canyouseeme, lets add an exception to the windows firewall for your application. 
[http://windows.microsoft.com/en-US/windows-vista/Open-a-port-in-Windows-Firewall](http://windows.microsoft.com/en-US/windows-vista/Open-a-port-in-Windows-Firewall)

---

### Post by doas777 on 2011-07-19
> **rafaelvidal said:**
> Inside the dedicated server (Windows Webserver 2008), I can connect trhough Putty on VM machine by the IP: 192.168.211.128.

From my personal computer I use the public IP and it says connection refused.
what does the server say if you use the public ip?

since you are using the internal IP, that means that the problem is in one of two places: in the windows network settings (firewall) or in the VMWare port forwarding.
allow ssh through the windows firewall, and then double check your port forwarding configuration. feel free to post screenshots.

---

### Post by rafaelvidal on 2011-07-20
the firewall is closed.
It shouldn't bore me, right?

---

### Post by CharlesA on 2011-07-20
> **rafaelvidal said:**
> the firewall is closed.
It shouldn't bore me, right?
Huh? That doesn't make any sense. Is the firewall on or off?

---

### Post by rafaelvidal on 2011-07-20
I say it's closed since the begining of this thread...
Since you always ask me if it's on or off, now I ASK if it would bore me even closed...

---

### Post by doas777 on 2011-07-20
> **rafaelvidal said:**
> I say it's closed since the begining of this thread...
Since you always ask me if it's on or off, now I ASK if it would bore me even closed...
It's teh word 'bore' that is confusing us. it has nothing to do with firewall ports. perhaps you mean 'block'? and yes, the windows firewall will block you. Try the instructions I linked a couple posts back to add an allow rule to windows firewall.

---

### Post by psusi on 2011-07-20
> **rafaelvidal said:**
> I'm using putty.

I did the Port Forward thing.

open ports: 22, 3306, 9997, 9998, 9999.

Port forwarding in putty forwards a port from your machine to the ssh server.  It has nothing to do with with forwarding from the host to the guest.  That is something that needs to be configured on the host.

---

### Post by doas777 on 2011-07-20
@Op:
Forward ports thought your nat as described here:
[http://www.howtogeek.com/howto/vmwar...ther-computer/]("http://www.howtogeek.com/howto/vmware/allow-access-to-a-vmware-virtual-machinenat-from-another-computer/")

and unblock your service in windows firewall as described here:
[http://windows.microsoft.com/en-US/w...ndows-Firewall]("http://windows.microsoft.com/en-US/windows-vista/Open-a-port-in-Windows-Firewall")

Until you do both of those things, we cannot be of any more help.

---

### Post by rafaelvidal on 2011-07-20
**#iptables -L**
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```


[B][center]Canyouseeme.org[/center]
Port 22 result:
[/B]Error: I could not see your service on 85.25.100.203 on port (22)
Reason: Connection refused

**[center]Firewall[/center]**
I enabled the desired ports on the firewall, additionally I **closed** all firewalls (to ensure that it isn't blocking me).

**VMware Workstation**
Enabled ports: 22, 3306, 9997, 9998, 9999.

---

### Post by doas777 on 2011-07-20
> **rafaelvidal said:**
> **#iptables -L**
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```
[B][CENTER]Canyouseeme.org[/CENTER]
Port 22 result:
[/B]Error: I could not see your service on 85.25.100.203 on port (22)
Reason: Connection refused

[B][CENTER]Firewall[/CENTER]
[/B]
I enabled the desired ports on the firewall, additionally I **closed** all firewalls (to ensure that it isn't blocking me).

**VMware Workstation**
Enabled ports: 22, 3306, 9997, 9998, 9999.

the problem is in the WINDOWS firewall, not the linux one. if it were a problem with the linux firewall, you would not be able to connect via putty using the private address.

---

### Post by rafaelvidal on 2011-07-20
that's my guess too...
But I can't find the issue.

I closed all firewalls...
There are three firewalls:
- Private Profile
- Public Profile
- Domain Profile

Them all are OFF.

Do you know Windows Webserver 2008? Maybe there is other block.

---

### Post by doas777 on 2011-07-20
> **rafaelvidal said:**
> that's my guess too...
But I can't find the issue.

I closed all firewalls...
There are three firewalls:
- Private Profile
- Public Profile
- Domain Profile

Them all are OFF.

Do you know Windows Webserver 2008? Maybe there is other block.
try making sure the windows firewall is enabled, but make a rule to allow ssh instead.
there are a number of things that don;t work right if you disabled teh windows firewall, like RDP.

---

### Post by rafaelvidal on 2011-07-20
I have inbound and outbund rules...where the port 22 should be setted? inbound?

---

### Post by doas777 on 2011-07-20
> **rafaelvidal said:**
> I have inbound and outbund rules...where the port 22 should be setted? inbound?
yup

---

### Post by rafaelvidal on 2011-07-20
> there are a number of things that don;t work right if you disabled teh windows firewall, like RDP.
Cool it does makes sense.

I enabled all firewalls and the error changed.

**Canyouseeme.org**
Error: I could not see your service on 85.25.100.203 on port (22)
**Reason: Connection timed out**
Before it was "refused", remember?

---

### Post by rafaelvidal on 2011-07-20
now it seems that it couldn't "reach" the virtual machine, right?

---

### Post by rafaelvidal on 2011-07-20
**#arp -an**
```
? (192.168.21.2) at <incomplete> on eth0
? (192.168.21.1) at 00:50:56:C0:00:08 [ether] on eth0
? (192.168.21.254) at 00:50:56:E8:17:E2 [ether] on eth0
```

**#route**
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.21.0    *               255.255.255.0   U     0      0        0 eth0
default         192.168.21.2    0.0.0.0         UG    0      0        0 eth0
```

Virtual Machine losts internet access...can you tell me why my virtual machine loses connection everytime??
In order to have internet back, I always have to go in:
**Manage Virtual Networks** and "Restore Default" configurations.


Also if I set static IP it doesn't work ([http://ubuntuforums.org/showthread.php?t=1803185](http://ubuntuforums.org/showthread.php?t=1803185) **<-- my first thread regarding no internet access)**.

---

### Post by doas777 on 2011-07-20
> **rafaelvidal said:**
> **#arp -an**
```
? (192.168.21.2) at <incomplete> on eth0
? (192.168.21.1) at 00:50:56:C0:00:08 [ether] on eth0
? (192.168.21.254) at 00:50:56:E8:17:E2 [ether] on eth0
```**#route**
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.21.0    *               255.255.255.0   U     0      0        0 eth0
default         192.168.21.2    0.0.0.0         UG    0      0        0 eth0
```Virtual Machine losts internet access...can you tell me why my virtual machine loses connection everytime??
In order to have internet back, I always have to go in:
**Manage Virtual Networks** and "Restore Default" configurations.


Also if I set static IP it doesn't work ([http://ubuntuforums.org/showthread.php?t=1803185](http://ubuntuforums.org/showthread.php?t=1803185) **<-- my first thread regarding no internet access)**.

I have no idea why you would need to reset your virtual network connection, but I would surmise that every time you do, you need to reapply your NAT port forwarding. 
do you think that is the issue?

---

### Post by rafaelvidal on 2011-07-20
everytime I restore to default the network configuration, I also re forward the ports.

---

### Post by doas777 on 2011-07-20
I'm starting to lean toward somthing being wrong with your vmware install. have you tried backing up your VM, and then uninstalling/reinstalling your VMWare (workstation\server ) instance on the host

---

### Post by rafaelvidal on 2011-07-20
yes, two times.

First I installed the latest version (7.1).

The second time I reinstalled the OS and after that I installed VMware 6.5.

---

### Post by rafaelvidal on 2011-07-20
doas, I was testing.

It seems that when I set the ports to be forwarded on VMware...then the internet stop to works. (I'm 99% sure)

What can cause that?

---

### Post by doas777 on 2011-07-21
not sure. on your guest, configure the port forwarding, and let the internet fail for a minute. 

then run:
```

sudo ifconfig -a
nslookup www.ubuntuforums.org
ping <host-public-ip>
ping 192.168.21.2 
```and we'll try to see what is wrong with the internet.

in your /etc/network/interfaces file, remove the lines for Network and Broadcast, and then restart networking
```
sudo /etc/init.d/networking restart
```also, what is in your /etc/resolv.conf file?

---

### Post by rafaelvidal on 2011-07-21
Here it goes...
I don't have nslookup command.
What's nslookup for Debian?
**#ifconfig -a**
```
eth0      Link encap:Ethernet  HWaddr 00:0C:29:49:B7:B4
          inet addr:192.168.222.3  Bcast:192.168.222.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe49:b7b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:85 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8865 (8.6 KiB)  TX bytes:10784 (10.5 KiB)
          Interrupt:59 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

**#ping 192.168.222.2**
```
PING 192.168.222.2 (192.168.222.2) 56(84) bytes of data.
64 bytes from 192.168.222.2: icmp_seq=1 ttl=128 time=2.91 ms
64 bytes from 192.168.222.2: icmp_seq=2 ttl=128 time=0.243 ms
arp -
--- 192.168.222.2 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1003ms
rtt min/avg/max/mdev = 0.243/1.577/2.912/1.335 ms
```

**#ping 85.25.100.203**
```
PING 85.25.100.203 (85.25.100.203) 56(84) bytes of data.
64 bytes from 85.25.100.203: icmp_seq=1 ttl=128 time=35.4 ms
64 bytes from 85.25.100.203: icmp_seq=2 ttl=128 time=3.77 ms
64 bytes from 85.25.100.203: icmp_seq=3 ttl=128 time=0.936 ms

--- 85.25.100.203 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2004ms
rtt min/avg/max/mdev = 0.936/13.394/35.473/15.655 ms
```

**#cat /etc/network/interfaces**
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#allow-hotplug eth0
#iface eth0 inet dhcp
auto eth0
iface eth0 inet static
address 192.168.222.3
netmask 255.255.255.0
gateway 192.168.222.2
```

**#cat /etc/resolv.conf**
```
search localdomain
nameserver 192.168.222.2
```

---

### Post by doas777 on 2011-07-21
well, on ubuntu anyway, the nslookup app is included in the [DNSUtils]("http://packages.ubuntu.com/lucid-updates/dnsutils") package

you can try 'dig <IPAddr>' instead. the only problem with dig, is that a success and a failure look a lot alike to those unfamilliar with the program. 

anyway, that output is very helpful. you appear to have a working internet connection on the guest, so I believe you cannot get DNS lookups. 

I notice that your resolv.conf points to your gateway IP for resolution. 
try replacing the nameserver address with the one your host is using, and save your resolv.conf. restart networking, and see if dig/nslookup start working again (or just try to browse-to\curl\wget a page).

---

### Post by rafaelvidal on 2011-07-21
I realized that I also don't have the dig command.

Well, doas, now I'm forwarding only the port 22 on VMware.
In this way I still have internet access and SSH connections are enabled

Like I said before, when I was forwarding ports, for some reason the internet access was being lost.
Now that I left only one port both things are working (internet and SSH).

Anyway I need to forward more ports.
Like: 3306, 9997, 9998 and 9999.

When I forward port 3306, then I lose internet again.

---

### Post by rafaelvidal on 2011-07-21
I just added the 999x ports together with the 22 one and all seems to be working fine.

I'll test 3306 together now.


EDIT: I bought this dedicated server and it comes with some features (Plesk, MYSQL DB, etc). These features are all enabled.
Since I just disabled them, maybe this is the reason that everything is working now...I'm not sure...I'm not a specialist...
In really I'm just learning.

Now it's working...
I'm scarry to restart the computer and everything stop to works again.

So I'm not sure what is going on...

I'm saying many things...I'm quite confused.
I'll try to figure out what is happening.

Just to be clear: **everything seems to be working now.**

---

### Post by doas777 on 2011-07-22
Wonderful; glad you got it working.

so, it seems to me like the vmnet networking is flaky when adding nat rules. hopefully it remains fixed.

Good luck and have fun

---

### Post by rafaelvidal on 2011-10-27
Well, it happened again.

I did restarted the computer today and now I lost internet access on VM...

When I forward the ports i lost internet.



ANY CLUES?

---

### Post by CharlesA on 2011-10-27
No idea.

It makes no sense to me.

---

### Post by rafaelvidal on 2011-10-27
Since the problem is when a port is forwarded, then I guess it has some kind of conflict...

Maybe some service is using the forwarded port and then connection goes down.

---

### Post by CharlesA on 2011-10-27
Maybe.

Did you already try what got it working earlier?

---

### Post by rafaelvidal on 2011-10-27
Well...I really don't know what to say...

I'm very lost.

I just setted system to DHCP and now I'm restoring default confs on VM.
I already did the previous step before, so I can say it will works.

The problem will be when I forward ports based on the provided IP.

---

### Post by CharlesA on 2011-10-27
> **rafaelvidal said:**
> Well...I really don't know what to say...

I'm very lost.

I just setted system to DHCP and now I'm restoring default confs on VM.
I already did the previous step before, so I can say it will works.

The problem will be when I forward ports based on the provided IP.
Same. I don't have any experience with a network setup like the one you are using, so I can't really offer any more ideas - since I have none left.

---

### Post by rafaelvidal on 2011-10-27
Hey.

I found out.

I use NAT connection.
So I must forward some ports for my application to works.
The ports are these: **9997, 9998, 9999, 3306 and 22**(just for ssh).

Currently 2 ports are running with success: **9997 and 22**.

When I try to forward any other (9998, 9999 or 3306), then I lose internet access.

What could make it happens?

---

