---
title: "LXC Containers"
date: 2011-11-21
forum: Virtualisation
---

### Post by svtguy88 on 2011-11-21
Alright, I'm trying to configure a few containers using LXC.  I followed a number of guides that I found online, but I'm running into a dead end, and am just about ready to start pulling my hair out.

The container starts fine, or at least appears to.  I don't know enough about LXC to start looking for log files though.  Anyway, after starting the container, I try to connect to it by ssh'ing to 192.168.80.2 (the address that, if I set everything up correctly, belongs to this container), but it says connection refused.

Also, if I try to run "lxc-console -n <container_name>" I'm left with an unusable terminal.  I can type, and hitting enter makes a new line, but I can't seem to send any commands.

The following is my host-side /etc/network/interfaces file:

```
#set up local loopback interface
auto br0 lo eth4 eth3 eth2 eth1 eth0 
iface lo inet loopback

#set up external (internet) interface
iface eth4 inet dhcp
	#gateway 192.168.10.1

#set up internal (network) interface
iface eth3 inet static
	address 192.168.40.1
	netmask 255.255.255.0
	broadcast 192.168.40.255
	network 192.168.40.0

iface eth2 inet static
	address 192.168.30.1
	netmask 255.255.255.0
	broadcast 192.168.30.255
	network 192.168.30.0

iface eth1 inet static
	address 192.168.20.1
	network 192.168.20.0
	netmask 255.255.255.0
	broadcast 192.168.20.255

iface eth0 inet static
	address 192.168.10.1
	netmask 255.255.255.0
	broadcast 192.168.10.255
	network 192.168.10.0
	
#wireless
iface wlan0 inet static
	address 192.168.90.1
	netmask 255.255.255.0
	broadcast 192.168.90.255
	network 192.168.90.0
	#wireless-mode ad-hoc
        #wireless-essid PoopDeck
	#channel 11
	#wireless-key 12345
	
#bridge for LXC
iface br0 inet static
	bridge-ports eth3
	bridge_maxwait 0
	address 192.168.80.1
	network 192.168.80.0
	netmask 255.255.255.0
	broadcast 192.168.80.255

```

The external interface is eth4.  eth0 - eth3 are internal, and my bridge attaches to eth3 (as it is a DMZ).

The following is my /var/lib/lxc/config file:

```
lxc.utsname = PE1800_email0
lxc.tty = 4
lxc.network.type = veth
lxc.network.flags = up
lxc.network.link = br0
lxc.network.name =
lxc.network.mtu = 1500
lxc.network.ipv4 = 192.168.80.2/24
lxc.rootfs = /etc/lxc/rootfs.PE1800_email0
lxc.mount = /etc/lxc/fstab.PE1800_email0
lxc.cgroup.devices.deny = a
# /dev/null and zero
lxc.cgroup.devices.allow = c 1:3 rwm
lxc.cgroup.devices.allow = c 1:5 rwm
#consoles
lxc.cgroup.devices.allow = c 5:1 rwm
lxc.cgroup.devices.allow = c 5:0 rwm
lxc.cgroup.devices.allow = c 4:0 rwm
lxc.cgroup.devices.allow = c 4:1 rwm
# /dev/{,u}random
lxc.cgroup.devices.allow = c 1:9 rwm
lxc.cgroup.devices.allow = c 1:8 rwm
# /dev/pts/* - pts namespaces are "coming soon"
lxc.cgroup.devices.allow = c 136:* rwm
lxc.cgroup.devices.allow = c 5:2 rwm
# rtc
lxc.cgroup.devices.allow = c 254:0 rwm
```

The following is my guest-side /etc/network/interfaces file:

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo eth0
iface lo inet loopback

iface eth0 inet static
inet 192.168.80.2
network 192.168.80.1
netmask 255.255.255.0


```

Any and all help would be appreciated.  I'm reasonaly new to Linux networking (at least the more in-depth stuff).  Oh, and for the record, right now my system is set up using Shorewall Firewall (IP masquerading and such is all set up).

---

### Post by svtguy88 on 2011-11-22
No one with any input?  I guess I'll try and find an LXC message board...

---

### Post by svtguy88 on 2011-11-22
Got myself a bit further.  The problem before was I forgot to assign a root password for the container, and I was trying to log in to the root account.

Anyway...now I'm left with this:

```
pat@PowerEdge1800:~$ sudo ssh root@192.168.80.2
root@192.168.80.2's password: 
PTY allocation request failed on channel 0
Welcome to Ubuntu 11.10 (GNU/Linux 3.0.0-13-generic x86_64)

 * Documentation:  https://help.ubuntu.com/
stdin: is not a tty

```

I've already tried solutions offered [here]("http://www.emanuelis.eu/2010/06/04/how-to-fix-lxcs-error-pty-allocation-request-failed-stdin-is-not-a-tty/") and [here]("http://forums.quantact.com/viewtopic.php?f=35&t=1149")....

---

