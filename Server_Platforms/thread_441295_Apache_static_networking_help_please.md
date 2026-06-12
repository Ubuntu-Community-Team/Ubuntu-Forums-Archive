---
title: "Apache static networking help please"
date: 2007-05-12
forum: Server Platforms
---

### Post by ixus_123 on 2007-05-12
I'm following the following guide in an attempt to set up my own IMAP mail server. Once it's running I'll also host my blog on there.
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3")

I have got as far as installing the LAMP, and creating a php test page and all display perfectly.

However this is with my LAN on DHCP so I tried to install a static route to my server by editing **/etc/network/interfaces** as follows
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

```

and then **/etc/init.d/networking restart**

After I do this, I can still SSH into the server, ping it on the LAN address & ping my external IP and URL (kieren.demon.co.uk) and ping google from the server.

However, if I point my browser at my website it just gives me an error 504
> Gateway Timeout
The following error occurred:

Server unreachable
Please contact the administrator.

Setting back to DHCP fixes everything but I'd really prefer a static route. Any ideas? I guess I'm missing something blindingly obvious.

---

### Post by ixus_123 on 2007-05-14
Well I fixed it bt in a bit of a weird way.

I kernel upgrade fixed the problem - not quite sure how that works but it's done now so I'm happy again :)

---

