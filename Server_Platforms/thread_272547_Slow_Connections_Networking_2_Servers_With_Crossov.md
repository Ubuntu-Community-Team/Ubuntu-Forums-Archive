---
title: "Slow Connections Networking 2 Servers With Crossover Cable"
date: 2006-10-06
forum: Server Platforms
---

### Post by JLTB on 2006-10-06
Hi,

I've got a setup with 2 Dell 2850 servers.  Server #1 is a web server, and #2 is a database server.  Each server has two Gigabit NICs.

I have the web server (#1) having one NIC hooked up to the WAN and the other NIC on a crossover connection to server #2.

Everything is humming along just fine on each server, however I can never sustain a transfer of more than 11.5 - 12 MBps between the two, even when the connections are very idle.

So, it appears that my servers are in a 100 base T LAN (100Mbps / 8 ~= 12MBps) even though they BOTH have 1000 base T NICs.

What is going on here?  Is there any way to get these puppies putting out the proper gigabit speed?

Do I really have to go buy a switch to make this happen?  I can't afford the downtime nor the cost, sigh.

Thanks in advance for any tips you networking guru's have got!

PS: If anybody feels this should be in the networking forum I can put it there.  Since the network IS working, no hardware issues, I thought it was better suited for the server forum.

---

### Post by peanut butter on 2006-10-06
ok for 1 i have never used gigabit lan but i do know that it requires a cat6 cable to perform correctly.~$10.00

disregard this if you alredy know this:)

---

### Post by JLTB on 2006-10-07
Hi peanut butter,

Thanks for the reply.  Lol, yes I was very sure to get a gigabit supporting cable.

Either way, the thing is about 4 feet long since the servers are stacked on top of eachother so a standard Cat 5e should be able to handle it .... erhm .. i think anyway.

I'm still feeling like it is something to do with how the network is configuring itself ... however ya, it might be the cable i guess, since I'm not 100% certian I've ever had it working at gigabit.

Anyone know if there's a way to see how my network is configuring itself?  Can I tell if the NIC is "intentionally" throttling itself back, or misnigotiating the link?

In my /etc/networking/interfaces file can I specify that this is a gigabit link?

Thanks,

James.

---

### Post by sonic2000gr on 2006-10-07
Assuming your network card is eth0 or eth1 or eth... something ;)  you could do something like:

```
dmesg |grep eth
```

and see the speed they connect. In my server for example:

```

sonic@diktia:~$ dmesg |grep eth
eth0: RealTek RTL8139 at 0xec00, 00:10:5c:df:28:55, IRQ 11
eth0:  Identified 8139 chip type 'RTL-8100'
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
eth0: no IPv6 routers present

```

Pitty I don't have gigabit cards :-k

---

### Post by JLTB on 2006-10-07
Hi sonic2000gr,

Thanks for the suggestion.  I greped dmesg for both cards and it looks like both cards are running at 10Mbps (yikes!!).

```

james@simon:/var/log$ grep eth0: ./dmesg
[   80.799134] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   82.312325] e1000: eth0: e1000_watchdog_task: NIC Link is Up 10 Mbps Full Duplex
[  127.064607] eth0: no IPv6 routers present


james@simon:/var/log$ grep eth1: ./dmesg
[   81.042576] e1000: eth1: e1000_probe: Intel(R) PRO/1000 Network Connection
[  116.535560] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  138.319784] e1000: eth1: e1000_watchdog_task: NIC Link is Up 10 Mbps Full Duplex
[  138.328745] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  149.202349] eth1: no IPv6 routers present

```

This can't be right though because I have transfered in and out of both cards at over 10Mbps ... hmmmm very wierd.

On the second server (database server, only using 1 NIC for interal LAN) I get this result:

```

james@garfunkel:/var/log$ grep eth1: ./dmesg
[   94.857130] e1000: eth1: e1000_probe: Intel(R) PRO/1000 Network Connection
[  106.292276] e1000: eth1: e1000_watchdog_task: NIC Link is Up 100 Mbps Full Duplex
[  118.486764] eth1: no IPv6 routers present

```

