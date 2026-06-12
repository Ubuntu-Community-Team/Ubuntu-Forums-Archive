---
title: "Ubuntu Server Periodically Goes Offline"
date: 2010-04-02
forum: Server Platforms
---

### Post by The Titan on 2010-04-02
I just set up a server using Ubuntu Server 9.10. I am running Apache2, MySQL, OpenSSH, and Samba.

I have 2 Windows XP computers and the server on the network. My router is a Lynksys BEFSX41.

I have set all of the computers on the network to static IP addresses and turned DHCP off on my router. 

The problem is that periodically the server just drops off the network, PuTTTy closes and the web server is inaccessible. Sometimes I just wait a moment and the server comes back online, other times I wait a few minutes and I end up restarting the server.

This Happens every 10 minutes or so, but there seems to be no pattern to it whatsoever.  It also seems to only happen when I am using it. For example if it idles for an hour or two i can access it immediately, but after using it for a while it goes down. 

As you can imagine this is quite frustrating while I am trying to work.

Please respond if you need more information.

I really need your help, Thank You.

---

### Post by cdenley on 2010-04-02
Are you sure it isn't a bad network cable? Do the LED lights on your network card or router port turn off when you lose network connectivity?
```

sudo apt-get install ethtool
sudo ethtool eth0

```

---

### Post by KB1JWQ on 2010-04-02
Set up a ping stream to the server.  When your connection dies, does the ping stream stop as well?

---

### Post by The Titan on 2010-04-02
I will look into ethtool, and try it.  What is a ping stream? Just a script pinging repeatedly?

---

### Post by The Titan on 2010-04-02
Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 24
        Transceiver: internal
        Auto-negotiation: on
        Current message level: 0x00000001 (1)
        Link detected: yes

---

### Post by cdenley on 2010-04-02
> **The Titan said:**
> Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 24
        Transceiver: internal
        Auto-negotiation: on
        Current message level: 0x00000001 (1)
        Link detected: yes

Was that run when there was no network connection?
```

ifconfig

```

---

### Post by KB1JWQ on 2010-04-02
On your client:

ping SERVER 

You may have to give it the -t flag if you're using Windows.

---

### Post by The Titan on 2010-04-02
Ok, I have the ping running, and no, the router lights stay on when the connection is lost.

I have been using it for about 10 minutes now running ping trying to get it to go down and it wont. I will post when it does.

Scratch.  Just dropped and ping times out.

I sent ping temple -n 10000

I want to see how ling it will be down

Edit: PuTTY gives "Error: Software caused connection abort" if it matters.

---

### Post by cdenley on 2010-04-02
> **The Titan said:**
> and no, the router lights stay on when the connection is lost.


I meant specifically the light for the port the server is connected to, or the light on your network interface on the server, or the output from the ethtool command.

---

### Post by The Titan on 2010-04-02
> **cdenley said:**
> I meant specifically the light for the port the server is connected to, or the light on your network interface on the server, or the output from the ethtool command.

Sorry, I said "lights" because there is 3 lights for each port.  I did understand correctly. The lights on the nic are also still on.

---

### Post by cdenley on 2010-04-02
> **The Titan said:**
> Sorry, I said "lights" because there is 3 lights for each port.  I did understand correctly. The lights on the nic are also still on.

And does the "ifconfig" command show any errors or dropped packets?

---

### Post by The Titan on 2010-04-02
This is a few entries from the /var/log/kern.log where i see some entries relating to the network:

```
Apr  2 13:14:18 temple kernel: [   10.913941] ip_tables: (C) 2000-2006 Netfilter Core Team
Apr  2 13:14:18 temple kernel: [   11.247569]   alloc irq_desc for 17 on node -1
Apr  2 13:14:18 temple kernel: [   11.247579]   alloc kstat_irqs on node -1
Apr  2 13:14:18 temple kernel: [   11.247596] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr  2 13:14:18 temple kernel: [   11.247634] Intel ICH 0000:00:1f.5: setting latency timer to 64
Apr  2 13:14:18 temple kernel: [   11.375714] eth0:  setting full-duplex.
Apr  2 13:14:18 temple kernel: [   11.872128] intel8x0_measure_ac97_clock: measured 55385 usecs (3100 samples)
Apr  2 13:14:18 temple kernel: [   11.872137] intel8x0: clocking to 41164
Apr  2 13:14:20 temple kernel: [   14.359393] type=1505 audit(1270232060.760:7): operation="profile_replace" pid=674 name=/sb$
Apr  2 13:14:20 temple kernel: [   14.360439] type=1505 audit(1270232060.764:8): operation="profile_replace" pid=674 name=/us$
Apr  2 13:14:20 temple kernel: [   14.360963] type=1505 audit(1270232060.764:9): operation="profile_replace" pid=674 name=/us$
Apr  2 13:14:20 temple kernel: [   14.368433] type=1505 audit(1270232060.772:10): operation="profile_replace" pid=675 name=/u$
Apr  2 13:14:20 temple kernel: [   14.374667] type=1505 audit(1270232060.776:11): operation="profile_replace" pid=676 name=/u$
Apr  2 13:14:23 temple kernel: [   17.492833] type=1503 audit(1270232063.366:12): operation="open" pid=830 parent=829 profile$
Apr  2 13:14:23 temple kernel: [   17.828713] type=1503 audit(1270232063.702:13): operation="open" pid=850 parent=849 profile$
Apr  2 13:14:24 temple kernel: [   18.292715] type=1503 audit(1270232064.166:14): operation="open" pid=965 parent=857 profile$
Apr  2 13:14:24 temple kernel: [   18.990709] type=1503 audit(1270232064.862:15): operation="open" pid=975 parent=974 profile$
Apr  2 13:14:25 temple kernel: [   20.077530] type=1503 audit(1270232065.950:16): operation="open" pid=991 parent=990 profile$
Apr  2 13:14:26 temple kernel: [   20.195915] type=1503 audit(1270232066.066:17): operation="open" pid=1002 parent=1001 profi$
Apr  2 13:14:27 temple kernel: [   21.956062] eth0: no IPv6 routers present


```

