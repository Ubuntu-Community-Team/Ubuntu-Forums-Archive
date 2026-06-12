---
title: "[LTSP] dhcp3 server not working"
date: 2009-02-08
forum: Server Platforms
---

### Post by Ash96 on 2009-02-08
I'm having problems with my dhcp3 server. I'm assuming I need it for LTSP since it has it's own dhcpd.conf. Here is mine by the way:

the path: /etc/ltsp/dhcpd.conf
```

#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.0.0 netmask 255.255.255.0 {
    range 192.168.0.20 192.168.0.250;
    option domain-name "example.com";
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

I haven't altered it.

And this is the message I get in the syslog when I try to start it.

```

Feb  8 18:29:05 ichi-ban dhcpd: Wrote 0 leases to leases file.
Feb  8 18:29:05 ichi-ban dhcpd: 
Feb  8 18:29:05 ichi-ban dhcpd: No subnet declaration for eth0 (192.168.1.4).
Feb  8 18:29:05 ichi-ban dhcpd: ** Ignoring requests on eth0.  If this is not what
Feb  8 18:29:05 ichi-ban dhcpd:    you want, please write a subnet declaration
Feb  8 18:29:05 ichi-ban dhcpd:    in your dhcpd.conf file for the network segment
Feb  8 18:29:05 ichi-ban dhcpd:    to which interface eth0 is attached. **
Feb  8 18:29:05 ichi-ban dhcpd: 
Feb  8 18:29:05 ichi-ban dhcpd: 
Feb  8 18:29:05 ichi-ban dhcpd: Not configured to listen on any interfaces!

```

Help would be much appreciated. If you guys need any more information just ask.

---

### Post by srangelov on 2009-03-16
Hi Ash96,

Did you managed to make dhcp3-server start at startup?

I have the same thread here:
[http://ubuntuforums.org/showthread.php?t=1094344&highlight=dhcp3-server]("http://ubuntuforums.org/showthread.php?t=1094344&highlight=dhcp3-server")

But no solution yet.

Sotir

---

### Post by sanemanmad on 2009-03-16
Please answer these questions:

What interfaces are you using? eth0, ath0 etc....

?Results of ```
cat /etc/network/interfaces
```

?Results of ```
route
```

Just wondering why your DHCP server is listening on 192.168.1.x and your network 192.168.0.x? There must be more to your network topology

---

### Post by sanemanmad on 2009-03-16
Also, > option root-path "/opt/ltsp/i386"
 Would'nt that mean that > 
        filename "/ltsp/i386/pxelinux.0";
    } else {
    filename "/ltsp/i386/nbi.img";
    }

 
Should be > 
        filename "pxelinux.0";
    } else {
    filename "nbi.img";
    }


---

### Post by srangelov on 2009-03-17
sanemanmad,

Thank you for your attention!

I found what is the problem :)

DHCP requires a static IP address and is looking for it here - /etc/network/interfaces.
But Ubuntu 8.10 uses NetworkManager 0.7 which does not write static IP configuration to /etc/network/interfaces .

I removed NetworkManager, set manually static IP, configure default interfaces for DHCP and - it is now starting automatically after the restart.

For more info see my post in the other thread - 
[http://ubuntuforums.org/showthread.php?t=1094344&highlight=dhcp3-server]("http://ubuntuforums.org/showthread.php?t=1094344&highlight=dhcp3-server")

Sotir

---

### Post by sanemanmad on 2009-03-23
Glad you were able to solve the issue. Thanks for posting your resolution so that others may find it as well.

---

