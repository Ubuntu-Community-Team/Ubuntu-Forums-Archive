---
title: "Adding new network card"
date: 2011-12-03
forum: Server Platforms
---

### Post by jdawgvh on 2011-12-03
Hi guys,
I'm running 11.10 server edition and I decided to put in a new network card.  I'm having some trouble with that so I'm hoping that you guys can give me a hand.  I purchased the LAN card at this web address:
[HTML]
http://www.startech.com/Networking-IO/Adapter-Cards/10100-1000-Mbps-32-bit-PCI-Gigabit-Ethernet-Card~ST1000BT32
[/HTML]

I downloaded the driver for it and tried installing it.  I've copied and pasted the README from the driver below.  I have completed all of the commands in bold but I can't get any further.

> [B]<Linux device driver for Realtek Ethernet controllers>

	This is the Linux device driver released for RealTek RTL8169S/8110S, RTL8169SB/8110SB, and RTL8110SC.

<Requirements>

	- kernel source tree (supported Linux kernel 2.6.x/2.4.20 and latter)
	- compiler/binutils for kernel compilation

<Quick install with proper kernel settings>
	Check whether the built-in driver, r8169.ko(or r8169.o for linux kernel 2.4.x), is installed. 
		# lsmod | grep r8169

	If it is installed, please remove it.
		# rmmod r8169
	note: If the built-in driver cannot removed by rmmod, please edit /etc/modprobe.conf and comment 'alias eth0 r8169'. Then, remove it again or reboot your computer.

	Unpack the tarball :
		# tar vjxf r8169-6.aaa.bb.tar.bz2

	Change to the directory:
		# cd r8169-6.aaa.bb

	If you are running the target kernel, then you should be able to do :

		# make clean modules	(as root or with sudo)
		# make install
		# depmod -a
		# modprobe r8169

	You can check whether the driver is loaded by using following commands.

		# lsmod | grep r8169
		# ifconfig -a

	If there is a device name, ethX, shown on the monitor, the linux 
	driver is loaded. Then, you can use the following command to activate 
	the ethX.

		# ifconfig ethX up

		, where X=0,1,2,...[/B]

  
<Set the network related information>
	1. Set manually
		a. Set the IP address of your machine.

			# ifconfig ethX "the IP address of your machine" 

		b. Set the IP address of DNS.

		   Insert the following configuration in /etc/resolv.conf.
		
			nameserver "the IP address of DNS"

		c. Set the IP address of gateway.

			# route add default gw "the IP address of gateway"

	2. Set by doing configurations in /etc/sysconfig/network-scripts
	   /ifcfg-ethX for Redhat and Fedora, or /etc/sysconfig/network
	   /ifcfg-ethX for SuSE. There are two examples to set network 
	   configurations.

		a. Fix IP address:
			DEVICE=eth0
			BOOTPROTO=static
			ONBOOT=yes
			TYPE=ethernet
			NETMASK=255.255.255.0
			IPADDR=192.168.1.1
			GATEWAY=192.168.1.254
			BROADCAST=192.168.1.255

		b. DHCP:
			DEVICE=eth0
			BOOTPROTO=dhcp
			ONBOOT=yes	

<Change the MAC address>
	There are two ways to modify the MAC address of the NIC.
	1. Use ifconfig:

		# ifconfig ethX hw ether YY:YY:YY:YY:YY:YY

	   , where X is the device number assigned by Linux kernel, and
		  YY:YY:YY:YY:YY:YY is the MAC address assigned by the user.

	2. Use ip:

		# ip link set ethX address YY:YY:YY:YY:YY:YY

	   , where X is the device number assigned by Linux kernel, and
		  YY:YY:YY:YY:YY:YY is the MAC address assigned by the user.

