---
title: "Correct DHCP Server Configuration for a Router"
date: 2013-03-13
forum: Ubuntu Development Version
---

### Post by BhimaPandava on 2013-03-13
I'm trying to setup a 13.04 server edition based router.  It has 4 network ports (eth0-eth3) and an USB WWAN modem (ppp0).

Currently my /etc/dhcp/hdcpd.conf reads:
```

[FONT=Courier New]ddns-update-style none;[/FONT][FONT=Courier New][SIZE=2]
#option definitions common to all supported networks...[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]#optiondomain-name-servers ns1.example.org, ns2.example.org;

[/SIZE][/FONT][FONT=Courier New]option domain-name "home";[/FONT][FONT=Courier New][SIZE=2]
[/SIZE][/FONT][FONT=Courier New]option routers 192.168.0.1; #Default Gateway[/FONT]
[FONT=Courier New]option domain-name-servers 192.168.0.1;[/FONT]
[FONT=Courier New][SIZE=2]default-lease-time600;[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]max-lease-time7200;[/SIZE][/FONT]


[FONT=Courier New][SIZE=2]#If this DHCP server is the official DHCP server for the local[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]#network, the authoritative directive should be uncommented.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]authoritative;[/SIZE][/FONT]


[FONT=Courier New][SIZE=2]#Use this to send dhcp log messages to a different log file (you also[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]#have to hack syslog.conf to complete the redirection).[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]log-facilitylocal7;[/SIZE][/FONT]


[FONT=Courier New][SIZE=2]subnet192.168.0.0 netmask 255.255.255.0 {[/SIZE][/FONT]
       [FONT=Courier New][SIZE=2]    option subnet-mask                     255.255.255.0;[/SIZE][/FONT]
       [FONT=Courier New][SIZE=2]    option broadcast-address               192.168.0.255;[/SIZE][/FONT]
    
[FONT=Courier New][SIZE=2]    range 192.168.0.51 192.168.0.61;   #DHCP Range to assign[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]}[/SIZE][/FONT]
```[FONT=Courier New][SIZE=2]

[/SIZE][/FONT][SIZE=2]I have edited my /etc/default/isc-dhcp-server to read:[/SIZE][FONT=Courier New][SIZE=2]

[/SIZE][/FONT]```

[FONT=courier new][SIZE=2]# On what interfacesshould the DHCP server (dhcpd) serve DHCP requests?[/SIZE][/FONT]
[FONT=courier new][SIZE=2]#       Separate multipleinterfaces with spaces, e.g. "eth0 eth1".[/SIZE][/FONT]
[FONT=courier new][SIZE=2]INTERFACES="[/SIZE][/FONT][FONT=courier new]eth0 eth1 eth2 eth3[/FONT][FONT=courier new][SIZE=2]"[/SIZE][/FONT]

```
[FONT=Courier New][SIZE=2]
[/SIZE][/FONT][SIZE=2]and my /etc/network/interfaces reads: [/SIZE][FONT=Courier New][SIZE=2]

[/SIZE][/FONT]```
[FONT=Courier New][SIZE=2]#The primary network interface[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]auto ppp0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iface ppp0 inet dhcp[/SIZE][/FONT]


[FONT=Courier New][SIZE=2]# LAN Ports served by DHCPD[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]auto eth0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]    iface eth0 inet static[/SIZE][/FONT]
        [FONT=Courier New][SIZE=2]    address 192.168.0.1[/SIZE][/FONT]
        [FONT=Courier New][SIZE=2]    netmask 255.255.255.0[/SIZE][/FONT]
        [FONT=Courier New][SIZE=2]    gateway 192.168.0.1[/SIZE][/FONT]


[FONT=Courier New][SIZE=2]auto eth1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]    iface eth1 inet static[/SIZE][/FONT]
        [FONT=Courier New][SIZE=2]    address 192.168.0.2[/SIZE][/FONT]
        [FONT=Courier New][SIZE=2]    netmask 255.255.255.0[/SIZE][/FONT]
        [FONT=Courier New][SIZE=2]    gateway 192.168.0.1[/SIZE][/FONT]


[FONT=Courier New][SIZE=2]auto eth2[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]    iface eth2 inet static[/SIZE][/FONT]
        [FONT=Courier New][SIZE=2]    address 192.168.0.3[/SIZE][/FONT]
        [FONT=Courier New][SIZE=2]    netmask 255.255.255.0[/SIZE][/FONT]
        [FONT=Courier New][SIZE=2]    gateway 192.168.0.1

[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]auto eth3[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]    iface eth0 inet static[/SIZE][/FONT]
        [FONT=Courier New][SIZE=2]    address 192.168.0.4[/SIZE][/FONT]
        [FONT=Courier New][SIZE=2]    netmask 255.255.255.0[/SIZE][/FONT]
        [FONT=Courier New][SIZE=2]    gateway 192.168.0.1[/SIZE][/FONT]



```

