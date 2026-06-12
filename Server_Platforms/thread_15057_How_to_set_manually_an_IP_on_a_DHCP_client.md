---
title: "How to set manually an IP on a DHCP client?"
date: 2005-02-11
forum: Server Platforms
---

### Post by istoyanov on 2005-02-11
I'm running an Ubuntu-powered server (no X, no monitor, no keyboard!) within a Windows network, that gets its IP through DHCP, but I would like to assign the IP address manually.

I would be VERY grateful if some experienced Admin points me at the right configuration files that have to be manipulated in order to achieve the desired result. 

Thank you in advance!

---

### Post by cblack on 2005-02-11
That isn't something you do on the client side. Unless I'm mis-reading your post you're saying that your Ubuntu box gets assigned an IP from a DHCP server residing elsewhere on the network, yes?

Without knowing what DHCP server you're running on the other machines we're not going to be able to help much. If you aren't the admin of your network you could always send your admin your server's MAC address and ask that it be assigned a "static" DHCP IP.

---

### Post by istoyanov on 2005-02-11
I have another fully-featured Ubuntu box on the same network and I know how to assign manually an specific IP under X (i.e. Computer -> System configuration -> Network -> Connections -> Properties).

The problem is that I have almost no experience with a X-less install:( I assume that the above described effect can be reached by editing some configuration files.

---

### Post by alastair on 2005-02-11
I'm not sure about this - I assume you want a DHCP assigned "fixed" address?

If so, you could check :

/etc/dhcp3
/etc/dhcp3/dhclient.conf

and "man dhclient.conf".

It looks like it might be possible from the .conf file.

---

### Post by Viper12 on 2005-02-12
2 ways in a windows networked enviroment.

1. Use the DHCP utilities on the windows server to manually assign a specific address to the linux's mac address.  (Every time the linux machine comes online asking for an assignment, DHCP will hand it the 'reserved' address.

2. Use the router's DHCP static address section (if using a router i.e. netgear/linksys, etc.).

the linux machine boots up, and the router sees the mac address and hands out the same address to the machine.

---

### Post by istoyanov on 2005-02-12
Thank you for the valuable input, alastair and Viper12!

I'll deal with your suggestions on monday, and will let you know the results.

Thanks again!

---

### Post by dewey on 2005-02-12
The word you're looking for, is a
"Static" IP address, that is, one that is not assigned by DHCP, your computer will use it instead of what it is assigned by your router. I used the:
Computer -> System Config -> Networking
Gui for setting my internal address to 192.168.1.111  Which is high enough that it won't be given away to another computer (My router starts assignging at 192.168.1.100) and still easy to remember.

---

### Post by istoyanov on 2005-02-13
[QUOTE=dewey]The word you're looking for, is a
"Static" IP address, that is, one that is not assigned by DHCP, your computer will use it instead of what it is assigned by your router. I used the:
Computer -> System Config -> Networking
Gui for setting my internal address to 192.168.1.111  Which is high enough that it won't be given away to another computer (My router starts assignging at 192.168.1.100) and still easy to remember.[/QUOTE]

Yes, exactly!

But if you read my post, you'll notice that the machine in question doesn't have X installed, consequently I can not use the GUI to do the settings. Do you have any idea where I have to write the desired IP to use it?

---

### Post by mendicant on 2005-02-13
Look in /etc/network/interfaces

For a static IP address, you need a stanza like:

auto eth0
iface eth0 inet static
  address 192.168.0.2
  netmask 255.255.255.0
  broadcast 192.168.0.255
  gateway 192.168.0.1

---

### Post by istoyanov on 2005-02-13
[QUOTE=mendicant]Look in /etc/network/interfaces

For a static IP address, you need a stanza like:

auto eth0
iface eth0 inet static
  address 192.168.0.2
  netmask 255.255.255.0
  broadcast 192.168.0.255
  gateway 192.168.0.1[/QUOTE]

Thanks a lot for this suggestion! I'll try it tomorrow and 'll post back.

Cheers!

---

### Post by istoyanov on 2005-02-14
Thanks a lot, **mendicat**!

Your advice solved my problem -- now the Ubuntu box has the desired IP:)

However, I just observed one drawback: the machine is no more reachable on the network by its name, but ONLY by its IP:(

How can I make the box reachable by its name again?

---

### Post by mendicant on 2005-02-14
Well, whoever is assigning names needs to point the name to the correct IP address.  Alternatively, change the static IP address to what the name points to.  Depending on your situation, changing the name to point to the address could involve changing a DNS record, or modifying /etc/hosts on various clients.

---

### Post by istoyanov on 2005-02-14
Thanks again for the valuable comments!!!

The problem is resolved:)

Good luck, and cheers!

---

### Post by jdong on 2005-02-14
[QUOTE=istoyanov]How can I make the box reachable by its name again?[/QUOTE]

That's handled by the DNS server, not your box. Contact your DNS administrator, or put on your DNS admin hat and investigate!

A  workaround is to install Samba, which would let windows boxes use NMB broadcast to locate your server by NetBIOS name.

---

### Post by istoyanov on 2005-02-15
[QUOTE=jdong]That's handled by the DNS server, not your box. Contact your DNS administrator, or put on your DNS admin hat and investigate!

