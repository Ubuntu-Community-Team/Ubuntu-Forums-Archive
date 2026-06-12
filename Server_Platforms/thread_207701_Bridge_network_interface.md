---
title: "Bridge network interface"
date: 2006-07-02
forum: Server Platforms
---

### Post by lvanderree on 2006-07-02
Hello all,

I have Ubuntu 6.06 now running on my server for some months and the only really big problem I encountered and still having problems with is with my bridge setup.

First I found it difficult to use the bridge tools correctly. I still don't know what the differences are between my initial setup of /etc/network/interfaces and the one I have now, but for some reason it first have to work magically one time, after which my setup does stay working. But why it didn't work out with my (as far as I know) identical setup is still a mystery to me.

Also during booting, my server still halts for a minute when it is starting the network interfaces, probably because of an error somewhere (in my configuration or in my network, or in a combination of the network-hardware and the drivers I assume).

**Problem:**
So although my current setup does work, I keep getting these strange messages once in a while:

```

Jul  2 14:19:05 server kernel: [18360271.280000] br0: port 1(eth1) entering disabled state
Jul  2 14:20:05 server kernel: [18360331.280000] br0: port 1(eth1) entering learning state
Jul  2 14:20:20 server kernel: [18360346.280000] br0: topology change detected, propagating
Jul  2 14:20:20 server kernel: [18360346.280000] br0: port 1(eth1) entering forwarding state

```

The network cables never get disconnected and my eth1 is connected to a switch which is always on, so I really don't see why this happens.

Because of this problem, the network is down for a minute. And because I have the Windows "My Music"-folder stored on my server (sharing it with samba) iTunes can't save it's database file properly at these moments, causing all my music to stop, the iTunes database to get corrupted, and Windows reporting write-error reports.
Also because the server is completely unreachable, my web-server is not reachable from the Internet and no new mail can arrive.

**Question:**
Can someone tell me what can cause this problem, and what I can do to resolve it. Or does someone know how to change the restore time, because the one minute precisely between the disabled state and the learning state should be defined somewhere, if you ask me.

I now have the following lines for my bridge in my interfaces file:

```


auto br0
iface br0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        dns-nameservers 192.168.0.1
        bridge_ports eth1 eth2


```
*which I think is pretty nice, letting the bridge-tools do all the work for me.*

I have eth1 and eth2, because after a couple of months I have replaced eth0, to see if this caused my problems, but this also doesn't seem to make any difference.

---

### Post by Randomskk on 2006-07-02
Why do you need a bridge?
If you're just trying to get packets to go in one interface and out the other, do this as root (sudo -i):
```
echo 1 > /proc/sys/net/ipv4/ip_forward
```

Any packets not addressed to the server will then get sent on to their destination, just ensure the devices sending to it use it as the default gateway.

---

### Post by lvanderree on 2006-07-02
Woo, thanks for the fast response!

I can definitely try this, but I liked the bridge solution, because both interfaces then have the same IP-address.

Using your solution both interfaces would have to have there own address, isn't insuperable, so if no other solutions come up, I will definitely try this.

---

### Post by mips on 2006-07-02
This might sound like a stupid question but why do you require bridging ?

As far as my knowledge goes bridging is a layer2 function and does not require any layer3 protocols like tcp/ip ?

---

### Post by Randomskk on 2006-07-02
I don't see why using the ip_forward thing disallows having the same IP on each interface, but I've never tried.
What's your network like? What two things are the server bridging, etc?

---

### Post by mips on 2006-07-02
[QUOTE=Randomskk]I don't see why using the ip_forward thing disallows having the same IP on each interface, but I've never tried.[/QUOTE]

That is a definate no-no.

---

### Post by lvanderree on 2006-07-02
Well let me explain my setup.

I have an Internet connection, using an ADSL router-modem. This is connected to my switch, where also all my other workstations (windows and Linux), the server and a WIFI-accesspoint are connected to.

But because I haven't got room for cables through the walls everywhere, there is one (Linux) workstation which is directly connected to the second interface of my server. My server is also a DHCP server, but my modem is a router, because of the lack of space for more cables. Otherwise I would have connected the modem directly to an interface on my server.

So to give a schematic idea:

