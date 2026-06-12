---
title: "setting up network"
date: 2011-05-23
forum: Server Platforms
---

### Post by Azyx on 2011-05-23
Hi
Have very old hardware and during install i did not set up network cos i did not have the comuter plugged in. I wonder how i set it up the network with DHCP-client in command line interface on ubuntu 10.04LTS.

Another question. is it possible after I get install and configured the network also install a desktop for configuration and then only log in to commandline and have it like a server?

/cheers

---

### Post by papibe on 2011-05-23
I think most regular wired connections will just work (even if not configured at installation). 

Is it a wireless connection?

Regards.

---

### Post by arrrghhh on 2011-05-23
> **Azyx said:**
> Hi
Have very old hardware and during install i did not set up network cos i did not have the comuter plugged in. I wonder how i set it up the network with DHCP-client in command line interface on ubuntu 10.04LTS.

Another question. is it possible after I get install and configured the network also install a desktop for configuration and then only log in to commandline and have it like a server?

/cheers

Don't install a GUI just to setup the network - that's more than overkill :p.

You can do this the CLI-way, it's easy.

So you want your server to be using DHCP not a static IP?  I assume it's hardline, but the previous post asks if it's wifi - that's good to know as well.

IMHO, static IPs are better for servers - DHCP addresses *can* change.  They usually don't, but you don't want to be troubleshooting that when your server seemingly is unreachable, all because the IP changed...

At any rate, the file you need to modify is /etc/network/interfaces file.  Here's mine:```
# The primary network interface

    auto eth0
    iface eth0 inet static
    address 192.168.0.99
    gateway 192.168.0.1
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.0.255
```This assumes you want a static IP, and you only have one interface - eth0.  If you want to use DHCP, all you need is:```
auto eth0
iface eth0 inet dhcp
```

---

### Post by Azyx on 2011-05-23
THanx :)

---

### Post by Azyx on 2011-05-23
> **arrrghhh said:**
> Don't install a GUI just to setup the network - that's more than overkill :p.

You can do this the CLI-way, it's easy.


Yes it's eacy, but other thing i want to setup are little more complicated. But is it possible to do these thing i desktop and the boot up only in CLI?

---

### Post by kibaya on 2011-05-23
Hi.
to easily set up dhcp on a machine, on ubuntu,  just open the Terminal and type in "sudo dhclient" without the quotes.

---

### Post by Azyx on 2011-05-24
> **kibaya said:**
> Hi.
to easily set up dhcp on a machine, on ubuntu,  just open the Terminal and type in "sudo dhclient" without the quotes.

Does it work even if the eth0 not is pressent in /etc/network/interfaces.list ?

/cheers

---

### Post by arrrghhh on 2011-05-24
> **Azyx said:**
> Does it work even if the eth0 not is pressent in /etc/network/interfaces.list ?

/cheers

/etc/network/**interfaces** - no .list.

If there's no entries, add one for lo (loopback) and one for eth0 (main NIC).  Ubuntu *should* have generated these for you...

---

### Post by Azyx on 2011-05-24
> **arrrghhh said:**
> /etc/network/**interfaces** - no .list.

If there's no entries, add one for lo (loopback) and one for eth0 (main NIC).  Ubuntu *should* have generated these for you...

No, it does not do it, if you don't do it during install.

/cheers

---

### Post by arrrghhh on 2011-05-24
> **Azyx said:**
> No, it does not do it, if you don't do it during install.

/cheers

Ah, news to me.  I haven't done a clean install on my server in a while... I must've configured it initially.

Did you get it going?  Anything else you need...?

---

### Post by Azyx on 2011-05-24
> **arrrghhh said:**
> Ah, news to me.  I haven't done a clean install on my server in a while... I must've configured it initially.

Did you get it going?  Anything else you need...?

Yes it worked fine. Now it is to figure out ethernet over firewire.

---

