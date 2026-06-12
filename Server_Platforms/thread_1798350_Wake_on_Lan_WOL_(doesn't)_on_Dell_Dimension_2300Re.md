---
title: "Wake on Lan WOL (doesn't) on Dell Dimension 2300/Realtek 8139"
date: 2011-07-06
forum: Server Platforms
---

### Post by cjkenworthy on 2011-07-06
Hello there.

I've been trying to get Wake On Lan (WOL) working on a Dell Dimension 2300 running Ubuntu server 11.04 (Natty). But I'm having no success. My computer just won't respond to magic packets.

Please can someone help? I've given as much information as possible below.

**lspci -tv**

```

-[0000:00]-+-00.0  Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
           +-02.0  Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
           +-1d.0  Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
           +-1d.7  Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
           +-1e.0-[01]--+-04.0  Ralink corp. RT2561/RT61 802.11g PCI
           |            \-06.0  Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
           +-1f.0  Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
           +-1f.1  Intel Corporation 82801DB (ICH4) IDE Controller
           +-1f.3  Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
           \-1f.5  Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller

```

My ethernet card is WOL capable, as shown by 

**ethtool eth0**

```

	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 32
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000007 (7)
			       drv probe link
	Link detected: yes

```

The ethernet device is a Realtek 8139 as shown in

**lspci**

```

01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

**ifconfig **

```

eth0      Link encap:Ethernet  HWaddr 00:40:f4:3c:88:49  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fe3c:8849/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1403 errors:0 dropped:0 overruns:0 frame:0
          TX packets:743 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:133132 (133.1 KB)  TX bytes:160142 (160.1 KB)
          Interrupt:18 Base address:0xc000 

```

I auto-enable WOL at boot-up and power down in /etc/network/interfaces with:

```

post-up /usr/bin/activateWOL
post-down /usr/bin/activateWOL

```

That file points to the script activateWOL which contains:

```

#!/bin/bash
ethtool -s eth0 wol g

```

Based on lspci I manually "enabled" ACPI devices with:

sudo sh -c "echo HUB0 > /proc/acpi/wakeup"
sudo sh -c "echo PCI0 > /proc/acpi/wakeup"

**cat /proc/acpi/wakeup**

```

Device	S-state	  Status   Sysfs node
PCI0	  S5	*enabled   no-bus:pci0000:00
HUB0	  S5	*enabled   pci:0000:00:1e.0
USB0	  S3	*disabled  pci:0000:00:1d.0
USB1	  S3	*disabled  pci:0000:00:1d.1
USB2	  S3	*disabled  pci:0000:00:1d.2
USB3	  S3	*disabled  pci:0000:00:1d.7
MODM	  S5	*disabled  
UAR1	  S5	*disabled  pnp:00:08

```

I even went as far as "enabling" the ethernet device itself with

```

sudo sh -c "echo enabled > /sys/devices/pci0000\:00/0000\:00\:1e.0/0000\:01\:06.0/power/wakeup"
```

I also tried stopping network manager going to sleep by commenting out lines in suspend_nm() 

/usr/lib/pm-utils/sleep.d/55NetworkManager

```

#!/bin/sh
# If we are running NetworkManager, tell it we are going to sleep.
# TODO: Make NetworkManager smarter about how to handle sleep/resume
#       If we are asleep for less time than it takes for TCP to reset a
#       connection, and we are assigned the same IP on resume, we should
#       not break established connections.  Apple can do this, and it is
#       rather nifty.

. "${PM_FUNCTIONS}"

suspend_nm()
{
	# Tell NetworkManager to shut down networking
        #printf "Having NetworkManager put all interaces to sleep..."
	#dbus_send --print-reply --system                         \
	#	--dest=org.freedesktop.NetworkManager  \
	#	/org/freedesktop/NetworkManager        \
	#	org.freedesktop.NetworkManager.sleep && \
	#   echo Done. || echo Failed.
}

resume_nm()
{
	# Wake up NetworkManager and make it do a new connection
	printf "Having NetworkManager wake interfaces back up..."
        dbus_send --print-reply --system                        \
		--dest=org.freedesktop.NetworkManager \
		/org/freedesktop/NetworkManager       \
		org.freedesktop.NetworkManager.wake && \
	    echo Done. || echo Failed.
}

case "$1" in
	hibernate|suspend)
		suspend_nm
		;;
	thaw|resume)
		resume_nm
		;;
	*) exit $NA
		;;