```

Internet -- ADSL-modem -- Switch -- Server -- linux-workstation
                           |
         workstation   -------   workstation
                           |
         workstation   -------   workstation
                           |
                  WIFI-Accesspoint

```

It of course would be nicer if the Linux-workstation could also be connected to the switch, but this is physically impossible. The Bridge method worked out fine, except for the occasional drop of the entire bridge connection on the server.

I just tried the solution of removing the bridge and restoring two eth interfaces, but this didn't work out.

I had the folowing interfaces file:
```

auto eth1
iface eth1 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        dns-nameservers 192.168.0.1

auto eth2
iface eth2 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255

```

And while this worked out OK for all my workstations connected to the switch, my Linux-workstation wasn't be able to even ping my server at 192.168.0.100

So I changed to IP address of eth2 to 192.168.0.101 but I still couldn't ping my server from my Linux-workstation; not on 192.168.0.101 or on 192.168.0.100

After that I changed the IP of eth2 on my server to 192.168.1.100 and this gave me some better results.
I was now able to ping my server from my Linux-workstation (of course after changing its IP-address) on both 192.168.1.100 and 192.168.0.100
but I couldn't get any further. So I wasn't able to ping my modem-router on 192.168.0.1 let alone ping something like [www.google.com](www.google.com)

I assume I have to use some router functions on my server on this, and that is not what I want. I want to have one transparent network and this is what the bridge functions where doing for me (except for that tiny little problem showing up once in a while).

I'm no guru on this either (obviously), but my understanding of a bridge is exactly as I'm using it for; connecting to networks with each other transparently as one big network.
So on both sides the interfaces would have the same network (192.168.0.x in my case) and both sides can reach each other as if there is nothing in between (like the server in my case).

As far as I can see now, I'm still correct, because it did worked out (except for that little error once in a while) with the bridge functions and without the bridge function nothing is working anymore, unless I create two separate networks (with on one side 192.168.x.z and on the other 192.168.y.z) and a router to join these two networks. A router in between is not what I want, because I then can't connect from all my workstations to the others anymore (unless I configure my router, but that would be strange if there is something like a bridge which does exactly what I want).

---

### Post by Randomskk on 2006-07-02
Yea, I guess a bridge is what you want, and I can't say I know why it would drop now and again.
My best guess as to why the interface is dropping is some script that's putting it down then up again, or similar, do you have any programs that might do this on the server? :/

---

### Post by mips on 2006-07-02
If I was you I would do this:

```

Internet -- ADSL-modem -- Server -- Switch --  linux-workstation
                                      |
                     workstation   -------   workstation
                                      |
                     workstation   -------   workstation
                                      |
                              WIFI-Accesspoint

```

Configure the 'server' to do DHCP/NAT/DNS/Routing/Firewall. Your server would be connected to two networks but all your workstations/wireless will be on the same network. This could also improve your security.

Look at:
[http://www.ubuntuforums.org/showthread.php?t=111972](http://www.ubuntuforums.org/showthread.php?t=111972)

---

### Post by lvanderree on 2006-07-02
I'm not aware of any scripts that are reconfiguring my network interfaces. I've only installed applications from the Ubuntu repositories and nothing extraordinary (as far as I know). But maybe there is an application that is reconfiguring my network setup.

What I think is that once in a while a package over the network is confusing the bridge-software. This comes to light when I'm using iTunes, because the down-time of the network causes my music to stop playing, after which iTunes comes into problems, because it can't write it's database back to the network-drive. After the network has been (automatically) restored after a minute the file which iTunes uses for its database is still in use, while iTunes can't open it anymore. 

I know the solution you describe (mips) would be optimal, not only for security, but I then also don't need any bridge tools. 
Unfortunately this isn't possible at the moment, because of the physical location of the server and the room for network cables through the walls, but I think I might can find a new location for the server solving this problem. Which is probably easier then looking for a solution to this problem.

But if someone knows where I can change the time-out value I would love to here from you.

---

### Post by houstonbofh on 2006-07-03
First let me start by saying I never got this to work.  I tried for several days, before I bought some additional hardware.  It just never worked right.  Buy a cheap hub and set it behind the server.

The Bridge tools have a learning faze to account for switch loops.  You may be bumping into this...  It can be disabled in the startup script.

---