What the heck?

--edit--
Just for anybody who might be wondering, I'm using eth1 on the second server because eth0 is broken (my boss tripped over the ethernet cable when the servers were in my office :o.  He didn't damage any hardware (luckily), just the small plastic tabs broke off that keep the ethernet cable snug.  I didn't feel comfortable using that card on a production server

---

### Post by uforic on 2007-07-17
Hello all,

We will be building servers similar to JLTB setup, I was wondering if anyone have solved or understood the best way of going about it yet?

We have read on the net that gigabit connection between 2 nics does not need to be crossed , is this true? 

And like JLTB, our 2 Dell servers are stack ontop of each other, so the cat6 cable can be as short as possible, how will this effect the transfer rate?

And since our servers will both have 1 wan (co-lo) and 1 between servers connections, can anyone please instruct us how to go about setting this up in the configuration files, we are linux noobs, thank you.

---

### Post by JLTB on 2007-07-17
Hi uforic,

As for using a crossover to connect 2 servers "it's supposed to work with a standard ethernet cable", but often a crossover is required.  My servers still hookup at 100/T, it hasn't been a big issue for us .. so we just left it like that.

In regards to the setup, do some research on the debian config file /etc/network/interfaces

The file for our WAN facing server is something like this..

```

# NIC One
auto eth0
iface eth0 inet static
address XXX.XXX.XXX.XXX    # This is our EXTERNAL IP
netmask 255.255.240.0
gateway XXX.XXX.XXX.XXX    # Supplied by the ISP

# NIC Two
auto eth1
iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0

```

The config for our LAN server (connected to the net via the WAN server) is like this ...

```

# NIC One (LAN server)
auto eth0
iface eth0 inet static
address 192.168.0.2    # This is an INTERNAL IP
netmask 255.255.240.0
gateway 192.168.0.1    # The IP of NIC One on the WAN server ..

# NIC Two
# ... unused ...

```

I'm sure you'll figure out the rest :-)

PS: Do some research on IP tables as well, you'll need this.  If you find IP tables too confusing, try using one of the debian programs that makes the configuration easier (ie: shorewall, firestarter .. etc ..)

James.

---

### Post by uforic on 2007-07-17
Thank you JLTB, we are still gathering all information before taking the steps. Its a big move for us as we are moving from windows to ubuntu.

Very similar to your setup as one is webserver and the other a mysql server, accept both will have wan connections.

I was wondering if you have dealt with Dell PERC raid controllers, and raid configurations?

Thanks

---

### Post by JLTB on 2007-07-17
Not much, in my experience all that setup is done in the BIOS (read your PERC manual).  From there Ubuntu/Debian should just breeze through the install.

Keep in mind, PERC RAID controllers are very low-level (compared to your average desktop PCI-E RAID card).  From the OS's perspective the individual HD's don't exist.  Only the space created by the RAID.  In, errr, theory of course.

Pretty much any Linux, Windows, or BSD system should be able to install on this setup.

Good luck,

PS: One hic-up I've experienced, in Dell's opinion RedHat is the only version of Linux that exists.  Their tech support will be monumentally useless if  you mention you're using Ubuntu.  Also, all their prepackaged Linux software is RedHat only.  Some of it can be compiled for Debian based systems, other's of it can be Alien'ed (alien converts RPMs to DEBs).  Alas, some of their software (eg: the hardware monitoring tools) don't yet run on Debian based systems.

James.

---

### Post by Mr. C. on 2007-07-17
One or both of the two NICs is autonegotiating to the lower speeds.  This is not uncommon when using a crossover cable.  NICs do not have very large buffer space, and often have trouble auto-negotiating with one another.

Get a gigabit switch between those two NICs and that will solve the problem.

You can try to force 100 or 1000mbit, full duplex on both systems with ethtool.

MrC

---

