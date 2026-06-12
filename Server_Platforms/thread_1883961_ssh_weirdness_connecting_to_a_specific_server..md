---
title: "ssh weirdness connecting to a specific server."
date: 2011-11-20
forum: Server Platforms
---

### Post by MakOwner on 2011-11-20
I recently installed an Ubuntu server.

I was doing some setup and was doing some quick login, change parms and reboots via ssh from my laptop.

After the last time, I can no longer login via ssh - I can't find any logs on the laptop or the server as to why the login isn't working.

ssh debug looks like this:

$ ssh -vvv pe8502
OpenSSH_5.3p1 Debian-3ubuntu7, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to pe8502 [192.168.20.42] port 22.
debug1: connect to address 192.168.20.42 port 22: Connection timed out
ssh: connect to host pe8502 port 22: Connection timed out

This is using the wireless connection from my laptop.
The wired connection works fine.
I can ssh into another server from the laptop, then into the subject server fine -- so it's only the conneciton directly from the wireless interface to the server that's the issue.

Can anyone point me where to look to solve this?

I posted this in the laptops forum and haven't gotten any replies, so I thought I'd try here.

Two days now and I can't ssh in from wireless.
The wireless router does NAT, so I tried it from another wireless laptop and it doesn't work from there either, so it appears the issue is between the wireless router and the server.

The server in question is at 192.168.20.42, the wireless router is at 192.168.20.13. The wireless router hands out 192.169.1.x addresses to wireless clients.

It's a Linksys WRTLN160 if that rings a bell with anyone.

---

### Post by hawkmage on 2011-11-20
I assume that there is a software firewall on the server, have you checked to see that could be blocking connections from the Wireless network IP range?

---

### Post by MakOwner on 2011-11-20
> **hawkmage said:**
> I assume that there is a software firewall on the server, have you checked to see that could be blocking connections from the Wireless network IP range?

There shouldn't be unless one somehow got activated on the linksys.
The server is a mini install disk and all the packages added after that are manually added -- even ssh client and server.
I have looked over the linksys too, and I can't even see a request going through it, however, the logs are not too good on the linksys.

---

### Post by MakOwner on 2011-11-20
Looks like anything on the wireless network can't connect to the new server.

Network topology looks like this:

Internet -> NAT'ing router -> 192.168.20.x network -> Linksys NAT'ing router at 192.168.20.13 -> 192.169.1.x network.  Addresses on this network are provided from the Linksys DHCP server starting at .100.

I just changed the linksys NAT network to 192.168.30.x network.

I can't find anything on the linksys that says it's rejecting or dropping the packets and ssh to any other box on the 192.168.20.x network works.

I can't find anything on the server at 192.168.20.42 that indicates the packets are even getting there.  

Arggh.

Any clue would help at this point as I'm fairly convinced the ubuntu server at 192.168.20.42.

---

### Post by MakOwner on 2011-11-20
OK, I have this working again, but it's not solved.
I'd *REALLY* like to understand how this happened, and if anyone can help me figure this out...

I started working backwards through the changes I had been making on the server before connectivity no longer worked.  The last changes I had been working on was getting jumbo frames set up on a bonded interface.

I had added "mtu 9000" in the /etc/interfaces file with no change to the MTU after reboot.
I added a /etc/modprobe.d/bonding.conf file.  I added the bond option and mtu option.
Reboot caused no change in the MTU but I could no longer connect from the wireless network, but connections from everywhere else worked fine.

This is the current interfaces file - note that mtu has been commented out.
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp
auto bond0
iface bond0 inet dhcp
slaves eth0 eth1
#mtu 9000
# LACP confuration
bond_mode 6
bond_miimon 500

```

This is what the bonding.conf file looked like in two iterations:
```

first:
$ cat bonding.conf 
alias bond0 bonding
  options bonding mode=6 mtu 9000 

second:
$ cat bonding.conf 
alias bond0 bonding
  options bonding mode=6

```

The bonding.conf file has been removed from the /etc/modprobe.d directory and connectivity works...

---

### Post by hawkmage on 2011-11-20
Unless all of your routers, switches and devices support jumbo frames I would not increase the MTU.  

If you have devices that support large packets connected to a device that doesn't you will get the initial Sync packets to establish the connection but once it really tries to send data it can't get there and you get the connection timeout.

---

### Post by MakOwner on 2011-11-21
> **hawkmage said:**
> Unless all of your routers, switches and devices support jumbo frames I would not increase the MTU.  

If you have devices that support large packets connected to a device that doesn't you will get the initial Sync packets to establish the connection but once it really tries to send data it can't get there and you get the connection timeout.

Wouldn't a change in packet size result in a change in the ifconfig output on the interface(s)?  That didn't change, nor did I get any change in performance on transfer between two servers plugged into the same switch.
Without both set up for jumbo frames I wouldn't expect that to change.
I did expect to see a change in the MTU displayed on the interface however and was basing the success of the setting on that.

---

### Post by hawkmage on 2011-11-21
But does your wireless router support jumbo frames on the wireless connections?

---

### Post by MakOwner on 2011-11-21
> **hawkmage said:**
> But does your wireless router support jumbo frames on the wireless connections?

It does, but I never made any change on the device.

And that appears to be the issue that jumbo frames weren't passed across the wireless interface.  If the frame size did change on the server.

Now the question becomes, if I set up jumbo frames on a bonded interface aside from network traffic failing - sometimes - how can I tell the MTU size has changed?

The ifconfig display continued to show MTU 1500 on the slaves and the bonded interface.  Communications to other servers on the same subnet without jumbo frames set worked as normal - granted, they were on the same dumb gig switch.  This was on an older 24 port rackmount netgear switch.

---

