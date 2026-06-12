---
title: "server acting as a gateway"
date: 2006-10-29
forum: Server Platforms
---

### Post by sim-x on 2006-10-29
Hello Everyone.

I live in a house that has many computers hooked up to a switch. We have one internet line.

One of those computers is my ubuntu server box.

I can't keep my machine on for long since the other computers (windows boxes) think my ip is the network gateway, i.e. when they try connecting to the web, windows assigns my server's ip as the gateway. 

All they have to do is repair their internet connections and then they can connect fine, but why is my box simulating a gateway? How do I make it stop?

Thanks,

sim-x
Seattle, WA

---

### Post by sim-x on 2006-10-30
No one has any idea???

---

### Post by bmillsap on 2006-10-30
What's assigning IP addresses to each of your machines?  Do you have a router on your network acting as a DHCP server?

---

### Post by FeraTech on 2006-10-30
You need a router or have your server act as the router. If you don't have one you can only have 1 computer at a time access the internet. 

I would recommend adding another network card to your server. Hook up the modem to one card. Hook up the other card to the switch on which all the other PCs are connected to. This will allow all your PCs to run without needed to repair the connection every time.

It seems like your modem is the only thing assigning IPs and it can only do that 1 computer at a time.

---

### Post by sim-x on 2006-10-30
Thanks guys,

Yes, our house has a router on the network acting as a DHCP server. All the other machines (windows boxes) are set to dhcp, only the linux server has a static ip. 

That's what i don't understand.. why do the windows machines see my linux's ip as their gateway? The reason I thought was that somehow my linux box was emitting "gateway pheromones" or something, but perhaps its not that?

---

### Post by bmillsap on 2006-10-30
So your DHCP server is set to pass one IP address as the default gateway, but your Windows machines are picking up something else?  That sounds odd.  First, can you confirm the gateway that your DHCP server is passing is NOT the IP of your linux box?  Then, if you look at the network connection status in Windows, confirm that the DHCP server that issued the lease is in fact your router?  Is it possible that your linux box is configured to also be a DHCP server and is instead what's giving the leases to the Windows machines?

---

### Post by sim-x on 2006-10-30
Thanks bmillsap,

Ok i'm going to try and answer your questions:

Q: can you confirm the gateway that your DHCP server is passing is NOT the IP of your linux box?
A: All the windows machines have to do to reset their ip to the correct on is use the "repair" option under windows and then they can connect fine, so i'm pretty sure the DHCP server is passing the correct gateway..

Q:if you look at the network connection status in Windows, confirm that the DHCP server that issued the lease is in fact your router?
A:that would great to test, how do i do that?

Q:Is it possible that your linux box is configured to also be a DHCP server and is instead what's giving the leases to the Windows machines?
A: I doubt that very much, but how do I check?

Thanks for help

---

### Post by bmillsap on 2006-10-30
Before you repair the connection, right click on the network icon in the system tray (the picture of two computers with flashiing screens), and pick Status|Support|Details, and you should get a list of info about the connection including the gateway address and the IP of the DHCP server that issued the lease.  It would be intersting to see what these look like before and after you "repair" it.

---

### Post by sim-x on 2006-10-31
Thanks, I'll check that.

Also, how do I check whether or not my linux box is configured to also be a DHCP server and that it is he who is instead what's giving the leases to the Windows machines?

---

### Post by sim-x on 2006-10-31
by the way, I do NOT have dhcp3-server installed...

---

### Post by bmillsap on 2006-10-31
The information you get off the Windows machine when it doesn't work and then when it works will tell you the IP address of the DHCP server that it used.

---

### Post by dannyboy79 on 2006-10-31
do you have the switch installed before or after the router? this problem sounds very strange as bmillsap is stating and I would be very interested in learning what is causing this!!! something sounds very fishy and I am sure it's not your fault but there is something that we are not being informed of.

---

### Post by jimm on 2006-10-31
Hi,

It couldn't be that your static IP address and the linux box is the same as the gateway address? So when the windows machines fire up they get the gateway address which is actually the static address of your server?

Can you do an: **ipconfig /ALL** on one of the pre-"repaired" Windows machines and post the results, then do the same after you "repair" the connection.

Also do an: **ifconfig** on your linux box and post those results as well as the output of the **route** command. 

You could also post something like the output of a **tracert** command on windows so we could see where the traffic is going.

Perhaps then we can get a better idea of your config and work towards a solution. 

Thanks,
James

---

### Post by sim-x on 2006-11-01
Thanks so much guys, I'll try and get that information to you in the next few days.

---

### Post by sim-x on 2006-11-01
Hello Fellas,

Ok, it turns out my windows box was not connecting to the web so I was able to get some information. 

I have VMware player on the windows box, but it was not initialized during those tests.

