---
title: "LTSP not getting chroot"
date: 2009-06-01
forum: Server Platforms
---

### Post by rybl on 2009-06-01
I am trying to set up an LTSP server to serve a few clients.  My problem is as follows...

I can get a client to boot, but it appears to be loading the server's environment instead of the chroot enviornment.  From the client I can see /opt/ltsp/i386/.  I was under the impression that LTSP should chroot the client to that directory.  Can anyone tell me why this is happening.

Here is some background information.   I installed Ubuntu 9.04 from the alternate cd using the LTSP install option.  After the install I set eth0 to 192.168.0.254 and hooked it into the network that the clients will be on.  I set eth1 to get a dhcp address from our 192.168.1.0/24 network.  I set the dhcp server to run on eth0.  My /etc/ltsp/dhcpd.conf looks like this

```
#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.0.0 netmask 255.255.255.0 {
    range 192.168.0.20 192.168.0.250;
    option domain-name "[my domain].com";
    option domain-name-servers 192.168.0.1;
    option broadcast-address 192.168.0.255;
    option routers 192.168.0.1;
#    next-server 192.168.0.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}
```

I thought this may also be relevant.  Any time I chroot and make a change and I try to run ltsp-update-image I get the following error message.

```

Info: port 2000 is already defined with /opt/ltsp/images/i386.img in inetd.conf
```

---

### Post by wirelessben on 2009-09-18
rybl,

The "info: port 2000 ..." message is not a problem, just an information message that confuses a lot of LTSP users.

In your dhcp.conf, you seem to be missing the "/opt" in your full path. Since you already specified the root path, you should be able to just code

```
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "pxelinux.0";
    } else {
        filename "nbi.img";
    }

```

---

### Post by glj on 2009-10-14
> **wirelessben said:**
> 
In your dhcp.conf, you seem to be missing the "/opt" in your full path. Since you already specified the root path, you should be able to just code

```
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "pxelinux.0";
    } else {
        filename "nbi.img";
    }

```
 Correction:
/ltsp/i386/pxelinux.0 and /ltsp/i386/nbi.img that appear in the original post are not in the chroot as you apparently believe, but are instead in /var/lib/tftpboot. The dhcpd.conf file in the original post was correct.

---

