---
title: "diablo 1: ipx lan games"
date: 2010-10-22
forum: Wine
---

### Post by gufide on 2010-10-22
there a way to unable ipx on wine for diablo? I follow some tutorial but doesn't work :(

---

### Post by gradinaruvasile on 2010-10-22
IPX works on wine. I played Bomberman over LAN and that uses IPX too. You have to install the ipx package, load the ipx module with

sudo modprobe ipx

and add to the used network interface (my is eth0, but yours may differ)

sudo ipx_interface add -p eth0 802.2

And start the game. I added these commands to a script. Recently i played Bomberman over the internet (we set up a vpn server with openvpn, and added ipx to the used tap interface - it works great).
Also i had some sound issues - sound cut off in other apps when running wine - solved by running the game with

padsp wine program.exe

---

### Post by gufide on 2010-10-22
I already do this but I got a error message in the game and it say:

unable to initialize selected network connection

---

### Post by gufide on 2010-10-22
no one?

---

### Post by gradinaruvasile on 2010-10-22
More exactly?
Post the output of:

ifconfig

and the command you tried to use to initialize ipx.

Bear in mind that you must have the ipx package installed beforehand and the ipx module loaded in memory.

---

### Post by gufide on 2010-10-22
I got that

```
eth0      Link encap:Ethernet  HWaddr e0:cb:4e:4e:94:f6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:48 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2875 (2.8 KB)  TX bytes:2875 (2.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:25:d3:89:84:53  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:d3ff:fe89:8453/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:403 errors:0 dropped:0 overruns:0 frame:0
          TX packets:479 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:405238 (405.2 KB)  TX bytes:105012 (105.0 KB)
```

I used the same command as you

---

### Post by gradinaruvasile on 2010-10-22
Not good. I said you might have a different interface. You do have.
Your interface that is used is wlan0 (wireless)

so in your case the command is:

sudo modprobe ipx

sudo ipx_interface add -p wlan0 802.2

---

### Post by gufide on 2010-10-22
that's good?

```
eth0      Link encap:Ethernet  HWaddr e0:cb:4e:4e:94:f6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:48 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5270 (5.2 KB)  TX bytes:5270 (5.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:25:d3:89:84:53  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:d3ff:fe89:8453/64 Scope:Link
          IPX/Ethernet 802.2 addr:0025D3898453
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:94908 errors:0 dropped:0 overruns:0 frame:0
          TX packets:113068 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20019680 (20.0 MB)  TX bytes:11752029 (11.7 MB)

```

I try to run diablo with ipx and it say the same message, don't work again

---

### Post by gradinaruvasile on 2010-10-23
```
wlan0     Link encap:Ethernet  HWaddr 00:25:d3:89:84:53  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:d3ff:fe89:8453/64 Scope:Link
          [COLOR="Red"]IPX/Ethernet 802.2 addr:0025D3898453[/COLOR]
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:94908 errors:0 dropped:0 overruns:0 frame:0
          TX packets:113068 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20019680 (20.0 MB)  TX bytes:11752029 (11.7 MB)
```

ipx is set up correctly. Other than that i cant help you because i dont know the way Diablo is handled by wine ([http://www.linuxquestions.org/questions/linux-games-33/diablo-1-in-linux-218393/](http://www.linuxquestions.org/questions/linux-games-33/diablo-1-in-linux-218393/)).
Here are some things to consider:
- I played Bomberman over ipx in Ubuntu 9.04 and Debian Squeeze and had no trouble connecting to the server. Do not compile wine, use the one provided by Ubuntu (preferably 1.2+ version) because that has ipx support compiled.
- Make sure the other computer has ipx set up correctly too.
- Make sure your computers are in the same LAN (same ip class), preferably the same switch (i did however play over internet too, but there we had a dedicated vpn tunnel created for this with specified routing and tap devices).
- The other computer must be reachable by its ip address (should reply to ping - if it is Windows, disable the firewall). Because if it is not you should check your wireless routers settings and make sure that the wireless clients connected to it  "see" each other (if both connected via wireless) or the wired clients connected through cable (if the other computer is connected via cable).
- If both are connected through wireless, it might work a little slower because of the many small packets transmitted both ways.

Edit:
You might try disable the wired connection interface (maybe wine tries to work through the eth0 by default) - right-click on the network-manager icon, untick the wired connection or in a terminal type "sudo ifdown eth0" (re-enabling is "sudo ifup eth0 or ticking the wired button again).

---

### Post by twipley on 2011-08-23
Have you tried using VirtualBox?
[http://diablo.incgamers.com/forums/showthread.php?t=805105](http://diablo.incgamers.com/forums/showthread.php?t=805105)

One might have to try using v0.2.2 of the there-referenced wrapper.

---

