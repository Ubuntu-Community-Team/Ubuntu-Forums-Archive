---
title: "shutdown hangs on deconfiguring network interfaces"
date: 2010-03-17
forum: Server Platforms
---

### Post by lytithwyn on 2010-03-17
There are several threads in the forums about karmic not shutting down properly, but none of them were under the exact same circumstances as I'm having.

I'm using 9.10 server-edition as a intercepting squid server, and during shutdown/reboot, it gets to "deconfiguring network interfaces" then hangs indefinitely.  I can do REISUB, but it doesn't actually reboot.  It tells me that it's killing everything, the sync completes, and the remount r/o completes, but the "B" part doesn't do anything.

If I don't REISUB, it hangs for a few minutes on startup before init outputs anything.

I posted all the useful information I can think of below.  In regard to my iptables rules, do I need something on pre/post-down to clear them?  Is that the problem?

Network hardware:
```

06:01.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 01)

```

/etc/network/interfaces: (I have udev rules that set my interface names)
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto wan0
     iface wan0 inet static
     address 208.78.184.140
     netmask 255.255.255.128
     gateway 208.78.184.129

auto lan0
       iface lan0 inet static
       address 192.168.2.1
       netmask 255.255.255.0
       pre-up iptables-restore < /etc/iptables.rules

```

The iptables commands that were entered for generating /etc/iptables.rules with iptables-save:
```

# iptables forwarding
iptables -A FORWARD -i lan0 -o wan0 -s 192.168.2.0/24 -m state --state NEW -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A POSTROUTING -t nat -j MASQUERADE 

# iptables for squid transparent proxy
iptables -t nat -A PREROUTING -i lan0 -p tcp --dport 80 -j DNAT --to 192.168.2.1:3128
iptables -t nat -A PREROUTING -i wan0 -p tcp --dport 80 -j REDIRECT --to-port 3128

iptables -A INPUT -i wan0 -p icmp --icmp-type 8 -j DROP
iptables -A INPUT -i wan0 -s 192.168.2.0/24 -j ACCEPT
iptables -A INPUT -i wan0 -m state --state ESTABLISHED -j ACCEPT
iptables -A INPUT -i wan0 -j REJECT

```

---

### Post by lytithwyn on 2010-03-24
Well, today I decided to just try my idea of clearing iptables on shutdown.  It seems to have fixed my hang on deconfiguring network interfaces.  If anyone knows of a security problem with this, let me know.  I do still sometimes have a hang on startup even with a clean reboot, but I guess this is a different problem.

For the record, here's the relevant block from my /etc/network/interfaces:

```

auto lan0
       iface lan0 inet static
       address 192.168.2.1
       netmask 255.255.255.0
       pre-up iptables-restore < /etc/iptables.rules
       pre-down iptables -F ; iptables -t nat -F ; iptables -t mangle -F

```

---

### Post by mfecteau on 2011-03-29
This didn't fix the problem for me.  I finally got it working by troubleshooting like this :

edit the file /etc/init.d/networking
change :
#!/bin/sh -e
by
#!/bin/sh -ex

By doing this, I knew which line of the script got stuck ...  It was an interface that was setup for a device that was not plugged in the computer, so it was stuck in an infinite loop.  I commented out a part of this script (/etc/init.d/networking) so it would not try to unload the driver..

---

### Post by lytithwyn on 2011-03-29
Nice tip, mfecteau!  I'll have to remember that one!

---

### Post by backu on 2011-04-05
Tried both of these methods, could not get it to work. the /etc/init.d/networking '-ex' change stopped at the ifdown -a --exclude=lo, showed nothing past that, and I didn't feel like commenting that section out would be a good idea.

However, I did get it fixed. Went into the rc.6 and rc.0 folders, changed S35networking to S15networking (deconfigure earlier), and it worked just fine. Everything shuts down and reboots properly with no hang.

---

### Post by K_Light2003 on 2011-04-05
> **backu said:**
> Tried both of these methods, could not get it to work. the /etc/init.d/networking '-ex' change stopped at the ifdown -a --exclude=lo, showed nothing past that, and I didn't feel like commenting that section out would be a good idea.

However, I did get it fixed. Went into the rc.6 and rc.0 folders, changed S35networking to S15networking (deconfigure earlier), and it worked just fine. Everything shuts down and reboots properly with no hang.


Hi, but of a newbie at this I'm afraid.

I tried all the mentioned fixes, and was hoping that  ***backu***'s fix would fix things for me.

Unfortunately changing the names of the above files in my  rc0.d & rc6.d folders them prevented the server from booting.. Oppps.. 

Anyone got any more Ideas on this.. My system started to hang on shutdown after I installed wpasupplicant [(see this thread)]("http://ubuntuforums.org/showthread.php?t=1717127")

---

