---
title: "LTSP-server, client won't boot. Please help!"
date: 2009-03-23
forum: Server Platforms
---

### Post by Burbruee on 2009-03-23
Okay, first a little background information.
A HDD in one of our computers in the household recently died, and the computer doesn't support usb-boot and doesn't have a cdrom.
I heard of LTSP and noticed the built-in NIC supports PXE-booting, so I gave it a shot, and it will be a fun project too. (maybe even improve performance since the client is rather old)

I'm going to use my desktop computer as the server.
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
MEM: 2048 MB (DDR-800 DualChannel)
HDD: An old spare ATA-100 WD 80 GB for testing.
GFX: Geforce 7200GS 128 MB PCI-E

And the test-client:
CPU: AMD Athlon(tm) XP 1700+
MEM: 512 MB DDR
HDD: None.
GFX: Gainward BLISS Geforce 7800GS+ 512 MB AGP (funny how the client has better gfx than my new desktop..)
BOOT: LAN (PXE)

I downloaded the alternative install-cd for ubuntu 8.10 last night and installed it, selecting LTSP mode. Set up the network but got a RSOD at the end. (chroot step?)

Booted it up, removed /opt/ltsp/ and ran sudo ltsp-build-client and got no errors.

Configured /etc/ltsp/dhcpd.conf, here it is:
```

#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 10.1.0.0 netmask 255.255.255.0 {
    range 10.1.0.20 10.1.0.250;
    option domain-name "*";
    option domain-name-servers 10.1.0.10;
    option broadcast-address 10.1.0.255;
    option routers 10.1.0.10;
    next-server 10.1.0.10;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
#    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/opt/ltsp/i386/boot/pxelinux.0";
    } else {
        filename "boot/nbi.img";
    }
}

```
*Note the root-path commented out and absolute path to the pxelinux.0. Tried many different combination but no success, more on that soon.

/etc/default/dhcp3-server
```

INTERFACES="eth1"

```

Ok, updating stuff now, all of it just in case.
```

sudo ltsp-update-sshkeys
sudo ltsp-update-image
sudo ltsp-update-kernel

```

And rebooting the dhcp-server.
```

sudo /etc/init.d/dhcp3-server restart

```


Booting up the client, here is the output:
```

NVIDIA Boot Agent, PXE-2.0 (build 082 V1.82)
Copyright (C) 2001 NVIDIA Corporation
Copyright (C) 1997-2000 Intel Corporation

CLIENT MAC ADDR: 00 04 61 24 56 5D  GUID: FFFFFFFF-FFFF-FFFF-FFFF-FFFFFFFFFFFF
CLIENT IP: 10.1.0.20  MASK: 255.255.255.0  DHCP IP: 10.1.0.10
GATEWAY IP: 10.1.0.10
TFTP.
PXE-T01: File not found
PXE-E3B: TFTP Error - File Not found
PXE-M0F: Exiting NVIDIA Boot Agent.

```
So, looks like it can't locate the pxelinux.0 file, also back on the server syslog:

```

Mar 23 16:42:21 burbruee dhcpd: DHCPDISCOVER from 00:04:61:24:56:5d via eth1
Mar 23 16:42:22 burbruee dhcpd: DHCPOFFER on 10.1.0.20 to 00:04:61:24:56:5d via eth1
Mar 23 16:42:23 burbruee dhcpd: DHCPREQUEST for 10.1.0.20 (10.1.0.10) from 00:04:61:24:56:5d via eth1
Mar 23 16:42:23 burbruee dhcpd: DHCPACK on 10.1.0.20 to 00:04:61:24:56:5d via eth1

```
There is no mention of TFTP request, should it not?

Does this help anything?
```

burbruee@burbruee:~/Dokument$ ps ax | grep dhcpd
17001 ?        Ss     0:00 /usr/sbin/dhcpd3 -q -pf /var/run/dhcp3-server/dhcpd.pid -cf /etc/ltsp/dhcpd.conf eth1
17371 pts/0    R+     0:00 grep dhcpd
burbruee@burbruee:~/Dokument$ netstat -lu
Aktiva internetanslutningar (endast servrar)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
udp        0      0 *:43840                 *:*                                
udp        0      0 *:bootps                *:*                                
udp        0      0 *:tftp                  *:*    
udp        0      0 *:mdns                  *:* 

```

I really don't know what's going on, and I've tried every combination possible in the dhcpd.conf under root-path and filename such as the defaults and "/opt/ltsp/i386" (as root-path) and "boot/pxelinux.0" for filename..

```

burbruee@burbruee:~/Dokument$ sudo find / -name pxelinux.0
/var/lib/tftpboot/ltsp/i386/pxelinux.0
/usr/lib/syslinux/pxelinux.0
/opt/ltsp/i386/boot/pxelinux.0
/opt/ltsp/i386/usr/lib/syslinux/pxelinux.0
burbruee@burbruee:~/Dokument$ 

```

Please help, would love to have this up and running by tonight. :popcorn:
The client and server are both connected to a switch, meaning NO router with built-in firewall that should interfere or block connections.

Thanks.

---

### Post by microzonepl on 2009-12-16
Hello do you have an anwser to your problem because i've got the same issue.

Thanks

---

### Post by Burbruee on 2009-12-17
> **microzonepl said:**
> Hello do you have an anwser to your problem because i've got the same issue.

Thanks

I did manage to solve it, it had something to do with the path I think. Don't remember really, it was a long time ago..

However, I did back up my working dhcpd.conf before I got rid of the server, (it was a temporary solution to boot a computer at home because of a dead HDD) I guess because I had so much trouble getting it to work properly I saved the file in case I would need to set up something like this again.

I can post it here for you if you want, but if it doesn't help you then there's not much more I can do to help you out. Like I said it was such a long time ago so I don't remember the specific details.

```
#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 10.1.0.0 netmask 255.255.255.0 {
    range 10.1.0.20 10.1.0.250;
    option domain-name "burbruee.homelinux.com";
    option domain-name-servers 10.1.0.10;
    option broadcast-address 10.1.0.255;
    option routers 10.1.0.10;
    next-server 10.1.0.10;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;

#    option root-path "/opt/ltsp/i386";
#    filename "ltsp/i386/pxelinux.0";

    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "ltsp/i386/pxelinux.0";
    } else {
        filename "ltsp/i386/nbi.img";
    }

} 
```

Hope it helps.

---

