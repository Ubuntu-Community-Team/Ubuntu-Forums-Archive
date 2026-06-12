---
title: "changing eth2 to eth1?"
date: 2007-05-10
forum: Server Platforms
---

### Post by Aberrix on 2007-05-10
So I setup my server with the intention of having 2 network cards, one being in the DMZ and serving all my web/email/etc functions and then one that I could use locally for samba and such. I decided to upgrade the second card (eth1) to a gigabit card since I have the hardware for it. So out with the old in with the new, except the new one is listed as eth2, which is fine and all but for practicality and my own attention to detail, how can I change this from eth2 to eth1?

second question, I'd like to have the gigabit nic somewhat locked down as in, since I have samba bound to it I'd like for it to not be accessable via the outside world. I removed the default route, is that all I need to do or is there more?

thanks in advance!

(if needed)
```
eth0      Link encap:Ethernet  HWaddr 00:40:05:39:22:D9
          inet addr:192.168.0.200  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::240:5ff:fe39:22d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1781060 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2213642 errors:0 dropped:0 overruns:8 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2108355449 (1.9 GiB)  TX bytes:704044308 (671.4 MiB)
          Interrupt:5 Base address:0xc000

eth2      Link encap:Ethernet  HWaddr 00:08:54:47:26:FE
          inet addr:192.168.0.201  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:54ff:fe47:26fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5172704 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2036097 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:612560280 (584.1 MiB)  TX bytes:1271366144 (1.1 GiB)
          Interrupt:10 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128534 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128534 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:24336052 (23.2 MiB)  TX bytes:24336052 (23.2 MiB)
```

```
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth2
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
```

---

### Post by MJN on 2007-05-10
Edit /etc/iftab to match your new card's MAC address to the name eth1 - the currently entry will still be referring to your old card and hence in its absence the name eth2 is being used.

> I'd like to have the gigabit nic somewhat locked down as in, since I have samba bound to it I'd like for it to not be accessable via the outside world. I removed the default route, is that all I need to do or is there more?I'll leave that question for someone with more (any!) experience in this area.

Mathew

---

### Post by Aberrix on 2007-05-10
> **MJN said:**
> Edit /etc/iftab to match your new card's MAC address to the name eth1 - the currently entry will still be referring to your old card and hence in its absence the name eth2 is being used.

here is what my iftab looks like;

```

eth0 mac 00:40:05:39:22:d9 arp 1
eth1 mac 00:a0:cc:79:3c:ef arp 1
```

shouldn't eth2 be listed in there?

---

### Post by MJN on 2007-05-10
To be honest I'm not sure at what stage, and by whom, it gets configured - it could perhaps be during initial installation when the networking gets installed.

Either way as you've just got the two cards just manually edit it to:

```
eth0 mac 00:40:05:39:22:d9 arp 1
eth1 mac 00:08:54:47:26:fe arp 1
```I stumbled across this little-discussed issue when I transplanted a hard drive (with Kubuntu already installed on it) from one machine to another, identical, one. I was scratching my head as to why the network needed manually bringing up every reboot and I eventually sussed out that the 'new' network card obviously didn't have the same MAC address as that previously and hence was not being called eth0.

Mathew

---

### Post by Aberrix on 2007-05-10
well if I manually change /etc/iftab and then also /etc/network/interface

then do a sudo /etc/init.d/networking restart, I get the following;

```
 * Reconfiguring network interfaces...
Ignoring unknown interface eth2=eth2.
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFBRDADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Failed to bring up eth1.
```

---

### Post by MJN on 2007-05-10
I know it's very 'Windows' but I think I'd go with a reboot given that part of the networking 'restart' will inevitably be shutting down the existing service and given you've changed the config mid-way perhaps this is stalling the process and hence failing to complete.

Mathew

---

### Post by Aberrix on 2007-05-10
well that was an exercise in patients...

both nic's went down...

there is something else that's holding onto that eth2 namespace...

anyone have any ideas?

---

### Post by MJN on 2007-05-10
How strange...

Have you got any GUI installed? Do you still have the problems when booting into single-user mode (and no X)?

Post your current /etc/iftab and /etc/interfaces - perhaps there's something not quite right that's being overlooked.

Mathew

---

### Post by Aberrix on 2007-05-10
I have no gui (see signature for system)

