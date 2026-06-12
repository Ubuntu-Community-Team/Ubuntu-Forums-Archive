---
title: "Network Speed Issues"
date: 2008-08-13
forum: Server Platforms
---

### Post by The Titan on 2008-08-13
I am having trouble with my local network,  I have a small server set up and it runs apache and ssh and some other services but anyways when i try to connect with my browser with the local IP it is very slow, it is actually faster to go through a web proxy with my real IP.  (I have to go through a proxy else i get my modem =/)

This is the interfaces file from my workstation (not the server):

```

titan@laboratory:/etc/network$ cat interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.2
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.0.1
titan@laboratory:/etc/network$       

```and hosts:

```

titan@laboratory:/etc/network$ cat /etc/hosts
127.0.0.1       localhost
192.168.0.2     laboratory
192.168.0.5     dungeon


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


```If you need any more information let me know please, i appreciate your help.

---

### Post by The Titan on 2008-08-13
Any way a mod con move this to the networking section please?

---

### Post by MJN on 2008-08-14
> **The Titan said:**
> Any way a mod con move this to the networking section please?We not good enough for ya? ;)
 
You really need to try and narrow it down to either a hardware, software or network issue. You can do this to a certain extent by using different applications (Apache, SCP copies, Samba fileshares etc) to compare the throughput with each. If you find it is only slow with the one method then it is likely to be a configuration issue with that particular application.
 
Alternatively, or perhaps in addition to, there are a few network tools that will help you determine exactly how 'good' your network is and hence what to expect to get from it practically.
 
First off, try running **mii-diag** to show the connection status of your Ethernet adapter(s) (I'm assuming you're using Ethernet) - e.g. whether it is running in half/full duplex, at what speed, etc.
 
Assuming this comes out fine (if it doesn't then we need to work out why not) then try installing **iperf** - it is a low-level network throughput tool to really max out your network.
 
It requires installing on both ends - client and server - and on the server you should run it with **iperf -s**
 
On the client you then have a few options. First, run it with **iperf -c <ip of server>** and this will establish a TCP stream between the two machines and tell you the maximum throughput. For a full-duplex 100Mbps Ethernet connection you should be looking at reaching ~90Mbps on an otherwise-silent network.
 
You can also run it in UDP mode, which will highlight packet loss better, using **iperf -u -b <speed> -c <ip of server> **where <speed> is the transfer rate you want to test at. Start with **1** and go up through **10**, **20**, etc and see how much packet loss you get. Again, with a full-duplex 100Mbps network (supported properly at both ends) you should be getting ~90mbps without any packet loss.
 
If you want to try this but need further help just shout and I'll walk you through it in more detail.
 
Mathew

---

