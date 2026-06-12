---
title: "LTSP can't start X session (all weekend no luck)"
date: 2008-05-18
forum: Server Platforms
---

### Post by YogiPaolo on 2008-05-18
You may read my long winded post or cut right to the config files. The short story is that I now have a remote desktop. I did so by adding this line to my lts.conf file:

LDM_DIRECTX=True

This allows a direct, unencrypted TCP X pipe to my server. Crazy....
The problem all along was SSHD, though I'm not sure how...
I noticed that when I run ltsp-update-sshkeys, I see no output. Perhaps the keys were not being updated. I would appreciate some input on this.

Thanks again

=begin old message=

Ok, I've been obsessing about this all weekend. I've gone very my entire server with a find toothed comb. All necessary services are running and configured properly (it seems, yet....).

I get the LDM login window, enter my username and password and the screen flashes a few times from gray to black, then dumps me back to the login.

I assume this is because X is not configured properly OR gnome can't set up my desktop for some reason. I'm lost at this point and my eyes are bleeding too much (and I'm too frustrated) to figure this out. So, bew hew on me, will somebody please give me a clue?  Here are my succulent config files that I've slaved for over a hot keyboard all weekend. Hope they help.

I haven't been able to find much of anything about how nbd-server is supposed to do its thing. There is no nbd config file where the man page says its supposed to be and when i try to start nbd server manually, it complains about the lack of a config file. Also, invoking nbd server complains about config file as well. Could this be why the xsession soils itself?

However, I do see that nbd is running , so hmmm....
```
ps aux | grep nbd
nobody   31323  0.0  0.0   1772   496 ?        Ss   18:31   0:00 /bin/sh /usr/sbin/nbdrootd /opt/ltsp/images/i386.img
nobody   31324  0.0  0.1   3672  1140 ?        S    18:31   0:00 /bin/nbd-server 0 /opt/ltsp/images/i386.img -r -C /dev/null
nobody   31524  0.0  0.0   1772   492 ?        Ss   18:40   0:00 /bin/sh /usr/sbin/nbdrootd /opt/ltsp/images/i386.img
nobody   31525  0.0  0.1   3672  1140 ?        S    18:40   0:00 /bin/nbd-server 0 /opt/ltsp/images/i386.img -r -C /dev/null
paolo    31802  0.0  0.0   3004   748 pts/2    R+   18:58   0:00 grep nbd

```



First, the DHCP server file: 

```

#
# Default LTSP dhcpd.conf config file.
#

authoritative;
subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.5 192.168.1.200;
    option domain-name "*";
    option domain-name-servers 192.168.0.1;
    option broadcast-address 192.168.1.255;
    option routers 192.168.0.1;
    next-server 192.168.1.5;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}
# on what interfaces should the DHCP server serve the DHCP request
INTERFACES="eth3";

```

Next, my interfaces config:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.201
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
dns-nameservers 192.168.0.1

# The secondary network interface - this is the declared ip/iface for the "next$
#meaning this is the tftp server
auto eth1
iface eth1 inet static
address 192.168.1.5
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
dns-nameservers 192.168.0.1

# default gateway - one day I will route you somewhere nice...
auto eth2
iface eth2 inet static
address 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

# third nic for DHCP
auto eth3
iface eth3 inet static
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

```

Then, my lts.conf
```
 My lts.conf file. I hope it works
# Let's try to make the thing autoconfigure itself

[Default]
X_COLOR_DEPTH=24
LOCALDEV=True
SOUND=True
NBD_SWAP=Y
SYSLOG_HOST=server
XKBLAYOUT=en

```

Thanks, Ubuntu community!

---