/etc/iftab
```
eth0 mac 00:40:05:39:22:d9 arp 1
eth1 mac 00:a0:cc:79:3c:ef arp 1
eth2 mac 00:08:54:47:26:fe arp 1
```
*note I manually added eth2

/etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.200
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

# The secondary network interface
auto eth2
iface eth2 inet static
        address 192.168.0.201
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:40:05:39:22:D9
          inet addr:192.168.0.200  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::240:5ff:fe39:22d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10466 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14396 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:955837 (933.4 KiB)  TX bytes:11340541 (10.8 MiB)
          Interrupt:5 Base address:0x4000

eth2      Link encap:Ethernet  HWaddr 00:08:54:47:26:FE
          inet addr:192.168.0.201  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:54ff:fe47:26fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:288 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:27727 (27.0 KiB)  TX bytes:1128 (1.1 KiB)
          Interrupt:10 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1307 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1307 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:317340 (309.9 KiB)  TX bytes:317340 (309.9 KiB)
```

basically, I played around with iftab & /etc/network/interfaces and doing /etc/init.d/networking start/stop/restarts. I ended up borking everything over ssh so I ran home quick and played with it some more and finally just tried to get it back to what it was, which I succeded and now am back where I started...

---

### Post by MJN on 2007-05-10
Ah... reconfiguring network interfaces over SSH is obviously not the wisest thing to be doing!

So if you swap eth1 and eth2 in /etc/iftab around it doesn't work? Specifically, you don't end up with just eth0 and eth1 up on your machine?

Howcome you've still got 00:a0:cc:79:3c:ef in that file? I thought that card no longer exists (in that machine)?

Mathew

---

### Post by Aberrix on 2007-05-10
> **MJN said:**
> Ah... reconfiguring network interfaces over SSH is obviously not the wisest thing to be doing!

I ssh into eth0 (.200), so I assumed that if I was messing with eth2/1 (.201) I wouldn't have too much a problem... well...

> **MJN said:**
> 
So if you swap eth1 and eth2 in /etc/iftab around it doesn't work? Specifically, you don't end up with just eth0 and eth1 up on your machine?

nope, ever after swapping and playing I'd get messages like "Ignoring unknown interface eth2=eth2."

> **MJN said:**
> Howcome you've still got 00:a0:cc:79:3c:ef in that file? I thought that card no longer exists (in that machine)?

It never deleted, I did delete it and re-added it during trying to get things to work.

---

### Post by Aberrix on 2007-05-10
okay, I did a 'sudo ifconfig eth2 down'

then went into /etc/iftab and edited it;
```
eth0 mac 00:40:05:39:22:d9 arp 1
eth1 mac 00:08:54:47:26:fe arp 1
```

then went into /etc/network/interface and edited it;
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.200
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

# The secondary network interface
auto eth1
iface eth1 inet static
        address 192.168.0.201
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
```

then did a 'sudo ifconfig eth1 up'
and got the following;
```
eth1: ERROR while getting interface flags: No such device
```

but at the end of it all, if I do a 'sudo ifconfig eth2 up' then eth2 comes back up...

---

### Post by MJN on 2007-05-10
I'm still not happy that you're not rebooting...

Could be very wrong about it, and it sounds like you're not in the best position (geographically!) to enjoy such blunt manoeuvres!

Mathew

---

### Post by Aberrix on 2007-05-10
> **MJN said:**
> I'm still not happy that you're not rebooting...

Could be very wrong about it, and it sounds like you're not in the best position (geographically!) to enjoy such blunt manoeuvres!

Mathew

are you suggesting I change /etc/iftab and /etc/networking/interfaces and THEN reboot?

(reboots are for windows :P)

---

### Post by MJN on 2007-05-10
Yeah - change then reboot.

If the worst comes to the worst just change back, reboot again, and we'll both go our separate ways! ;)

Mathew

---

### Post by Aberrix on 2007-05-10
> **MJN said:**
> Yeah - change then reboot.

If the worst comes to the worst just change back, reboot again, and we'll both go our separate ways! ;)

Mathew

well what do you know... it worked! :oops:

thank you very much!

---

### Post by MJN on 2007-05-10
Of course it worked! Did I ever sound unsure? (don't answer that... ;))

> **Aberrix said:**
> (reboots are for windows :P)

... :-\"

Mathew

---