I notice something about IPv6 but don't really know what this all means


This is the ifconfig output

```
root@temple:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:06:5b:a5:23:c7
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:fea5:23c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1528 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1586 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:148523 (148.5 KB)  TX bytes:1103640 (1.1 MB)
          Interrupt:18 Base address:0xcc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

```

Edit: Note: this was directly after a reboot...

Edit2: It just dropped for a few minutes, still no dropped packets in ifconfig.

---

### Post by cdenley on 2010-04-02
When it drops, does it still have an IP and gateway assigned? Can you ping your gateway?
```

ifconfig eth0
route -n
ping -c 3 192.168.1.1

```

---

### Post by The Titan on 2010-04-02
> **cdenley said:**
> When it drops, does it still have an IP and gateway assigned? Can you ping your gateway?
```

ifconfig eth0
route -n
ping -c 3 192.168.1.1

```

The IP and gateway are static so it stays assigned.

The instant that I pinged the router from the server the server came back online.  Is there some sort of inactivity setting or something somewhere?

---

### Post by cdenley on 2010-04-02
> **The Titan said:**
> The IP and gateway are static so it stays assigned.

The instant that I pinged the router from the server the server came back online.  Is there some sort of inactivity setting or something somewhere?

Are you sure you don't have any duplicate IP's?

---

### Post by The Titan on 2010-04-02
Not that i know of.  I will try a different IP to be sure.

here is my interfaces file btw, just in case i did something wrong here.

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.5
        netmask 255.255.255.0
        gateway 192.168.1.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.1.1

```

Edit:
changed ip to 192.168.1.5 and no difference.

Could this be a router issue? The server is set to DMZ through the router.

---

### Post by cdenley on 2010-04-02
> **The Titan said:**
> Not that i know of.  I will try a different IP to be sure.

here is my interfaces file btw, just in case i did something wrong here.

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.5
        netmask 255.255.255.0
        gateway 192.168.1.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.1.1

```

Now that you changed IP's, instead of waiting for it to happen again, verify your new IP, then ping your old IP.
```

ifconfig eth0
ping -c 3 192.168.1.4

```

---

### Post by The Titan on 2010-04-02
nothing on 192.168.1.4

I just remembered that there is another nic installed on this machine.  How can I verify that it is instaled correctly, I will try using that instead if it works.

---

### Post by cdenley on 2010-04-02
> **The Titan said:**
> nothing on 192.168.1.4

I just remembered that there is another nic installed on this machine.  How can I verify that it is instaled correctly, I will try using that instead if it works.

```

ifconfig -a

```
If it shows up in there, you should be able to configure it in /etc/network/interfaces.

---

### Post by The Titan on 2010-04-02
I dont see it.  Oh well, I think I remember that linux didn't recognize this card.

edit: I think I see it in lspci....  Would my onboard show up there?

---

### Post by chrisinspace on 2010-04-02
> **The Titan said:**
> The instant that I pinged the router from the server the server came back online.  Is there some sort of inactivity setting or something somewhere?

I had a problem that was very similar to this and it was an IP conflict.  This was one of the exact symptoms.  

I see that you changed your address from .4 to .5, but I would try spacing it out a little more.  I'd suggest .201 or something further up the range.  Maybe some old hardware you forgot about or a wifi enabled device grabbed some of the addresses before you disabled dhcp.

---

### Post by KB1JWQ on 2010-04-03
Be sure to let us know if the above suggestion works or not-- I'm curious now!  This is atypical behavior for Linux.

---

### Post by The Titan on 2010-04-22
Sorry it took so long to get back to you guys. Went out of town... There was a death in the family.

Anyways, I have reinstalled Ubuntu server on the machine, and the IP is now 192.168.1.100 and still having the same issue....  This must be a hardware issue right?

I have checked the BIOS for anything relating to the network hardware and all I found was Enabled/Disabled integrated hardware. I just got a new NIC card out of a friends old machine and I am going to try that out.... I will reply soon.

If that doesn't work, does anyone see an issue with making a cron job pinging the router every minute? Other than the obvious issue that it is a ghetto ( for lack of a better term ) workaround.

---

### Post by The Titan on 2010-04-23
Ok, Using a different NIC got the problem fixed...  I will mark this as solved, but if anyone knows why this may have happened please let me know.  Thanks.

---

### Post by tgalati4 on 2010-04-23
Network cards do fail.  They have sensitive transmitter and receiver circuits that can get damaged with power spikes.  I presume this is in a home setting?  Do you have an UPS on the server?

It could also be a power supply problem.  How old is the server?  When was the last time it was cleaned out?  Also, with 2 windows machines on the network, it could be a network storm due to a virus or some other windows strangeness.  Try removing the other machines from the network and see how long your machine stays connected.

Routers fail as well.  Try a different router or change the ports that the machines are connected to.

---

