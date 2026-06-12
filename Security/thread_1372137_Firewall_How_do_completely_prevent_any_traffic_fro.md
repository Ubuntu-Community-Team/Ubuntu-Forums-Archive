---
title: "Firewall: How do completely prevent any traffic from network?"
date: 2010-01-04
forum: Security
---

### Post by abcuser on 2010-01-04
Hi,
I have Ubuntu 8.04 as virtual host. On this host I have installed VirtualBox virtualization software. I have installed Windows XP as virtual machine and installed HTTP server.

I would like temporally disable all network connections to host and virtual machine.
So on Ubuntu host I have set firewall settings:
```
sudo iptables -F  (to flush - delete all firewall settings)
sudo iptables -P INPUT DROP (to disable all input traffic)
sudo iptables -P FORWARD DROP (to disable all forward traffic)
sudo iptables -P OUTPUT DROP (to disable all output traffic

```

List firewall settings:
```
sudo iptables -L -n -v
```
outputs:
```

Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 

``` 

I see I can't connect to internet from Ubuntu host, sample "sudo apt-get update" returns error.

But I can still connect to my HTTP server witch is running in virtual machine. This is strange. Why isn't this traffic prevented? What should I do to prevent all of the traffic to virtual machine and host?

I have two network adapters (ifconfig command): lo (local) and eth0 (ethernet). VirtualBox is using eth0 to communicate to internet.

P.S. There is no other firewall installed on Ubuntu like ufw.
Regards

---

### Post by overdrank on 2010-01-06
Moved to Security Discussions and bumped :)

---

### Post by BkkBonanza on 2010-01-06
What networking mode have you selected for the guest network adapter?

---

### Post by iponeverything on 2010-01-06
you might try:

```

iptables -t nat -P PREROUTING DROP
iptables -t nat -P POSTROUTING DROP

```

---

### Post by bodhi.zazen on 2010-01-06
Change the default policy back to accept (not DROP)

then

```
sudo iptables -A INPUT -s windows_ip_address -j DROP
sudo iptables -A OUTPUT -d windows_ip_address -j DROP
```

---

### Post by bodhi.zazen on 2010-01-06
> **iponeverything said:**
> you might try:

```

iptables -t nat -P PREROUTING DROP
iptables -t nat -P POSTROUTING DROP

```

Or this if you are using NAT ^^

---

### Post by abcuser on 2010-01-07
> **BkkBonaza said:**
> What networking mode have you selected for the guest network adapter?
Hi,
virtual guest uses "bridged addapter". This means that guest have its own IP address. I am not using NAT.
Regards

---

### Post by abcuser on 2010-01-07
> **iponeverything said:**
> you might try:

```

iptables -t nat -P PREROUTING DROP
iptables -t nat -P POSTROUTING DROP

```
Hi,
I have tested this and I can still connect to my HTTP server running in guest on server from my notebook.

If I understand correctly this is for NAT network connection. I use bridged connection, not nat.
Regards

---

### Post by abcuser on 2010-01-07
> **bodhi.zazen said:**
> Change the default policy back to accept (not DROP)

then

```
sudo iptables -A INPUT -s windows_ip_address -j DROP
sudo iptables -A OUTPUT -d windows_ip_address -j DROP
```
Hi,
I have tested this and I can still connect to http server from my notebook. If I understand correctly iptables, then my command (drop all three connection) is way more restrictive then yours, because my commands drop all connections from input/forward/output and yours only drop connections from one source/destination IP address.

Any other idea how I could prevent all the traffic to my host and guest from other world (like my notebook)?
Regards

---

### Post by BkkBonanza on 2010-01-07
I suspected maybe bridged mode. I've had a look here because I use that too. It seems the virtual driver for the bridged mode network is at a very low level and does not go through iptables on the host. At least that's what I surmise from some tests I did.

This seems to imply in this case you would have to use a firewall on the guest to protect it. But an easier way if you want temporary control from the host would be to use VBoxManage commands to disable/enable guest networking when needed.

eg.

VBoxManage vmname modifyvm --nic1 none
VBoxManage vmname modifyvm --nic1 bridged

or perhaps 

VBoxManage vmname controlvm setlinkstate1 off
VBoxManage vmname controlvm setlinkstate1 on

I haven't tested if this works while it's running but I think it should as you can do the same manually from the guest control panel at bottom of it's window.

---

### Post by bodhi.zazen on 2010-01-07
Is "host only" what you want ?

[http://opensourceexperiments.wordpress.com/2008/04/18/virtualbox-case-study-making-host-only-networking-work-between-two-ubuntu-guest-os-virtual-machine-on-windows-vista-host/](http://opensourceexperiments.wordpress.com/2008/04/18/virtualbox-case-study-making-host-only-networking-work-between-two-ubuntu-guest-os-virtual-machine-on-windows-vista-host/)

You can create a private network as well.

You could firewall the guest as well.

---

### Post by EJeanmaire on 2010-01-07
> **abcuser said:**
> Hi,
I have Ubuntu 8.04 as virtual host. On this host I have installed VirtualBox virtualization software. I have installed Windows XP as virtual machine and installed HTTP server.

I would like temporally disable all network connections to host and virtual machine.
So on Ubuntu host I have set firewall settings:
```
sudo iptables -F  (to flush - delete all firewall settings)
sudo iptables -P INPUT DROP (to disable all input traffic)
sudo iptables -P FORWARD DROP (to disable all forward traffic)
sudo iptables -P OUTPUT DROP (to disable all output traffic

```

List firewall settings:
```
sudo iptables -L -n -v
```
outputs:
```

Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 

``` 

I see I can't connect to internet from Ubuntu host, sample "sudo apt-get update" returns error.

But I can still connect to my HTTP server witch is running in virtual machine. This is strange. Why isn't this traffic prevented? What should I do to prevent all of the traffic to virtual machine and host?

I have two network adapters (ifconfig command): lo (local) and eth0 (ethernet). VirtualBox is using eth0 to communicate to internet.

P.S. There is no other firewall installed on Ubuntu like ufw.
Regards

I guess I don't fully understand your motive, but what if you just take eth0 down... sudo ifconfig eth0 down.... or edit the /etc/hosts.deny file

---

### Post by Fire_Chief on 2010-01-07
Or you could just unplug the cable...

---

### Post by __p1n__ on 2010-01-07
I'm a bit confused by your use of terminology i.e. virtual host.  Is the host ubuntu instance itself running within a virtual machine or is it running natively on the h/w?  Also, what is the scope of network isolation required?  Are you looking to block all traffic to/from the host os as well as to/from the guest os or just between the physical network and the guest os?

I'm going to presume that you mean:

1. the linux host os is running natively
2. the winxp os is a guest of the linux host os
3. you want to isolate traffic between the physical network and the guest os but preserve traffic between the host os and the physical network

Inside the host os with uid=0 priviledges:

# brctl show
# ifconfig [bridgename] down

where [bridgename] is the name of the relevant bridge displayed in the brctl show command.  Assuming that you don't delete it you can subsequently restore the bridge at any time by entering the command:

# ifconfig [bridgename] up

---