<Force Link Status>

	1. Force the link status when insert the driver.

	   If the user is in the path ~/r8169, the link status can be forced 
	   to one of the 5 modes as following command.

		# insmod ./src/r8169.ko speed=SPEED_MODE duplex=DUPLEX_MODE autoneg=NWAY_OPTION

		, where
			SPEED_MODE	= 1000	for 1000Mbps
					= 100	for 100Mbps
					= 10	for 10Mbps
			DUPLEX_MODE	= 0	for half-duplex
					= 1	for full-duplex
			NWAY_OPTION	= 0	for auto-negotiation off (true force)
					= 1	for auto-negotiation on (nway force)
		For example:

			# insmod ./src/r8169.ko speed=100 duplex=0 autoneg=0

		will force PHY to operate in 100Mpbs Half-duplex(nway force).

	2. Force the link status by using ethtool.
		a. Insert the driver first.
		b. Make sure that ethtool exists in /sbin.
		c. Force the link status as the following command.

			# ethtool -s ethX speed SPEED_MODE duplex DUPLEX_MODE autoneg NWAY_OPTION

			, where
				SPEED_MODE	= 1000	for 1000Mbps
						= 100	for 100Mbps
						= 10	for 10Mbps
				DUPLEX_MODE	= half	for half-duplex
						= full	for full-duplex
				NWAY_OPTION	= off	for auto-negotiation off (true force)
						= on	for auto-negotiation on (nway force)

		For example:
		
			# ethtool -s eth0 speed 100 duplex full autoneg on

		will force PHY to operate in 100Mpbs Full-duplex(nway force).

<Jumbo Frame>
	Transmitting Jumbo Frames, whose packet size is bigger than 1500 bytes, please change mtu by the following command.

	# ifconfig ethX mtu MTU

	, where X=0,1,2,..., and MTU is configured by user. RTL8110S/SB/SC supports Jumbo Frame size (MTU) up to 7 kBytes.

	For example, to configure jumbo frame as 7 kBytes, use the following command:
		
		# ethtool eth0 mtu 7168

	If there is another computer inatalled RTL8169S/SB/SC and its jumbo size is also configured to be 7 kBytes, the Linux can ping it by using following command.

		# ping IP_ADDRESS -s 7126 -M do





When I type in ifconfig I get the following result:

> 
eth0      Link encap:Ethernet  HWaddr 00:13:20:d2:71:89
          inet addr:192.168.1.125  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:fed2:7189/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5713 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2072 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:376014 (376.0 KB)  TX bytes:286224 (286.2 KB)

eth1      Link encap:Ethernet  HWaddr 00:0a:cd:1e:77:7d
          inet addr:192.168.1.125  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0x6f00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:688 (688.0 B)  TX bytes:688 (688.0 B)

virbr0    Link encap:Ethernet  HWaddr 72:45:50:cd:95:85
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


I think this adapter got set up as ETH1 but I cannot communicate with it.

---

### Post by rubylaser on 2011-12-04
eth0 and 1 are sharing the same ip address, so you have a conflict that you'll want to fix before doing anything else.  What do you have here...

```
cat /etc/network/interfaces
```

---

### Post by drdos2006 on 2011-12-04
Have a look at these. Might help.

[http://ubuntuforums.org/showthread.php?t=1840543](http://ubuntuforums.org/showthread.php?t=1840543)
[http://ubuntuforums.org/showthread.php?t=1842656](http://ubuntuforums.org/showthread.php?t=1842656)

regards

---

### Post by jdawgvh on 2011-12-04
after I posted last night I continued hunting on Google.  I found an article that looked like it helped to set this up.  I ended up with the following /etc/network/interfaces file:

> 

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#pre-u iptables -A OUTPUT -p tcp -m owner --uid-owner local -j DROP
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp



I added the last two lines last night but they do not work.

---

### Post by drdos2006 on 2011-12-04
It appears that you have to bond the NICs together, check out the links I gave you.

regards

---

### Post by jdawgvh on 2011-12-04
That was it.  Thanks!  The first link you sent solved my problem.

---

### Post by drdos2006 on 2011-12-04
No problem. Please mark your topic as solved. It could help someone else.

regards

---