Also, the server has port 22 and 80 open in the firewall (if that's important...)

Here is what you asked for:

********************************************
ipconfig /all BEFORE repair:

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Sanjoy>ipconfig

Windows IP Configuration


Ethernet adapter VMware Network Adapter VMnet8:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.126.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

Ethernet adapter VMware Network Adapter VMnet1:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.62.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : localnet
        IP Address. . . . . . . . . . . . : 192.168.1.110
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.114

C:\Documents and Settings\Sanjoy>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : Simcom
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Hybrid
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : localnet

Ethernet adapter VMware Network Adapter VMnet8:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : VMware Virtual Ethernet Adapter for
VMnet8
        Physical Address. . . . . . . . . : 00-50-56-C0-00-08
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.126.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

Ethernet adapter VMware Network Adapter VMnet1:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : VMware Virtual Ethernet Adapter for
VMnet1
        Physical Address. . . . . . . . . : 00-50-56-C0-00-01
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.62.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : localnet
        Description . . . . . . . . . . . : Intel(R) PRO/1000 PL Network Connect
ion
        Physical Address. . . . . . . . . : 00-12-3F-7A-0E-2C
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.110
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.114
        DHCP Server . . . . . . . . . . . : 192.168.1.114
        DNS Servers . . . . . . . . . . . : 192.168.1.114
        Lease Obtained. . . . . . . . . . : Wednesday, November 01, 2006 5:47:25
 PM
        Lease Expires . . . . . . . . . . : Thursday, November 02, 2006 5:47:25
AM

C:\Documents and Settings\Sanjoy>

********************************************

ipconfig /all AFTER repair

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Sanjoy>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : Simcom
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Hybrid
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : localnet

Ethernet adapter VMware Network Adapter VMnet8:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : VMware Virtual Ethernet Adapter for
VMnet8
        Physical Address. . . . . . . . . : 00-50-56-C0-00-08
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.126.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

Ethernet adapter VMware Network Adapter VMnet1:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : VMware Virtual Ethernet Adapter for
VMnet1
        Physical Address. . . . . . . . . : 00-50-56-C0-00-01
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.62.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : localnet
        Description . . . . . . . . . . . : Intel(R) PRO/1000 PL Network Connect
ion
        Physical Address. . . . . . . . . : 00-12-3F-7A-0E-2C
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.110
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 4.2.2.2
                                            4.2.2.3
        Lease Obtained. . . . . . . . . . : Wednesday, November 01, 2006 5:55:55
 PM
        Lease Expires . . . . . . . . . . : Thursday, November 02, 2006 5:47:27
PM

C:\Documents and Settings\Sanjoy>
********************************************
ifconfig on the linux box:

sanjoy@astro:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:A0:CC:22:5E:28
          inet addr:192.168.1.114  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:ccff:fe22:5e28/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27567 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9724 errors:0 dropped:0 overruns:0 carrier:0
          collisions:49 txqueuelen:1000
          RX bytes:8069916 (7.6 MiB)  TX bytes:930153 (908.3 KiB)
          Interrupt:11 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sanjoy@astro:~$
*****************************************************
route on the linux box:
sanjoy@astro:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
*****************************************************
tracert on windows:

C:\Documents and Settings\Sanjoy>tracert 192.168.1.114

Tracing route to 192.168.1.114 over a maximum of 30 hops

  1     1 ms    <1 ms    <1 ms  192.168.1.114

Trace complete.

C:\Documents and Settings\Sanjoy>
********************************************


So I was able to tell that my server is the one handing out the gateway..WTF?

Thanks for your help!

---

### Post by sim-x on 2006-11-01
And this is my /etc/network/interfaces  file FYI:


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
        address 192.168.1.114
        gateway 192.168.1.1
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.169.1.255

---

### Post by sim-x on 2006-11-03
Does any of this info help elucidate what the problem is?

---

### Post by bmillsap on 2006-11-03
Well, from the one post above, it certainly appears that your Ubuntu machine (that's at 192.168.1.114, right?) is handing out an IP address to your Windows machine, and passing itself as the DNS server and gateway.  Are you sure it's not running a DHCP server?  I don't know how this could happen if it's not.

---

### Post by jjross on 2006-11-04
have you tried to set the dhcp range in your router (ie: 192.168.1.100 - 192.168.1.110)  and then set your static ip address for the ubuntu machine outside of that range, that way dhcp should not look outside of the range set for an ip address

---

### Post by sim-x on 2006-11-09
Thanks so much for a stimulating conversation guys. Bmillsap, your post gave me the clue I needed! I found this tiny package called dnsmasq that was causing all my problems!! I removed it and presto! I'm not ruining my housemates' internet access anymore :)

Thanks again,

sim-x

---

