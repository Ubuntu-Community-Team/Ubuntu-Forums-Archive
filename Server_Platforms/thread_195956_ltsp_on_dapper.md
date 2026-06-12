---
title: "ltsp on dapper"
date: 2006-06-13
forum: Server Platforms
---

### Post by amazilia on 2006-06-13
Hi,

I have dapper fully updated. 

I follwed the[ ltsp QuickInstall ]("https://wiki.ubuntu.com/UbuntuLTSP/LTSPQuickInstall?highlight=%28ltsp%29") 

1. sudo apt-get install ltsp-server-standalone openssh-server
2. sudo ltsp-build-client


once I start the thin client I get an address (192.168.0.250), it indicates the adress of the server/gateway (192.168.0.1), but then I get 

PXE-E32: TFTP open timeout
PXE-E32: TFTP open timeout
PXE-E32: TFTP open timeout
PXE-M0F: Exiting PXE ROM
disk boot failure, insert system disk and press return

Any advice would be great

Thanks

Philippe

---

### Post by fnjordy on 2006-06-15
Does ltsp-build-client actually finish correctly for you?

Just having installed Dapper when I run "sudo ltsp-build-client" the script terminates after debootstrap finishes :(   I edit the script comment out the debootstrap line and restart so it can finish off.  Werd.

> I: Configuring ubuntu-keyring...
I: Configuring ubuntu-minimal...
I: Base system installed successfully.
# 

---

### Post by amazilia on 2006-06-15
[QUOTE=fnjordy]Does ltsp-build-client actually finish correctly for you?
[/QUOTE]

Hi,

I do not know, and since apparently nobody knows anything about ltsp here. I guess I will live it where it is.

Philippe

---

### Post by robertmcox on 2006-06-17
amazilia,

Here's your easy answer, consider it a HOWTO for other users as well:

HOWTO:  Setup LTSP on your working ubuntu system using the edubuntu packages

Make sure you have a static IP address and know your network settings.  You should know your network address.  You will probably want to disable DHCP on your Linksys/DLink router/firewall -- this configuration makes your LTSP server the DHCP server.

Install the edubuntu packages:

```
sudo apt-get install edubuntu-server
```

If you want, you can also install *edubuntu-desktop* to "upgrade" to edubuntu.  This metapackage has desktop themes and child-friendly applications.  Whether or not you want to use LTSP, this package is great if you have kids!

Now edit your /etc/ltsp/dhcpd.conf according to Getting Started Guide at [http://www.edubuntu.org/GettingStarted](http://www.edubuntu.org/GettingStarted).  Note that if /etc/ltsp/dhcpd.conf exists, the contents of /etc/dhcp3/dhcpd.conf will be ignored.

Make sure the appropriate services are started:

```

sudo invoke-rc.d dhcp3-server restart 
sudo invoke-rc.d nfs-kernel-server restart 
sudo invoke-rc.d nfs-common restart
sudo invoke-rc.d portmap restart
```

You need to setup the thin client file system.  When your thin clients boot, they will mount the folder /opt/ltsp/i386 as /.  In case you have tried before and not been successful, let's blow away the past:

```
sudo rm -rf /opt/ltsp/*
```

And setup the thin client file system:

```
sudo ltsp-build-client
```

Done!

You should probably fine tune your environment some, most of the client settings are located in /opt/ltsp/i386/etc/lts.conf. The file does not exist by default, you should create it.  There are some hints for managing the setup here:

[https://wiki.edubuntu.com/EdubuntuLtsConfParams](https://wiki.edubuntu.com/EdubuntuLtsConfParams)
[https://wiki.edubuntu.org/HowToCookEdubuntu/Chapters/LTSPManagement](https://wiki.edubuntu.org/HowToCookEdubuntu/Chapters/LTSPManagement)

---

### Post by amazilia on 2006-06-20
Hi,

Thanks for all of this. 

I will work on it

Philippe

---

### Post by amazilia on 2006-06-20
Hi

[QUOTE=robertmcox]
Make sure you use the appropriate IP subnet address.  Now, make the new settings take effect:

```
sudo invoke-rc.d nfs-kernel-server restart 
sudo invoke-rc.d nfs-common restart
sudo invoke-rc.d portmap restart
```

[/QUOTE]

I get the following is it normal or do I need to adjust something ?

```
 sudo invoke-rc.d portmap restart 
/etc/default/portmap: line 12: portmap: : commande introuvable
/etc/default/portmap: line 13: rpc.mountd: : commande introuvable
/etc/default/portmap: line 14: rpc.statd: : commande introuvable
/etc/default/portmap: line 15: in.tftpd: : commande introuvable
/etc/default/portmap: line 12: portmap: : commande introuvable
/etc/default/portmap: line 13: rpc.mountd: : commande introuvable
/etc/default/portmap: line 14: rpc.statd: : commande introuvable
/etc/default/portmap: line 15: in.tftpd: : commande introuvable
 * Stopping portmap daemon...                                            [ ok ]
/etc/default/portmap: line 12: portmap: : commande introuvable
/etc/default/portmap: line 13: rpc.mountd: : commande introuvable
/etc/default/portmap: line 14: rpc.statd: : commande introuvable
/etc/default/portmap: line 15: in.tftpd: : commande introuvable
 * Starting portmap daemon...                                            [ ok ]

```

"commande introuvable" means that the commande cannot be found


Thanks

Philippe

---

### Post by robertmcox on 2006-06-21
I apologize for giving bad directions!

Actually, you do not need to to edit /etc/default/portmap on Ubuntu for this to work.  This file should not have any uncommented lines.

Does your setup work?

---

### Post by amazilia on 2006-06-22
Hi,

In fact I for the time being gave up with ubuntu. I installed edubuntu and the ltsp server was installed very easily.

I plan to come back to ubuntu as the look of edubuntu does not suit me.

thanks again

Philippe

---

### Post by v4169sgr on 2006-06-25
I came on to the forums this morning expecting to have to ask a question about the applicability of this link to Dapper:

[https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto)

and found this thread - and all the links. Many thanks you guys!:cool: 

I suspect that I am going  to find the folllowing links the most useful

[http://www.edubuntu.org/GettingStarted](http://www.edubuntu.org/GettingStarted)
[http://www.edubuntu.org/ThinClientConfig](http://www.edubuntu.org/ThinClientConfig)

I will be working from Kubuntu 6.06 with the aim of creating an all-in-one easy to administer family network comouting resource. Will let you know how I get on - may not make progress for a week or two as need to grab a bunch of PXE cards:p

---

### Post by v4169sgr on 2006-06-25
I am trying the first couple of steps to get started. I've installed the edubuntu-server package, and edited the /etc/dhcp3/dhcpd.conf file according to what I understand of the above instructions. All services restarted apparently normally, apart from the dhcp server, which gave the following o/p:

```
sudo invoke-rc.d dhcp3-server restart
Internet Systems Consortium DHCP Server V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/
 * Stopping DHCP server                                                  [fail]
Internet Systems Consortium DHCP Server V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/
 * Starting DHCP server:                                                 [fail]
invoke-rc.d: initscript dhcp3-server, action "restart" failed.

```

I found the following in my KSystemLog:

```
25/06/06 21:33:21	localhost	dhcpd	All rights reserved.

25/06/06 21:33:21	localhost	dhcpd	Copyright 2004-2005 Internet Systems Consortium.

25/06/06 21:33:21	localhost	dhcpd	For info, please visit http://www.isc.org/sw/dhcp/

25/06/06 21:33:21	localhost	dhcpd	** Ignoring requests on eth0.  If this is not what

25/06/06 21:33:21	localhost	dhcpd	Internet Systems Consortium DHCP Server V3.0.3

25/06/06 21:33:21	localhost	dhcpd	   in your dhcpd.conf file for the network segment

25/06/06 21:33:21	localhost	dhcpd	No subnet declaration for eth0 (10.0.0.1).

25/06/06 21:33:21	localhost	dhcpd	Not configured to listen on any interfaces!

25/06/06 21:33:21	localhost	dhcpd	   to which interface eth0 is attached. **

25/06/06 21:33:21	localhost	dhcpd	Wrote 0 leases to leases file.

25/06/06 21:33:21	localhost	dhcpd	   you want, please write a subnet declaration


```

Here is my etc/dhcp3/dhcpd.conf file

```
#
# Sample configuration file for ISC dhcpd for Debian
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
option domain-name "example.org";
option domain-name-servers ns1.example.org, ns2.example.org;

default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
#log-facility local7;

# No service will be given on this subnet, but declaring it helps the
# DHCP server to understand the network topology.

subnet 10.0.0.0 netmask 255.255.255.0 {
  range 10.0.0.20 10.0.0.250;
  option domain-name "example.com";
  option domain-name-servers 10.10.0.1;
  option broadcast-address 10.10.0.255;
  option routers 10.0.0.1;

  option subnet-mask 255.255.255.0;

  filename "/ltsp/pxelinux.0";
  option root-path "/opt/ltsp/i386";
}

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

#subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
#subnet 10.5.5.0 netmask 255.255.255.224 {
#  range 10.5.5.26 10.5.5.30;
#  option domain-name-servers ns1.internal.example.org;
#  option domain-name "internal.example.org";
#  option routers 10.5.5.1;
#  option broadcast-address 10.5.5.31;
#  default-lease-time 600;
#  max-lease-time 7200;
#}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
#}

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#}

```

I think there is something basic I am missing. What am I doing wrong?

Many thanks in advance!

---

### Post by amazilia on 2006-06-25
Hi,

3 things : 

1. restart your server that may help. I had this problem with every major changes in the settings (using edubuntu).

2. dhcp setting must be done in /etc/ltsp/

3. It never worked for me until I install everything from scratch with edubuntu not ubuntu.

Philippe

---

### Post by v4169sgr on 2006-06-25
Many thanks!

#1 Tried it with my settings as above but of course this has no effect. IMO restarts should rarely be necessary to solve anything, so long as you have the requisite knowledge and patience!

#3 I would like to stick with Ubuntu thank you as I tried Edubuntu and while I am sure that it is excellent it did not suit my purposes. And Ubuntu is just fine for everything else.

#2 *blinks* That worked! Shouldn't have - IMHO! - which implies that (a) the instructions as above are either incorrect or incomplete, and that (b) the dhcp server is configured to look for it's config file in a "strange" place.

---

### Post by amazilia on 2006-06-25
[QUOTE=v4169sgr]Many thanks!

#1 Tried it with my settings as above but of course this has no effect. IMO restarts should rarely be necessary to solve anything, so long as you have the requisite knowledge and patience!
[/QUOTE]
agreed
[QUOTE=v4169sgr]
#3 I would like to stick with Ubuntu thank you as I tried Edubuntu and while I am sure that it is excellent it did not suit my purposes. And Ubuntu is just fine for everything else.
[/QUOTE]
me too but 
[QUOTE=v4169sgr]
#2 *blinks* That worked! Shouldn't have - IMHO! - which implies that (a) the instructions as above are either incorrect or incomplete, and that (b) the dhcp server is configured to look for it's config file in a "strange" place.[/QUOTE]

Philippe

---

### Post by jsgaarde on 2006-06-26
Hi.

I got DHCP + PXE + ltsp up and running in under two hours using kubuntu dapper and the standard packages. :D 

I have one big problem/question though:
Everything is mounted read-only. So if I for instance install kdm or gdm on the thin client using chroot /opt/ltsp/i386, then I won't be able to log in anyway since KDE can't be started whthout writing a lot of configuration stuff to the users homedir.
How do I make the homedirs writable? :confused: 

One more question: What ltsp version is installed all it says in my package manager is 0.87 I certainly hope that doesn't reflect the ltsp version. :-| 

Best regards
Jakob Simon-Gaarde

---

### Post by v4169sgr on 2006-06-28
I've completed installation of the LTSP base system, and I just installed a PXE card on a client machine. The card is recognised by the client BIOS and powers up nicely, however after printing it's MAC address, DHCP request from the client times out, and it goes to disk to install the local O/S [which, by the way, complains of no networking - lo is ok, but not eth0].

On checking KSystemLog on the server, I find the following:

```
28/06/06 22:09:18	localhost	dhcpd	All rights reserved.

28/06/06 22:09:18	localhost	dhcpd	Copyright 2004-2005 Internet Systems Consortium.

28/06/06 22:09:18	localhost	dhcpd	For info, please visit http://www.isc.org/sw/dhcp/

28/06/06 22:09:18	localhost	dhcpd	Internet Systems Consortium DHCP Server V3.0.3

[...]

28/06/06 22:49:33	localhost	dhcpd	DHCPDISCOVER from 00:08:c7:25:b8:a5 via eth0

28/06/06 22:49:33	localhost	dhcpd	DHCPREQUEST for 10.0.0.1 (10.0.0.138) from 00:08:c7:25:b8:a5 via eth0: unknown lease 10.0.0.1.

28/06/06 22:49:34	localhost	dhcpd	DHCPOFFER on 10.0.0.250 to 00:08:c7:25:b8:a5 via eth0

28/06/06 22:49:38	localhost	dhcpd	DHCPDISCOVER from 00:08:c7:25:b8:a5 via eth0

28/06/06 22:49:38	localhost	dhcpd	DHCPOFFER on 10.0.0.250 to 00:08:c7:25:b8:a5 via eth0

28/06/06 22:49:47	localhost	dhcpd	DHCPDISCOVER from 00:08:c7:25:b8:a5 via eth0

28/06/06 22:49:47	localhost	dhcpd	DHCPOFFER on 10.0.0.250 to 00:08:c7:25:b8:a5 via eth0


```

So, the exciting thing is that a connection is clearly being made, but something is going wrong. It looks like something is not onfigured correctly.

What am I doing wrong?:confused:

---

### Post by v4169sgr on 2006-06-28
By the way, 10.0.0.1 is the server, and 10.0.0.138 is my Alcatel 510 four port ethernet hub / router / ADSL box which both client and server are plugged in to. I am using static addresses for all machines, and am not running DHCP on 10.0.0.138 [but am running DHCP on 10.0.0.1]

---

### Post by v4169sgr on 2006-06-28
Turns out I WAS running DHCP on 10.0.0.138 :roll: I've turned that off an now have a different error ...

Here is the system log:

```
28/06/06 23:17:36	localhost	dhcpd	DHCPDISCOVER from 00:08:c7:25:b8:a5 via eth0

28/06/06 23:17:37	localhost	dhcpd	DHCPACK on 10.0.0.250 to 00:08:c7:25:b8:a5 via eth0

28/06/06 23:17:37	localhost	dhcpd	DHCPOFFER on 10.0.0.250 to 00:08:c7:25:b8:a5 via eth0

28/06/06 23:17:37	localhost	dhcpd	DHCPREQUEST for 10.0.0.250 (10.0.0.1) from 00:08:c7:25:b8:a5 via eth0

28/06/06 23:17:37	localhost	dhcpd	Wrote 1 leases to leases file.

```

So my client got an address. However the client then complained it could not see a PXE server, and tried to TFTP something, which failed. At which point the PXE exited and it went back in local boot again.

Any clues about where I should start looking for an error?

---

### Post by v4169sgr on 2006-06-28
Error is:

PXE-EA1 No PXE server found, using standard boot file

From memory, so may not be character for character correct ...

---

### Post by v4169sgr on 2006-06-28
A bit of googling ...

This looks as though it might help:

From: [http://syslinux.zytor.com/hardware.php#network](http://syslinux.zytor.com/hardware.php#network)

> { PXE stacks based on Intel's 0.99 series code }
A lot of older PXE stacks are based on Intel LANDesk Service Agent II, versions 0.99, which were released by Intel as "PXE PDK v2.x", despite being what can best be described as alpha quality. These stacks have numerous problems and can trivially be crashed.

If you can, upgrade your firmware.

Unfortunately, firmware upgrade to a recent source base are frequently unavailable for these cards, especially motherboard cards where the PXE stack is integrated with the system BIOS. If so, these stacks can usually be made to work with the following workarounds:

    * Disable path MTU discovery on the boot servers. Some versions of these stacks are known to crash if the boot server supports path MTU discovery on UDP. For a Linux server, path MTU discovery can be disabled by setting the sysctl entry net.ipv4.ip_no_pmtu_disc to 1:

          echo 1 > /proc/sys/net/ipv4/ip_no_pmtu_disc 

      Note that that may cause bad performance for other services which may be running on the boot server, especially if they have to talk over WAN links. DHCP or TFTP services should generally not be affected.
    * Disable the blksize TFTP option on your TFTP server. Some version of these stacks are known to request the blksize option and fail to complete the initial bootstrap transfer if the option is granted by the server (i.e. they got what they asked for.) For tftp-hpa, specify -r blksize to disable blksize, for atftp specify --no-blksize. For other TFTP servers, see your TFTP server documentation. Note that disabling blksize may have a significant impact on the performance of all TFTP clients. Other services are not affected. 



I have an Intel 0.99b LAN Desk agent ...

---

### Post by v4169sgr on 2006-06-30
I don;t thinkt the above is causing the problem for me at the moment. I think I am now getting the error that amazilia originally got i.e.

TFTP open timeout after DHCP successfully assigns a lease.

I've followed the quick install procedures as above and can show that the relevant services have started and are running successfully. netstat shows inetd listening on udp 69 which gives me confidence that tftpd-ha is running.

What am I doing wrong?

---

### Post by v4169sgr on 2006-06-30
More data ... I installed ethereal on the boot server 10.0.0.1, and tried the client again, located at 10.0.0.3 this time. The trace [below] shows that client and server are talking using the TFTP, but that for whatever reason a file transfer is not happening. The client makes a request using the blksize option, so I don't think I need to follow the steps above [they don't work anyway], and all the server appears to be doing is acking the option!

Log below:


```
No.     Time        Source                Destination           Protocol Info
     11 4.930988    10.0.0.3              10.0.0.1              TFTP     Read Request, File: /ltsp/pxelinux.0, Transfer type: octet

Frame 11 (80 bytes on wire, 80 bytes captured)
Ethernet II, Src: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5), Dst: AsustekC_16:e4:ab (00:17:31:16:e4:ab)
Internet Protocol, Src: 10.0.0.3 (10.0.0.3), Dst: 10.0.0.1 (10.0.0.1)
User Datagram Protocol, Src Port: 2070 (2070), Dst Port: tftp (69)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     12 4.933519    10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 12 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32801 (32801), Dst Port: 2070 (2070)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     13 5.933478    10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 13 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32801 (32801), Dst Port: 2070 (2070)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     14 7.934952    10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 14 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32801 (32801), Dst Port: 2070 (2070)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     15 8.874293    10.0.0.3              10.0.0.1              TFTP     Read Request, File: /ltsp/pxelinux.0, Transfer type: octet

Frame 15 (80 bytes on wire, 80 bytes captured)
Ethernet II, Src: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5), Dst: AsustekC_16:e4:ab (00:17:31:16:e4:ab)
Internet Protocol, Src: 10.0.0.3 (10.0.0.3), Dst: 10.0.0.1 (10.0.0.1)
User Datagram Protocol, Src Port: 2071 (2071), Dst Port: tftp (69)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     16 8.875042    10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 16 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32802 (32802), Dst Port: 2071 (2071)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     17 9.873887    10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 17 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32802 (32802), Dst Port: 2071 (2071)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     18 11.873916   10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 18 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32802 (32802), Dst Port: 2071 (2071)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     19 11.933958   10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 19 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32801 (32801), Dst Port: 2070 (2070)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     20 15.873896   10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 20 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32802 (32802), Dst Port: 2071 (2071)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     21 16.784067   10.0.0.3              10.0.0.1              TFTP     Read Request, File: /ltsp/pxelinux.0, Transfer type: octet

Frame 21 (80 bytes on wire, 80 bytes captured)
Ethernet II, Src: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5), Dst: AsustekC_16:e4:ab (00:17:31:16:e4:ab)
Internet Protocol, Src: 10.0.0.3 (10.0.0.3), Dst: 10.0.0.1 (10.0.0.1)
User Datagram Protocol, Src Port: 2072 (2072), Dst Port: tftp (69)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     22 16.784830   10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 22 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32803 (32803), Dst Port: 2072 (2072)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     23 17.782057   10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 23 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32803 (32803), Dst Port: 2072 (2072)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     24 19.782146   10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 24 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32803 (32803), Dst Port: 2072 (2072)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     25 19.934419   10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 25 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32801 (32801), Dst Port: 2070 (2070)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     26 23.782391   10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 26 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32803 (32803), Dst Port: 2072 (2072)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     27 23.875689   10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 27 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32802 (32802), Dst Port: 2071 (2071)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     28 28.648727   10.0.0.3              10.0.0.1              TFTP     Read Request, File: /ltsp/pxelinux.0, Transfer type: octet

Frame 28 (80 bytes on wire, 80 bytes captured)
Ethernet II, Src: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5), Dst: AsustekC_16:e4:ab (00:17:31:16:e4:ab)
Internet Protocol, Src: 10.0.0.3 (10.0.0.3), Dst: 10.0.0.1 (10.0.0.1)
User Datagram Protocol, Src Port: 2073 (2073), Dst Port: tftp (69)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     29 28.649484   10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 29 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32804 (32804), Dst Port: 2073 (2073)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     30 29.646806   10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 30 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32804 (32804), Dst Port: 2073 (2073)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     31 31.646934   10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 31 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32804 (32804), Dst Port: 2073 (2073)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     32 31.783301   10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 32 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32803 (32803), Dst Port: 2072 (2072)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     33 33.646990   AsustekC_16:e4:ab     CompaqCo_25:b8:a5     ARP      Who has 10.0.0.3?  Tell 10.0.0.1

Frame 33 (42 bytes on wire, 42 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     34 33.647057   CompaqCo_25:b8:a5     AsustekC_16:e4:ab     ARP      10.0.0.3 is at 00:08:c7:25:b8:a5

Frame 34 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5), Dst: AsustekC_16:e4:ab (00:17:31:16:e4:ab)
Address Resolution Protocol (reply)

No.     Time        Source                Destination           Protocol Info
     35 35.647306   10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 35 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32804 (32804), Dst Port: 2073 (2073)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     36 35.935374   10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 36 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32801 (32801), Dst Port: 2070 (2070)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     37 39.875399   10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 37 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32802 (32802), Dst Port: 2071 (2071)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     38 43.647662   10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 38 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32804 (32804), Dst Port: 2073 (2073)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     39 44.468286   10.0.0.3              10.0.0.1              TFTP     Read Request, File: /ltsp/pxelinux.0, Transfer type: octet

Frame 39 (80 bytes on wire, 80 bytes captured)
Ethernet II, Src: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5), Dst: AsustekC_16:e4:ab (00:17:31:16:e4:ab)
Internet Protocol, Src: 10.0.0.3 (10.0.0.3), Dst: 10.0.0.1 (10.0.0.1)
User Datagram Protocol, Src Port: 2074 (2074), Dst Port: tftp (69)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     40 44.469040   10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 40 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32805 (32805), Dst Port: 2074 (2074)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     41 45.467792   10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 41 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32805 (32805), Dst Port: 2074 (2074)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     42 47.468281   10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 42 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32805 (32805), Dst Port: 2074 (2074)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     43 47.783896   10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 43 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32803 (32803), Dst Port: 2072 (2072)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     44 51.468124   10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 44 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32805 (32805), Dst Port: 2074 (2074)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     45 59.468623   10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 45 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32805 (32805), Dst Port: 2074 (2074)
Trivial File Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     46 59.648843   10.0.0.1              10.0.0.3              TFTP     Option Acknowledgement

Frame 46 (57 bytes on wire, 57 bytes captured)
Ethernet II, Src: AsustekC_16:e4:ab (00:17:31:16:e4:ab), Dst: CompaqCo_25:b8:a5 (00:08:c7:25:b8:a5)
Internet Protocol, Src: 10.0.0.1 (10.0.0.1), Dst: 10.0.0.3 (10.0.0.3)
User Datagram Protocol, Src Port: 32804 (32804), Dst Port: 2073 (2073)
Trivial File Transfer Protocol


```

---

### Post by v4169sgr on 2006-06-30
dhcp config:

```
authoritative;

subnet 10.0.0.0 netmask 255.255.255.0 {
  range 10.0.0.2 10.0.0.3;
  option domain-name "example.com";
  option domain-name-servers 10.10.0.1;
  option broadcast-address 10.10.0.255;
  option routers 10.0.0.138;

  option subnet-mask 255.255.255.0;

  filename "/ltsp/pxelinux.0";
  option root-path "/opt/ltsp/i386";
}


```


tftp config:

```
#Defaults for tftpd-hpa
RUN_DAEMON="no"
OPTIONS="-vvv -l -s /var/lib/tftpboot"


```

pxelinux.0 file location:

```
/var/lib/tftpboot/ltsp$ ls -lsart
total 5072
1388 -rw-r--r-- 1 root root 1414477 2006-05-23 17:56 vmlinuz-2.6.15-23-386
   4 drwxr-xr-x 3 root root    4096 2006-06-25 21:12 ..
3656 -rw-r--r-- 1 root root 3737714 2006-06-26 22:37 initrd.img-2.6.15-23-386
   0 lrwxrwxrwx 1 root root      21 2006-06-26 22:37 vmlinuz -> vmlinuz-2.6.15-23-386
   4 drwxr-xr-x 2 root root    4096 2006-06-26 22:37 pxelinux.cfg
  16 -rw-r--r-- 1 root root   13156 2006-06-26 22:37 pxelinux.0
   0 lrwxrwxrwx 1 root root      24 2006-06-26 22:37 initrd.img -> initrd.img-2.6.15-23-386
   4 drwxr-xr-x 3 root root    4096 2006-06-26 22:37 .

```


I've used the tftp client on 10.0.0.1 to retrieve the pxelinux.0 successfully [on the same machine, shouldn't matter, the log above shows that the network is ok]

Will be very grateful for any help!

---

### Post by v4169sgr on 2006-06-30
I've been running "strace -f -p <inet pid>" in attempts to find out what is going on. It is clear from the below that the pxelinux.0 file is being found. It is what happens then that remains a mystery.

Strace fragment with file in expected place:

```
[pid  5420] chroot(".")                 = 0
[pid  5420] setregid32(65534, 65534)    = 0
[pid  5420] setreuid32(65534, 65534)    = 0
[pid  5420] bind(0, {sa_family=AF_INET, sin_port=htons(0), sin_addr=inet_addr("10.0.0.1")}, 16) = 0
[pid  5420] connect(0, {sa_family=AF_INET, sin_port=htons(2070), sin_addr=inet_addr("10.0.0.3")}, 16) = 0
[pid  5420] open("/ltsp/pxelinux.0", O_RDONLY|O_LARGEFILE) = 1
[pid  5420] fstat64(1, {st_mode=S_IFREG|0644, st_size=13156, ...}) = 0
[pid  5420] fcntl64(1, F_GETFL)         = 0x8000 (flags O_RDONLY|O_LARGEFILE)
[pid  5420] fstat64(1, {st_mode=S_IFREG|0644, st_size=13156, ...}) = 0
[pid  5420] mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f25000
[pid  5420] _llseek(1, 0, [0], SEEK_CUR) = 0
[pid  5420] rt_sigprocmask(SIG_BLOCK, NULL, [], 8) = 0
[pid  5420] send(0, "\0\6blksize\0001456\0", 15, 0) = 15
[pid  5420] gettimeofday({1151704388, 244829}, NULL) = 0
[pid  5420] select(1, [0], NULL, NULL, {1, 0}) = 0 (Timeout)
[pid  5420] gettimeofday({1151704389, 243562}, NULL) = 0
[pid  5420] rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
[pid  5420] send(0, "\0\6blksize\0001456\0", 15, 0) = 15
[pid  5420] gettimeofday({1151704389, 244110}, NULL) = 0
[pid  5420] select(1, [0], NULL, NULL, {2, 0}) = 0 (Timeout)
[pid  5420] gettimeofday({1151704391, 243357}, NULL) = 0
[pid  5420] rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
[pid  5420] send(0, "\0\6blksize\0001456\0", 15, 0) = 15
[pid  5420] gettimeofday({1151704391, 243904}, NULL) = 0
[pid  5420] select(1, [0], NULL, NULL, {4, 0} <unfinished ...>

```

Strace fragment when as a test I moved the pxelinux.0 file away:

```
[pid  5468] chroot(".")                 = 0
[pid  5468] setregid32(65534, 65534)    = 0
[pid  5468] setreuid32(65534, 65534)    = 0
[pid  5468] bind(0, {sa_family=AF_INET, sin_port=htons(0), sin_addr=inet_addr("10.0.0.1")}, 16) = 0
[pid  5468] connect(0, {sa_family=AF_INET, sin_port=htons(2074), sin_addr=inet_addr("10.0.0.3")}, 16) = 0
[pid  5468] open("/ltsp/pxelinux.0", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)
[pid  5468] send(0, "\0\5\0\1File not found\0", 19, 0) = 19
[pid  5468] exit_group(0)               = ?

```

The client appears to show the same behaviour in both cases i.e. slow printing of dots after 'TFTP' then a timeout - the file not found error in the second test is not displayed, and there is no change in the behaviour.

The bit I need help with is in understanding the implication of these results. Why does the server send:
[pid  5420] send(0, "\0\6blksize\0001456\0", 15, 0) = 15
and then get no response? Why is the file not being sent?

---

### Post by v4169sgr on 2006-07-01
SUCCESS!!!

Turned out that the documentation in [http://syslinux.zytor.com/hardware.php#network](http://syslinux.zytor.com/hardware.php#network)
was what was required, but that the method of application needed to be given some thought.

PLEASE NOTE: This only worked for me because my client's PXE card has the old Intel LANDesk Service Agent 0.99[x] series firmware!

Step 1:

Edit /etc/inetd.conf. Since I already installed and configured the Ubuntu ltsp server packages, then I have a line for tftp there. Add "-r blksize" to the end of this line, save and exit. NB Do not waste your time with /etc/default/tftpd-hpa - this has no effect on the running of the service as it is started by inetd.

Step 2:

Edit /etc/sysctl.conf. Add the line

"net/ipv4/ip_no_pmtu_disc=1"

save and exit. I rebooted afterwards, fired up my client, and couldn't believe my eyes when the darn thing ACTUALLY WORKED:cool: 

Disclaimer: this worked for me, it may not work for you. I don't really know what I am doing and all of the above should be treated with suspicion!:p 

This is also not to say I haven't other challenges, however these will seem small compared to the mountain I just climbed.

Finally, a big THANK YOU to the *fantastic* work put in by the Ubuntu team who have after all put together an almost idiot proof method of seamlessly installing and bringing up an LTSP server!\\:D/

---

### Post by robertmcox on 2006-07-02
Man, you had it rough, v4169sgr!

Thank you for posting your experiences to help the rest of us.

---

### Post by v4169sgr on 2006-07-02
[QUOTE=robertmcox]Man, you had it rough, v4169sgr!

Thank you for posting your experiences to help the rest of us.[/QUOTE]
It's the least I can do, and nothing at all on top of your efforts, Robert. And I wll be back in these forums shortly no doubt:p

---

