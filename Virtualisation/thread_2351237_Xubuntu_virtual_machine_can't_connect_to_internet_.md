---
title: "Xubuntu virtual machine can't connect to internet on bridget connection"
date: 2017-02-01
forum: Virtualisation
---

### Post by peter1897 on 2017-02-01
I have xubuntu vrtualbox guest machine and windows 7 host. The guest machine can't connect to internet when the network adapter is 'bridget connection'. I can ping the guest from the host and i can ping the host from the guest, but i am unable to ping the router from the guest. 

This is the ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 08:00:27:a2:f3:17  
          inet addr:192.168.31.154  Bcast:192.168.31.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fea2:f317/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:126 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2443 (2.4 KB)  TX bytes:15316 (15.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:256 errors:0 dropped:0 overruns:0 frame:0
          TX packets:256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:19292 (19.2 KB)  TX bytes:19292 (19.2 KB)


```

Any idea what might be the problem?

---

### Post by ajgreeny on 2017-02-01
The router obviously sees the guest and gives it an IP which is showing in the ifconfig output as 192.168.31.154 so it seems a bit strange that you can not ping the router from the guest.

Just out of interest, can you ping the router and connect to the network and internet if you use the NAT network connection in your guest settings?
What happens if you try pinging an outside site such as 8.8.8.8 from the bridged and NAT networked guest; will either of those work?

---

### Post by peter1897 on 2017-02-01
With NAT adapter i can ping the router and outside ip addresses but with bridget connection i can't.

---

### Post by The Cog on 2017-02-01
Let's try the next step. After trying and failing to ping the router, can you try this command and post the result please:
```
arp -an
```

EDIT:
Can you also confirm that the router address and your host windows address are both 192.168.31.something?

---

### Post by peter1897 on 2017-02-01
This is the output of apr -an:
```
? (192.168.31.101) at 8c:70:5a:99:04:90 [ether] on eth0
? (192.168.31.1) at <incomplete> on eth0

```

My router address is 192.168.31.1
```
$ ipconfig

Windows IP Configuration


Ethernet adapter Local Area Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::fc67:4ded:1a7:e193%13
   IPv4 Address. . . . . . . . . . . : 192.168.31.101
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.31.1

Ethernet adapter Bluetooth Network Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Ethernet adapter VirtualBox Host-Only Network:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::b8c2:66d7:cf83:5a66%14
   IPv4 Address. . . . . . . . . . . : 192.168.56.1
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . :

Tunnel adapter isatap.{304028A7-D8F6-48B2-BF58-6B9CF4D6478A}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter isatap.{A7B52224-F8A5-4251-8C98-9CA62741E34E}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter isatap.{CC5DAE69-A17D-4C80-9086-73DBF62DB766}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter isatap.{D353B4BD-A5ED-46CB-ACB9-9899FDBB6096}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :


```

---

### Post by ajgreeny on 2017-02-01
I think the problem must be related to the line **? (192.168.31.1) at <incomplete> on eth0** in your **arp -an** output, which, if that is your router IP, shows no hardware address.

Very strange, but I will leave you in the good hands of my colleague The Cog who knows more about this than I do..

---

### Post by The Cog on 2017-02-01
> ...The Cog who knows more about this than I do..
Ha! I wish I did. 
The incomplete ARP entry suggests that it's not an IP firewalling issue. It's something more fundamental.

What I can't understand is that the guest seems to have been able to get a valid IP address. 
Have you configured the guest address manually, or is it being allocated automatically (by DHCP)? I'm wondering if the guest address has been manually configured and matches another machine already on the network.

It may be worth running tcpdump for a while and wait and see what packets the guest receives from outside. 
```
sudo tcpdump -ne
```
Also try the ping for 2-3 seconds in another window while tcpdump is running. Run tcpdump for a minute, or until you get 20 packets. Post the results and we might see something that gives us a clue.

---

### Post by peter1897 on 2017-02-01
No, the ip address of the guest machine is not configured manually:
```
osboxes@osboxes:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


```

I attached two files with tcpdump output - one without pinging, and one while pinging the router:
[ATTACH]273475[/ATTACH]

---

### Post by The Cog on 2017-02-01
That's really odd.
I can see in the ping trace:

**packet 1** is a ping request from 192.168.31.154 > 192.168.31.1, MAC addresses 08:00:27:a2:f3:17 > 00:16:0a:22:40:f8.
The source MAC and IP addresses agree with ifconfig from the guest.
The destination IP address is that of the router, and destination MAC address  of the router is 00:16:0a:22:40:f8.

This conflicts with the output of **arp -n** that says it can't figure out the MAC address of the router. It's sending the request to the correct MAC address. I don't understand why arp -n doesn't show the MAC address that it clearly knows. Odd.

**Packet 2** shows the router responds to the ping request with an ARP request asking what the MAC address of the guest is. The source MAC address is the same as the destination in packet 1. This proves that packet 1 had the correct destination MAC address for the router, and that the ping request reached the router.

**Packet 3** shows the guest responding to the ARP request. I guess this doesn't reach the router for some reason because every time it gets another ping request the router asks for the MAC address again instead of sending the ping reply.

I am wondering if the guest ARP reply isn't reaching the router because of some peculiarity of the wireless connection - maybe the wireless access point doesn't like its clients claiming to have multiple MAC addresses. Or perhaps something in the wireless driver is blocking the extra outgoing ARP response.

Sorry, but I don't know what to do from here. 
Perhaps try a cabled connection instead of wireless?

---

### Post by peter1897 on 2017-02-02
OK, thanks for the help. By the way, i have this problem with any virtual machine. If i set bridged connection they can't connect to internet.

---

### Post by ajgreeny on 2017-02-02
The next question is, I suppose, why do you need to use bridged connection?

You seem to have a successful NAT connection working so why not use that, or can you still not connect to the internet, even though you can ping the router and external IPs?  

If that's the case it might point to a DNS problem.

Baffling!

---

### Post by Irihapeti on 2017-02-02
Something that might be relevant:

Which network adapter type are you using in the guest?

Assuming that the Windows host interface is the same as the Linux one, that would be found under Advanced in the Network portion of the Settings window.

The default is Intel Pro/1000 MT Desktop. This for some reason does not work with bridged connections. Change it to PCnet-FAST III.

I've had several *buntu VMs work successfully in bridged mode with this setting. I'm using a Linux host, but I don't believe it makes a huge difference.

---

### Post by peter1897 on 2017-02-02
@Irihapeti I tried with PCnet-FAST III but still no internet.

@ajgreeny I want to setup bridged connection because i want to connect over ssh to the guest machine from other devices on the LAN network.

I think that is a problem with virtualbox itself. Some pc hardware doesn't support bridged connection on wireless networks. That is the answer that i got from virtaulbox developers. I should probably try VMware.

---

### Post by efflandt on 2017-02-04
There is nothing inherently wrong with bridging in virtualbox, and least not with a Linux host.

After I ping my router from 32-bit Ubuntu 16.04 virtualbox guest using bridging with dynamic IP, the router lists it as:
172.16.0.145 78:e4:00:26:b8:ac on Wireless static

After I ping my router from 64-bit 16.10 static IP host, that same line is listed as:
172.16.0.55 78:e4:00:26:b8:ac on Wireless static

I don't know if it matters for bridging, but do you have guest additions installed in the guest?

One curiosity is what this interface is on a different subnet from your LAN? I wonder what that is for (could Windows itself be doing NAT which is not what your guest is expecting)```
Ethernet adapter VirtualBox Host-Only Network:

      Connection-specific DNS Suffix  . :
      Link-local IPv6 Address . . . . . : fe80::b8c2:66d7:cf83:5a66%14
    IPv4 Address. . . . . . . . . . . : 192.168.56.1
    Subnet Mask . . . . . . . . . . . : 255.255.255.0
    Default Gateway . . . . . . . . . :
```PS: I think I may have stumbled on something, not sure if it will help you or not. My guest system got notification of updates that amounted to 11 MB. When I tried to do the updates it downloaded some and then said it could not finish, check your Internet connection. I tried again and same thing. I was streaming Internet radio on the host, turned that off, then Software Updater found over 100 MB or updates which it downloaded and installed without any problems, including updates for Firefox, Oracle Java, etc. So if the host is doing something on the network on one IP and the bridged guest is trying to use the network simultaneously on a different IP on same MAC address, maybe that can confuse a wireless router or gateway. And Windows is constantly broadcasting for other Windows computers, along with automatic updates and other programs updating themselves. So vbox bridging may work best if you have a network quiet host OS. That is not a problem when using NAT because everything comes in on the same host IP.

---

### Post by peter1897 on 2017-02-05
Yes, i have guest additions installed and the host only network is for another virtual machine. I don't think a program on my host that using the internet is the problem, i even uninstalled comodo firewall which i have installed on my host but still can't use bridged connection.

---

### Post by itcrowdsource on 2017-02-07
What kind of nic are you using on the Win7 host?

---

### Post by subach-pavel on 2017-12-09
> **Irihapeti said:**
> Something that might be relevant:

Which network adapter type are you using in the guest?

Assuming that the Windows host interface is the same as the Linux one, that would be found under Advanced in the Network portion of the Settings window.

The default is Intel Pro/1000 MT Desktop. This for some reason does not work with bridged connections. Change it to PCnet-FAST III.

I've had several *buntu VMs work successfully in bridged mode with this setting. I'm using a Linux host, but I don't believe it makes a huge difference.

Hmm, but I have two VM with Debian 8.0 and This adapters perfect work with Bridged network :(

---

### Post by coffeecat on 2017-12-09
Back to sleep, old thread.

---

