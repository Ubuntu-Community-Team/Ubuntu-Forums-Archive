---
title: "Firestarter + Internet Connection Sharing = No Go"
date: 2006-04-25
forum: Server Platforms
---

### Post by austin987 on 2006-04-25
Howdy

I'm working on setting up an old dell (P4, 1.7Ghz 512Mb ram) someone gave me as a router/file server for my other comp (AMD 64, 3000+, 1Gb ram). I've got ubuntu installed with a minimal gui installation (also using it for usenet, etc). Anywho, I'm on a school network, and can only use one computer at a time, unless using a router. My goal is to have the dell run a private network for the other comp (running kubuntu/xp/osx), with a firewall provided by firestarter and IP assigned by DHCP.

I can get the ubuntu system to have internet, and the local network is set to DHCP, etc, but the other system cannot get a connection. I can't ping from it, etc (it can't get an IP assigned to it).

Here's an output of ifconfig -a on the dell system. Eth1 is connected to the internet, and eth0 to the other system by a CROSSOVER cable.

```
eth0      Link encap:Ethernet  HWaddr 00:40:F4:EC:1B:F7
          inet6 addr: fe80::240:f4ff:feec:1bf7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:29262 (28.5 KiB)  TX bytes:22611 (22.0 KiB)
          Interrupt:17 Base address:0xaf00

eth1      Link encap:Ethernet  HWaddr 00:0F:1F:4C:AE:1D
          inet addr:128.194.52.XX  Bcast:128.194.53.255  Mask:255.255.254.0
          inet6 addr: fe80::20f:1fff:fe4c:ae1d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17756 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6897 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1601 txqueuelen:1000
          RX bytes:5334811 (5.0 MiB)  TX bytes:744541 (727.0 KiB)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1554 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1554 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:77860 (76.0 KiB)  TX bytes:77860 (76.0 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

One thing I've noticed that may be a problem is the subnet mask, as the school network has 255.255.254.0, whereas ubuntu may be trying to assign an IP with a subnet of 255.255.255.0

Any help would be appreciated.

---

### Post by Jason_25 on 2006-04-25
Why do you have to use DHCP?  Just give the ubuntu pc's eth0 192.168.1.1 and the other pc 192.168.1.2 .  
```

sudo ifconfig eth0 address 192.168.1.1

```

Since your ubuntu pc will be ip forwarding (routing) all pcs on the internal network, the subnet of your external address doesn't matter.

---

### Post by alamba on 2006-04-25
Check if you have dhcp-server installed. Also this link might give you insite on the code being used to deliver internet connection sharing by firestarter [https://wiki.ubuntu.com/ThinClientHowtoNAT](https://wiki.ubuntu.com/ThinClientHowtoNAT).

A

---

### Post by austin987 on 2006-04-25
I don't have to use DHCP, but that comp has several OS's, and using a static IP would be a bigger pain. DHCP-server wasn't installed, I just did. I'm about to test. I'll report back in a few.

Thanks for the quick responses.

---

### Post by austin987 on 2006-04-25
[QUOTE=austin987]I don't have to use DHCP, but that comp has several OS's, and using a static IP would be a bigger pain. DHCP-server wasn't installed, I just did. I'm about to test. I'll report back in a few.

Thanks for the quick responses.[/QUOTE]

Installed DHCP-server, but its still not assigning IP's to the other comp (nor to itself on Eth0).

What to try next?

---

### Post by austin987 on 2006-04-25
[QUOTE=austin987]Installed DHCP-server, but its still not assigning IP's to the other comp (nor to itself on Eth0).

What to try next?[/QUOTE]

[QUOTE=austin987]I don't have to use DHCP, but that comp has several OS's, and using a static IP would be a bigger pain. DHCP-server wasn't installed, I just did. I'm about to test. I'll report back in a few.

Thanks for the quick responses.[/QUOTE]


I recompiled my kernel, enabling NAT, ip forwarding, etc, yet still can't get it to assign IP's by DHCP. I'm going to try removing dhcp-server and replacing it with dhcp3. Anyone have any ideas what else it could be? ](*,) ](*,)

---

### Post by KLineD on 2006-04-25
In the machine that's directly connected to the internet, create a file, say /etc/init.d/ip.masq You need to use sudo to create a file there.

Now, insert these lines:
```

#!/bin/sh

IPTABLES=/sbin/iptables

#All The lines below are NAT routing

# flush any old rules
$IPTABLES -F -t nat

# turn on NAT (IP masquerading for outgoing packets)
$IPTABLES -A POSTROUTING -t nat -o eth0 -j MASQUERADE

# enable IP forwarding (of incoming packets)
echo 1 > /proc/sys/net/ipv4/ip_forward