This doesn't work for me.  The command dhcpd -t /etc/dhcp/dhcpd.conf returns: "/etc/dhcp/dhcpd.conf: interface name too long (is 20)"

sudo tail /var/log/syslog yields the following (repeats for each lan port): 
```
[FONT=courier new]Mar 13 13:20:33 home dhcpd: No subnet declaration for eth0 (no IPv4 addresses).[/FONT]
[FONT=courier new]Mar 13 13:20:33 home dhcpd: ** Ignoring requests on eth0.  If this is not what[/FONT]
[FONT=courier new]Mar 13 13:20:33 home dhcpd:    you want, please write a subnet declaration[/FONT]
[FONT=courier new]Mar 13 13:20:33 home dhcpd:    in your dhcpd.conf file for the network segment[/FONT]
[FONT=courier new]Mar 13 13:20:33 home dhcpd:    to which interface eth0 is attached. **[/FONT]

```
If anyone could point out where I went wrong, I'd appreciate it.

---

### Post by Bucky Ball on 2013-03-13
*Thread moved to **Ubuntu +1 (Raring Ringtail)***

13.04 not yet released (end of April). Just wondering if you might be better with an LTS release for a server. ;)

---

### Post by grahammechanical on 2013-03-13
I know nothing about networking but I do see this: > [COLOR=#000000][FONT=courier new][SIZE=2]INTERFACES="[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=courier new]eth0 eth1 eth2 eth3[/FONT][/COLOR][COLOR=#000000][FONT=courier new][SIZE=2]"[/SIZE][/FONT][/COLOR] and I compare that with this: > [COLOR=#000000][FONT=Courier New]autoeth0[/FONT][/COLOR] and I do wonder if that mismatch is the reason for this message: > [COLOR=#000000][FONT=courier new]please write a subnet declaration [/FONT][/COLOR][COLOR=#000000][FONT=courier new]in your dhcpd.conf file for the network segment [/FONT][/COLOR][COLOR=#000000][FONT=courier new]to which interface eth0 is attached.[/FONT][/COLOR] It is just an observation from an uneducated tester. Regards.

---

### Post by zika on 2013-03-13
> **grahammechanical said:**
> I know nothing about networking but I do see this:  and I compare that with this:  and I do wonder if that mismatch is the reason for this message:  It is just an observation from an uneducated tester. Regards.Also, there is no command/option ```
autoeth0
```That should be```
auto ethx
```x in {0,1,2,3...}
Also,```
[COLOR=#000000]ifaceeth0 inet static[/COLOR]
```[FONT=arial][COLOR=#000000]should be[/COLOR]```
[COLOR=#000000]iface ethx inet static[/COLOR]
```[/FONT]

---

### Post by BhimaPandava on 2013-03-13
I think you are making a good point.  I could not figure out how to indicate "all wired ethernet ports" in network/interfaces so I just listed them all individually but that appears to interfere with the dhcpd.conf subnet declaration.  Unfortunately all the how-tos I've found so far only use one nic for listening for DHCP requests.  I want anything that is plugged in to any of the 4 ethernet ports to be assigned an IP in the subnet.

No wait... I just twigged that in many places there are spaces missing in what I had pasted into my submission. ("autoeth0" should read "auto eth0"). I've gone through and tried to fix that in my submission but they were there all along in my configuration.

---

### Post by BhimaPandava on 2013-03-13
Great!  Just to be clear:  in /etc/default/isc-dhcp-server I should use "[FONT=Courier New]INTERFACES="eth**x**"
[FONT=arial]
[/FONT][/FONT]and for etc/network/interfaces[FONT=arial]:
[/FONT][FONT=Courier New][SIZE=2]#LAN Ports served by DHCPD[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]auto ethx[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iface ethx inet static[/SIZE][/FONT]
**        [FONT=Courier New][SIZE=2]address 192.168.0.1[/SIZE][/FONT]**
        [FONT=Courier New][SIZE=2]netmask 255.255.255.0[/SIZE][/FONT]
        [FONT=Courier New][SIZE=2]gateway 192.168.0.1

[/SIZE][/FONT]How do I indicate that each of the 4 ethernet ports should receive IP addresses? (I'm assuming they should be static and must be unique)

Why are the spaces in my pasted text disappearing?

---

### Post by SeijiSensei on 2013-03-13
It sounds like you only have one physical network and a single subnet, 192.168.0.0/24.  If so, bind dhcpd to just one of the interfaces, presumably eth0.

Also if you have a computer with multiple network cards, you're going to have problems if they are all connected to the same subnet.  Usually a so-called "multi-homed" server would have each network adapter assigned to a different IP subnet so that it can route traffic between the subnets.  In most cases there is no reason to assign all the cards to the same subnet unless you are implementing some type of "[bonding]("http://www.cyberciti.biz/tips/tag/nic-bonding-linux")" for bandwidth reasons or you want to use IP-based web hosting for SSL.

---

### Post by zika on 2013-03-13
Be sure to look into /etc/udev/rules.d/70-persistent-net.rules to see which NIC is recognized and how...
Also, disable UFW since it made me pull my hair before I recognized it is him that's making all the mess...
Lot of stuff, check them one-by-one...

---

### Post by BhimaPandava on 2013-03-13
> **zika said:**
> Be sure to look into /etc/udev/rules.d/70-persistent-net.rules to see which NIC is recognized and how...
Also, disable UFW since it made me pull my hair before I recognized it is him that's making all the mess...
Lot of stuff, check them one-by-one...

I haven't setup the firewall yet because I know that it can be diffiuclt... and I haven't even got the basics working yet!
My /etc/udev/rules.d/70-persistent-net.rules currently is:

```
[FONT=courier new]# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0/0000:08:00.0/0000:09:03.0/0000:0b:00.0 (e1000e)[/FONT]
[FONT=courier new]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:24:cf:28:3f", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:18.0/0000:03:00.0/0000:04:02.0/0000:05:00.0 (e1000e)[/FONT]
[FONT=courier new]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:24:cf:28:3c", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:18.0/0000:03:00.0/0000:04:03.0/0000:06:00.0 (e1000e)[/FONT]
[FONT=courier new]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:24:cf:28:3d", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0/0000:08:00.0/0000:09:02.0/0000:0a:00.0 (e1000e)[/FONT]
[FONT=courier new]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:24:cf:28:3e", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"[/FONT]

```

---

### Post by zika on 2013-03-14
> **BhimaPandava said:**
> I haven't setup the firewall yet because I know that it can be diffiuclt... and I haven't even got the basics working yet!
My /etc/udev/rules.d/70-persistent-net.rules currently is:

```
[FONT=courier new]# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0/0000:08:00.0/0000:09:03.0/0000:0b:00.0 (e1000e)[/FONT]
[FONT=courier new]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:24:cf:28:3f", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:18.0/0000:03:00.0/0000:04:02.0/0000:05:00.0 (e1000e)[/FONT]
[FONT=courier new]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:24:cf:28:3c", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:18.0/0000:03:00.0/0000:04:03.0/0000:06:00.0 (e1000e)[/FONT]
[FONT=courier new]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:24:cf:28:3d", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0/0000:08:00.0/0000:09:02.0/0000:0a:00.0 (e1000e)[/FONT]
[FONT=courier new]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:24:cf:28:3e", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"[/FONT]

```
On first glance they seem to be recognized OK. About ufw: Even if You have it disabled, if ethx stall just try ```
sudo ufw disable
``` because that was a problem that I had on one setup. I even had to put that to eb executed every time at boot. I still have to find some time to investigate that setup because it does not make any sense but only that works with it...

---

### Post by davismarkc on 2013-03-14
Er, in your /etc/network/interfaces, you have auto eth3 followed by configuration for eth0.  This typo may explain why you are having trouble.

---