esac

```

When I shutdown or suspend with the commands:

[B]halt
pm-suspend[/B]

The computer shuts down or suspends correctly (respectively), but when I send a magic packet (from my spare Ubuntu laptop on the same LAN) using:

**wakeonlan 00:40:f4:3c:88:49**

The Dell Ubuntu server fails to wake up. Nothing happens at all. There is no LED activity on the back of the NIC card. However, I did try installing Windows XP to test the card and WOL did work correctly (when I ticked "allow this device to bring the computer out of sleep" in device manager). I used the same wakeonlan command from my spare Ubuntu laptop. (No LEDs were on the Dell Ubuntu server NIC when it was running Windows XP and in suspend/off)

By the way, I can ping the Dell Ubuntu server when it is on and can ssh in correctly. It just won't wake on LAN when I send a magic packet.

Any ideas? Thank you for your help.

---

### Post by egpetrich on 2011-07-08
Does your BIOS setup offer you any control over allowing devices to wake the computer? (I know you said that thinks work okay with WinXP, but I have a recollection that WinXP sometimes does stuff for you that Linux does not.)

---

### Post by cjkenworthy on 2011-07-10
Hello. Yes I enabled the BIOS setting that reads:

"Wake-Up by PCI device"

There are no other reference to wake on LAN that I can find. There is an option to 'boot from LAN' so I enabled it anyway.

Thanks.

---

### Post by Gyokuro on 2011-07-10
It seems that's a driver problem as otherwise WOL would not work on XP either. Is it possible that you can try to shutdown your server via:

sudo shutdown -h now

and afterwards you send the WOL wake up.

---

### Post by brighty22 on 2011-07-10
Please post the contents of /etc/network/interfaces. There might be something missing from it.

---

### Post by ftesser on 2011-07-13
I have similar problems, I can't neither WOL after shutting down from Ubuntu 11.04. It worked with Ubuntu 10.10. To me seem something is wrong with natty and WOL, see:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/714417](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/714417)
[http://askubuntu.com/questions/49281/powernap-and-wake-on-lan](http://askubuntu.com/questions/49281/powernap-and-wake-on-lan)
[http://ubuntuforums.org/showthread.php?t=814939&highlight=wol&page=7](http://ubuntuforums.org/showthread.php?t=814939&highlight=wol&page=7)

---

### Post by kevinthecomputerguy on 2011-07-13
I see you already have it in startup, but this way works for me as it loads much later, and or maybe your missing a leading sudo

I put that command in /etc/rc.local

ethtool -s eth0 wol g

#It needs to run everytime the computer restarts, or else it forgets when you reboot.

*note, you might need to put sudo before it on a ubuntu box
sudo ethtool -s eth0 wol g

---

### Post by brighty22 on 2011-07-13
^ I put that line, with sudo, in /etc/network/interfaces and it works perfectly for me. Hence why I asked for the contents of the file ;)

---

### Post by cjkenworthy on 2011-07-14
I tried:

```
sudo shutdown -h now
```

to halt the server, then sent a WOL command: 

```
wakeonlan 00:40:f4:3c:88:49
```

But nothing happened.

Here's my /etc/network/interfaces:

```

cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

#Wired network (change DHCP for static address)
auto eth0
iface eth0 inet dhcp
#http://www.linuxquestions.org/questions/linux-networking-3/howto-make-wake-on-lan-wol-work-712283/
post-down /usr/bin/activateWOL

#Wireless (do not use when running as server as no WOL)
auto wlan0
iface wlan0 inet dhcp

```

I strongly suspect that this is a driver problem, as WOL worked with Windows XP on this same computer and NIC.

---

### Post by kevinthecomputerguy on 2011-07-14
Do you happen to have more than one network card in this box? (doesnt look like it) but i use etherwake (sudo apt-get install etherwake) and it fails with 2 nics unless you specify which NIC is LAN facing.
 
here is the one that works for me.
 
etherwake -b -i eth1 00:00:a0:a9:00:5c
 
You would probably want to change eth1 to eth0
 
or sudo etherwake -b -i eth1 00:00:a0:a9:00:5c
 
if only one nic, try
 
sudo etherwake -b 00:00:a0:a9:00:5c
 
*It might also help to set the brodcast address in your interfaces file, maybe dhcp isnt supplying that.
 
example
bcast 192.168.1.255

---