```

Of course change eth0 to whatever the nic that's connected to the internet is.

Save it and make it executable with chmod 755 /etc/init.d/ip.masq

Temporarily give the second nic in the gateway (the one with internet) computer a static ip like: 192.168.0.1 and netmask: 255.255.255.0. Setup the other computer with the same info but just change the last 1 to 2 and set the gateway to 192.168.0.1

Run the file you created earlier with sudo /etc/init.d/ip.masq and see if the other computer can get to the internet.

See if your second computer can ping the gateway computer, if it can, try to ping to the outside. If it can, you are good to go. If not, don't hit me ok? This is what I did a long time ago with warty and it worked like a charm (before I got a router).

The script, I got it from [here]("http://www.marianistas.org/comunidad_56_6493_0.htm")

---

### Post by alamba on 2006-04-26
This should work, however it still doesn't fix the problem of dhcp not dolling out IP addresses. Did you configure your dhcp server? Is the service running?

A

---

### Post by austin987 on 2006-05-03
[QUOTE=KLineD]In the machine that's directly connected to the internet, create a file, say /etc/init.d/ip.masq You need to use sudo to create a file there.

Now, insert these lines:
```

#!/bin/sh

IPTABLES=/sbin/iptables

#All The lines below are NAT routing

# flush any old rules
$IPTABLES -F -t nat

# turn on NAT (IP masquerading for outgoing packets)
$IPTABLES -A POSTROUTING -t nat -o eth0 -j MASQUERADE

# enable IP forwarding (of incoming packets)
echo 1 > /proc/sys/net/ipv4/ip_forward

```

Of course change eth0 to whatever the nic that's connected to the internet is.

Save it and make it executable with chmod 755 /etc/init.d/ip.masq

Temporarily give the second nic in the gateway (the one with internet) computer a static ip like: 192.168.0.1 and netmask: 255.255.255.0. Setup the other computer with the same info but just change the last 1 to 2 and set the gateway to 192.168.0.1

Run the file you created earlier with sudo /etc/init.d/ip.masq and see if the other computer can get to the internet.

See if your second computer can ping the gateway computer, if it can, try to ping to the outside. If it can, you are good to go. If not, don't hit me ok? This is what I did a long time ago with warty and it worked like a charm (before I got a router).

The script, I got it from [here]("http://www.marianistas.org/comunidad_56_6493_0.htm")[/QUOTE]


Been a while...I've been putting this off because registering comps on the network is a pain in the ***, and papers suck. Anywho, on to more important things.

I tried this method, as I still can't get dhcp to work (tried configuring /etc/dhcp3-server/dhcpd.conf, no go). I can ping one comp to the other, but the indirectly connected computer can't ping out. I also set the DNS server to be this comp, assuming that the above script would route it. Do I need to run a DNS server, or is that already being routed? As for DHCP, any ideas what else I should be looking for, or should I post config files, etc.

Thanks, much appreciated.

---

### Post by KLineD on 2006-05-03
No you dont need a DNS server on your machine. What DNS does the modem assign your computer? that's the one you should be using in the indirect machine, assuming you can ping the modem from there (if not, there's something wrong :-k )

---

### Post by austin987 on 2006-05-05
Working now (routing at least). I did a fresh install (unneccessary, I'm sure, but done for other reasons), followed KlineD's instructions, and put the DNS ip in the win machine along with a manual IP configuration. Internet now works there. Now I need to config DHCP, which I think I have figured out. 2 problems/questions remain:

1) Where would I add a link/command for the above script to be run on startup, it seems I have to run it upon reboot.
2) (Assuming I get the DHCP server running/configured), how could I allow the connected computer(s) to dynamically update DNS as well? Is it a matter of scripts, or installing packages related to DNS updates?

Thanks for all the help.

---

### Post by Peter76 on 2006-05-05
Hi, reading your ifconfig output in your first post, tells me that your eth0 is not configured; dhcp doesn't do this for you; you have to set it up manually either throught the networking program in gnome or if you have a server install through editingthe /etc/network/interfaces. Reading your last post, I assume eth0 is configure d now, so I won't go into that; only thing I don't understand is the sit0 in your ifconfig output..... 

Now for your questions... 

If you only have two interfaces in this setup; use Firestarter if you like it. Otherwise you put the script in /etc/init.d and make a link to this script in /etc/rcS (I think this is a new Dapper feature though)
Have a look at the README in /etc/rcS; you will have to name the symlink something like S61yourscriptname to start it at the right time.
Have a look at the ipmasq package, which can handle allthese routing things for you, even with multiple interfaces.....

Now to configure your dhcp server you need to have a look end edit /etc/dhcp3/dhcp.conf ( or something really like this, not at my router right now...)
See if you understrand it; italso forwards dns servers; if you don't, post and I'll help you out.

Good luck,

Peter

---

