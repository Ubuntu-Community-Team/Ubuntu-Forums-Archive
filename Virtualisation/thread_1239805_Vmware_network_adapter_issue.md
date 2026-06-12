---
title: "Vmware network adapter issue"
date: 2009-08-13
forum: Virtualisation
---

### Post by ViPeRaY on 2009-08-13
Hey guys,

I am running vmware on Jaunty. I have a weird problem. If i run only one virtual machine (XP in this case) everything works fine. However when i start the second virtual machine (again XP), i cannot ping anywhere until i shut down the other virtual machine. 

So basically i can only use networking with only one virtual machine at a time.

Any ideas?

---

### Post by jocampo on 2009-08-14
> **ViPeRaY said:**
> Hey guys,

I am running vmware on Jaunty. I have a weird problem. If i run only one virtual machine (XP in this case) everything works fine. However when i start the second virtual machine (again XP), i cannot ping anywhere until i shut down the other virtual machine. 

So basically i can only use networking with only one virtual machine at a time.

Any ideas?

Are you using NAT or Bridged network? with NAT, you're basically using same host IP. With Bridged, your VM gets its own IP address so it can communicate with host and any other virtual machine.

Check, change to Bridged ... and let us know ...

---

### Post by ViPeRaY on 2009-08-14
I am using bridge and i have a dhcp in the network up and running fine.

---

### Post by jocampo on 2009-08-14
Can you please run 

```
ipconfig /all
```

on each one and post? also, check Event Viewer for possible errors and IP conflict and post the error (again, both virtual machines)

---

### Post by ViPeRaY on 2009-08-14
All the computers have valid ip addresses in the network and they can ping localhost. There is no ip conflicts. All of them were receiving ips from dhcp. Now i assigned static addresses.  They are all in the same subnet. It is like only one vm can use the network at a time. Please see below.

First Virtual Machine:
```

        Physical Address. . . . . . . . . : 00-0C-29-DE-B6-FD
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.5.51
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.5.1
        DNS Servers . . . . . . . . . . . : 192.168.5.1

C:\Documents and Settings\Administrator>ping google.com

Pinging google.com [74.125.45.100] with 32 bytes of data:

Reply from 74.125.45.100: bytes=32 time=34ms TTL=53
Reply from 74.125.45.100: bytes=32 time=35ms TTL=53
Reply from 74.125.45.100: bytes=32 time=34ms TTL=53
Reply from 74.125.45.100: bytes=32 time=34ms TTL=53

Ping statistics for 74.125.45.100:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 34ms, Maximum = 35ms, Average = 34ms

```Second Virtual Machine:
```

Ethernet adapter LAN:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : VMware Accelerated AMD PCNet Adapter

        Physical Address. . . . . . . . . : 00-0C-29-DE-B6-FD
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.5.52
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.5.1
        DNS Servers . . . . . . . . . . . : 192.168.5.1

C:\Documents and Settings\Administrator>ping google.com
Ping request could not find host google.com. Please check the name and try again
.


```

---

### Post by ViPeRaY on 2009-08-14
I am suspecting tx-checksumming is dropping the packages. I tried to disable it but cannot get it disabled.

I used the command below:

sudo ethtool -K tx off

---

### Post by dcstar on 2009-08-15
Just ping the local gateway address.

---

### Post by dcstar on 2009-08-15
> **ViPeRaY said:**
> All the computers have valid ip addresses in the network and they can ping localhost. There is no ip conflicts. All of them were receiving ips from dhcp. Now i assigned static addresses.  They are all in the same subnet. It is like only one vm can use the network at a time. Please see below.

**First Virtual Machine:**
```

        Physical Address. . . . . . . . . : **00-0C-29-DE-B6-FD**

```**Second Virtual Machine:**
```

Ethernet adapter LAN:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : VMware Accelerated AMD PCNet Adapter
        Physical Address. . . . . . . . . : **00-0C-29-DE-B6-FD**

```

Every VM I have has a different address and the networking works fine, just copying VMs is not a good thing to do.

---

### Post by jocampo on 2009-08-15
MAC address issue here, look

**00-0C-29-DE-B6-FD**

Every NIC in a network, must has its own MAC. If not, you will get issues; one of them will go down.

Did you used "cp" command for your vdi drive? use clone command or create the 2nd one from scratch ...

---

### Post by ViPeRaY on 2009-08-15
Yeah. I totally missed that. They have same mac addresses. Thanks for pointing that out. I have changed the mac addresses of the virtual machine's virtual network cards. Now they all have different mac addresses. 

That have solved the problem.

Thanks for the answers...

---

### Post by jocampo on 2009-08-15
> **ViPeRaY said:**
> Yeah. I totally missed that. They have same mac addresses. Thanks for pointing that out. I have changed the mac addresses of the virtual machine's virtual network cards. Now they all have different mac addresses. 

That have solved the problem.

Thanks for the answers...

That's why we are here and this forum is good for ;-) ... happy to know issue is fix. Maybe we can marked the trhead as solved..

Have fun!

---

