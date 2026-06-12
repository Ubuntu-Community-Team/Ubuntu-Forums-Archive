---
title: "Samba on Karmic with Two NIC, Connections Problems"
date: 2010-02-24
forum: Server Platforms
---

### Post by waldgeist_di on 2010-02-24
My setup:

[LIST]
[*]Ubuntu Karmic Server Edition 64 bit
[*]Dell PowerEdge T610
[*]4 internal NIC RJ45
[*]1 add-on NIC Fibre 1 Gb
[*]Samba 3.4.0
[*]two shares intended for WIN clients
[/LIST]

Connections:

eth0 (the first internal NIC) is part of a private network of 4 servers connected to a Gb switch. this connections serves as a fast link among these servers to regularly transfer (backup) large quantities of data. Only I can utilise it from within the server room (among those servers, obviously).

eth0: 192.168.0.AA1

eth4 is the Intel add-on NIC with 1 GB fibre connections to the public network of our institution. This is the link/IP my WIN clints have to use to access their shares.

eth4: 134.XXX.YYY.ZZ1

My Problem:

Despite having including both interfaces in my smb.conf only the internal connection via eth0 lives up to my expectation and delivers up to 50 MB/s.

All clients trying to connect via eth4 will be able to see and access the shares, but file transfers commence with speeds severely below 0,5 MB/s with lots of aborts and warnings from the WIN file explorer.

So I experimented with the setting "interfaces" in the global section of smb.conf --- to no avail. I even set samba only to eth4: same problem. Only way to get flawless & fast transfers is the way through eth0.

The samba log files of the clients I tried do show some errors, but I fear I am unable to interpret them properly.

/etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface Intel Gb link via fibre
auto eth4
iface eth4 inet static
	address 134.XXX.YYY.ZZ1
	netmask 255.255.255.0
	network 134.XXX.YYY.0
	broadcast 134.XXX.YYY.255
	gateway 134.XXX.YYY.254
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 134.XXX.BBB.CCC

# internal Gb link via eth0
auto eth0
iface eth0 inet static
	address 192.168.0.AA1
	netmask 255.255.255.0

```

What other info/output shall I post to give any clues?

---

### Post by waldgeist_di on 2010-02-24
/etc/samba/smb.conf

```

# Samba Configuration File created manually by Waldgeist 2010/01/15
# edited 2010/02/24

[global]
        workgroup = WELTFORST
        server string = %h SRV (SMB, Karmic)
        dns proxy = No
	interfaces = 127.0.0.1, eth0, eth4
	bind interfaces only = yes
        hosts allow = 127.0.0.1, a couple of hosts here...
        hosts deny = ALL
        log file = /var/log/samba/log.%m
        max log size = 4096
        security = user
	load printers = no
	show add printer wizard = no
	printing = cups
	printcap name = /dev/null
	disable spoolss = yes 

[sicherungen]
        comment = Sicherungsordner von Meistergeiser
        path = /home/meistergeister/Sicherungen
        writable = yes
        browsable = no
        valid users = meistergeister

[ed_user1]
        comment = Files User1
        path = /home/user1/Daten
        writable = yes
        browsable = no
        valid users = user1

```

---

### Post by waldgeist_di on 2010-02-26
No one out there with a clue :o?

---

### Post by dmizer on 2010-02-26
Try posting the errors. I assume that the errors are in German, but there may still be someone here able to read and understand them.

Are the restrictions on hosts and interfaces necessary in your environment? These could possibly be causing your problem.
```
	interfaces = 127.0.0.1, eth0, eth4
	bind interfaces only = yes
        hosts allow = 127.0.0.1, a couple of hosts here...
        hosts deny = ALL
```
Otherwise, things may improve if you include the 134.XXX.YYY.0 in your "hosts allow" option. I was unable to determine if the bind interfaces only option overrides hosts deny or not, but it looks like unless your 134.XXX.YYY.0 range is in the hosts allow, it will be refused.

With that in mind though, I'm not sure why your eth0 interface works as desired.

Also, are you positive that the fiber nic is operating correctly?

---

### Post by waldgeist_di on 2010-02-26
Thank you for your help!

> **dmizer said:**
> 
...

Also, are you positive that the fiber nic is operating correctly?

Looks like that's exactly my problem. The site administrator just informed me about possible problems with the combination [my Intel NIC + Foundry Hardware].

Therefore, as a test, I reconfigured the connection to the outside LAN to use eth1 (the second internal RJ45/Gb NIC). All other configurations stay the same > instant success. Both transfer directions end up with 9 to 9,5 MB/s.

The only drawback: the internal NIC is presently connected to a 100 Mb switch/converter which in turn connects to the fibre network in this building instead of a 1 Gb link.

---

### Post by dmizer on 2010-02-26
> **waldgeist_di said:**
> Thank you for your help!



Looks like that's exactly my problem. The site administrator just informed me about possible problems with the combination [my Intel NIC + Foundry Hardware].

Therefore, as a test, I reconfigured the connection to the outside LAN to use eth1 (the second internal RJ45/Gb NIC). All other configurations stay the same > instant success. Both transfer directions end up with 9 to 9,5 MB/s.

The only drawback: the internal NIC is presently connected to a 100 Mb switch/converter which in turn connects to the fibre network in this building instead of a 1 Gb link.

Well, at least you know what the problem is. Hopefully you can get the hardware sorted out so that you can get back up to speed.

Glad to have helped.

---