A  workaround is to install Samba, which would let windows boxes use NMB broadcast to locate your server by NetBIOS name.[/QUOTE]

This is exactly what I did. Thank you for the response, **jdong**!

---

### Post by chapterthree on 2005-04-05
Hey All,

I tried the method above, but I'm having some issues.  I have pasted the details below for the settings.  Weird thing I can access the computer via an smbfs mount, but I am unable to get on the internet with that computer.  Any ideas?

This is the /etc/networking/interfaces file:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
#iface eth0 inet dhcp

# Static Assign
auto eth0
iface eth0 inet static
address 192.168.1.110
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.1

```

And here is what ifconfig reports:
```
eth0      Link encap:Ethernet  HWaddr 00:10:5A:19:8B:54
          inet addr:192.168.1.110  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::210:5aff:fe19:8b54/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:579 (579.0 b)  TX bytes:3406 (3.3 KiB)
          Interrupt:10 Base address:0xd000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5843 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5843 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:307468 (300.2 KiB)  TX bytes:307468 (300.2 KiB)

```

Any help would be greatly appreciated.

---

### Post by HungSquirrel on 2005-04-05
> Weird thing I can access the computer via an smbfs mount, but I am unable to get on the internet with that computer.
Well, you have an IP address, and other boxes can connect to your box, so that suggests a DNS problem.  What is the output of **cat /etc/resolv.conf**?

---

### Post by chapterthree on 2005-04-05
cat /etc/resolv.conf:

```
nameserver 63.200.115.40
nameserver 206.13.28.12

```

Please note this is the same information that is on this machine, which is working.

Any ideas?

---

### Post by Whiffle on 2005-04-05
[QUOTE=chapterthree]Hey All,

I tried the method above, but I'm having some issues.  I have pasted the details below for the settings.  Weird thing I can access the computer via an smbfs mount, but I am unable to get on the internet with that computer.  Any ideas?

This is the /etc/networking/interfaces file:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
#iface eth0 inet dhcp

# Static Assign
auto eth0
iface eth0 inet static
address 192.168.1.110
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.1

```

And here is what ifconfig reports:
```
eth0      Link encap:Ethernet  HWaddr 00:10:5A:19:8B:54
          inet addr:192.168.1.110  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::210:5aff:fe19:8b54/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:579 (579.0 b)  TX bytes:3406 (3.3 KiB)
          Interrupt:10 Base address:0xd000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5843 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5843 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:307468 (300.2 KiB)  TX bytes:307468 (300.2 KiB)

```

Any help would be greatly appreciated.[/QUOTE]


What kind of router are you using?  My linksys is on 192.168.1.1 not 192.168.0.1 , if the computer has the wrong gateway set it won't see the internet.


```
# The primary network interface
auto eth0
iface eth0 inet static
name Ethernet LAN card
address 192.168.1.151
netmask 255.255.255.0
gateway 192.168.1.1
```

---

### Post by chapterthree on 2005-04-05
I use a Linksys router as well, and I use 192.168.1.1 as well.  I just copied the gateway info from the post earlier in this thread.  I will try changing that.

Thanks for the suggestion

[Follow Up] Yes, this was the issue, thank you so much!  :)

---

### Post by juanpasolcas on 2006-03-21
hi, I need your Help, somebody can help me ?

---

### Post by juanpasolcas on 2006-03-21
[QUOTE=juanpasolcas]hi, I need your Help, somebody can help me ?[/QUOTE]
I have installed an ubunto but wen I Was install it, y put on it an IP address, but Now I need to change it, please help !!1

---

### Post by juanpasolcas on 2006-03-21
test

---

### Post by lcg on 2006-03-21
[QUOTE=juanpasolcas]I have installed an ubunto but wen I Was install it, y put on it an IP address, but Now I need to change it, please help !!1[/QUOTE]
First of all, repeat after me: "I shall not hijack a thread!"

Second, if you read the thread from the beginning, you will find the information in what file you can change your network interface configuration (hint: /etc/networking/interfaces).

HTH,
Lars

P.S.: If you really need multiple exclamation marks, at least keep the shift button pressed till the end, please. (Terry Pratchett anyone? ;))

---

### Post by rE~vOLt on 2006-03-30
Okay i get the jist of what needs to be done. but i'm new to this! How do i go into edit mode? To edit the files.

I got there. Tried to edit them as well. But tried to save (which i've forgotten the commands to) and it told me it couldn't save!

HELP

](*,)

---

### Post by kmi on 2006-03-30
To be short:
```
sudo gedit /the/thing/iwannaedit
```
You certainly may also have a brief journey into "manuals"... : [here]("http://ubuntuforums.org/forumdisplay.php?f=73") or [here]("http://doc.gwos.org/index.php/BreezyCust")...

3rd option : do not hesitate to fill the "search" field for more accurate results (warning ! several extra clicks required) : click 'search' and then 'advanced search'

:-|

---

### Post by rE~vOLt on 2006-03-31
Okay will get back to you.... Kind of messed up and wiped the interfaces file.

Young skyWalker is still breaking through....

---

