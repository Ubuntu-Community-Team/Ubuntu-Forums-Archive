---
title: "Cannot figure out what to do next."
date: 2008-08-11
forum: Server Platforms
---

### Post by alloydog on 2008-08-11
I have been following a tutorial, to set up a file sharing server, and have installed Ubuntu server 8.04.
So far everything has gone smoothly.

However, I am not sure of the network set-up situation.

Here's the problem:
The server seems to be running OK, and can install software with [FONT="Courier New"]**apt-get**[/FONT], so it must be connected to the internet somehow.

The internet connection is made through a modem/router which normally assigns local IP addresses in the 10.0.0.x range.

For instance, if I run [FONT="Courier New"]ipconfig[/FONT] on my Windows PC, it returns the IP address as [FONT="Courier New"]10.0.0.3[/FONT].

The external IP address is in the range of [FONT="Courier New"]91.154.53.xxx[/FONT],  although it changes from time to time, but usually stays fixed for a few weeks.

When I run [FONT="Courier New"]**ifconfig -a**[/FONT] on the server PC, I get and IP address in the range [FONT="Courier New"]91.154.58.xxx[/FONT].

I have tried connecting to it with putty, pinging the IP address and just looking for it on a web browser, but cannot find it at all.

What do I need to do look at to get external access (SSH/putty) to the server?

---

### Post by cdtech on 2008-08-11
Type "route" on the server PC. You should see something like:
```

xxxxxx@server:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    UseIface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
xx.xx.xx.0      *               255.255.248.0   U     0      0        0 eth0
default         x-xx-xx-xx-x.xx 0.0.0.0         UG    100    0        0 eth0

```
I'm using two NIC's on my server (eth1 and eth0). The "UG" Flag is the default gateway, that's the IP address you want to use within PUTTY.

---

### Post by alloydog on 2008-08-11
thanks for the speedy reply!

I get this:
```
~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    UseIface
91.154.xx.x     *               255.255.255.0   U     0      0        0 eth0
default         aaa-bbb-cc-d.xx 0.0.0.0         UG    100    0        0 eth0
```

I take it the value shown as **aaa-bbb-cc-d.xx** tranlates to an IP address of aaa.bbb.cc.d?

I tried that but still no connection.

I tried the 'route' command on my Windows PC,and it returned a load of info, but all the IP addresses, again, were local ones.

I can't figure out why the Linux server seems to have an external IP address not related (other than it's from the same ISP) to the external IP address allocated to my modem/router.
-------

I just had a look at /etc/network/interfaces
it reads:
```
auto lo
iface lo loopback

auto eth0
iface eth0 inet dhcp
```
I wonder if this is causing any problems - acting as a DHCP server?

---

### Post by cyracks on 2008-08-11
> **alloydog said:**
> 

auto eth0
iface eth0 inet dhcp[/code]I wonder if this is causing any problems - acting as a DHCP server?

The above means that your server is acting as DHCP client.
Since you don't have static IP address, probably your Internet provider is blocking access to your 22 port.

Try 
```
telnet **aaa-bbb-cc-d.xx** 22
```

If everithing is ok you sould get something like:
**SSH-2.0-OpenSSH_4.6p1 Debian-5ubuntu0.5**

---

### Post by cdtech on 2008-08-11
> I can't figure out why the Linux server seems to have an external IP address not related (other than it's from the same ISP) to the external IP address allocated to my modem/router.

Yes, that's your ISP provided IP address. That is the one you need to ping.

You've connected your server directly to the internet with no internal connections to your intranet. I guess you meant to do that?

---

### Post by alloydog on 2008-08-11
Thanks for the pointers, chaps.

From a quick web search, I found [*_this_*](http://www.cyberciti.biz/tips/howot-install-ubuntu-linux-ssh-server.html), which following the instructions, seems to imply that port 22 wasn't open anyway...  I followed the instructions about changing the port number for security reasons, but so far the new port still seems closed.

As for IP address.  I don't know how the server connects directly and gets it's own allocated IP address, as everything goes through the modem/router which is set up to give local IP addresses...
Maybe it has some sort of internal rules that lets servers have their own access?

Anyway, I'll have a further bash later and get back with how things worked out.  cheers.

---

### Post by alloydog on 2008-08-12
It turns out the 4th connector on my modem/router (A-link RR24AP (I+) is for IPTV and not part of the normal router connections.  I moved the cable from the laptop to another connector and now get a local IP address.

---

