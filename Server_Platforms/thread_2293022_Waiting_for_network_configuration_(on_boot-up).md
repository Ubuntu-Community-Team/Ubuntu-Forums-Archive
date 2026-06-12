---
title: "Waiting for network configuration (on boot-up)"
date: 2015-09-02
forum: Server Platforms
---

### Post by Marc-NJ on 2015-09-02
I've noticed lately on my new 14.04 Server that I get the following on boot-up:

```

Waiting for network configuration 

```

followed by:

```

Waiting up to 60 more seconds for network configuration 

```

and eventually followed by:

```

Booting system without full network configuration

```

I've read some places that this has to do with the /etc/network/interfaces configuration, and I don't necessarily see anything wrong with how mine is configured, but here it is:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto p2p1
iface p2p1 inet static
        address 192.168.79.249
        netmask 255.255.255.0
        gateway 192.168.79.1
        dns-nameservers 192.168.79.1 8.8.8.8


auto p3p1
iface p3p1 inet static
        address 192.168.79.252
        netmask 255.255.255.0
        gateway 192.168.79.1
        dns-nameservers 192.168.79.1 8.8.8.8

```


I do have two NIC's in the system just in case anyone is wondering.

Any help is greatly appreciated if this is something that I need to be concerned about.  Thanks!

---

### Post by volkswagner on 2015-09-02
I'm not certain why this just started happening, but a few things you can change.

Typically you don't want two default gateways. 
Even though yours are the same, I think it should only be listed once.
I'm not certain on this since you have two physical adapters, you may
need to specify the gateway on both. If the second was a virtual adapter, then I'm certain you wouldn't need gateway listed.


You should also include the network and broadcast. I'd change your file as follows:

```

# The primary network interface
auto p2p1
iface p2p1 inet static
        address 192.168.79.249
        netmask 255.255.255.0
        gateway 192.168.79.1
        network 192.168.79.0
        broadcast 192.168.79.255
        dns-nameservers 192.168.79.1 8.8.8.8


auto p3p1
iface p3p1 inet static
        address 192.168.79.252
        netmask 255.255.255.0
        network 192.168.79.0
        broadcast 192.168.79.255
        dns-nameservers 192.168.79.1 8.8.8.8
```

---

### Post by blitz2 on 2015-09-02
If you are sure the settings of interfaces run this command

sudo nano /etc/init/rc-sysinit.conf

Go to line;
start on (filesystem and static-network-up) or failsafe-boot
Change to;
start on (filesystem) or failsafe-boot

Save (ctrl+x)

Reboot..

---

### Post by Marc-NJ on 2015-09-02
I actually just commented out one of the two gateways in the /etc/network/interfaces file (per the suggestion by volkswagner) and that seems to have solved it.  Does that seem to make sense and won't cause any issues?

Thanks!

P.S. I also have a /etc/network/interfaces~ file, but have no idea what this file is...?

---

### Post by cariboo on 2015-09-02
> **Marc_Bressman said:**
> I actually just commented out one of the two gateways in the /etc/network/interfaces file (per the suggestion by volkswagner) and that seems to have solved it.  Does that seem to make sense and won't cause any issues?

Thanks!

P.S. I also have a /etc/network/interfaces~ file, but have no idea what this file is...?

The file ending with a ~ (tilde) is just a backup file, you can delete it if you want.

---

### Post by bab1 on 2015-09-03
> **Marc_Bressman said:**
> I actually just commented out one of the two gateways in the /etc/network/interfaces file (per the suggestion by volkswagner) and that seems to have solved it.  Does that seem to make sense and won't cause any issues?

Thanks!

P.S. I also have a /etc/network/interfaces~ file, but have no idea what this file is...?
Why do you need 2 interfaces attached to the same network?  In most cases the only need to have 2 interfaces to one network is for bonding purposes.  I believe under normal circumstances that one of the interfaces is set to inactive if you have configured both.  My guess is that only **p2p1** is active.

---

### Post by volkswagner on 2015-09-03
> **bab1 said:**
> Why do you need 2 interfaces attached to the same network?  In most cases the only need to have 2 interfaces to one network is for bonding purposes.  I believe under normal circumstances that one of the interfaces is set to inactive if you have configured both.  My guess is that only **p2p1** is active.

I'm also curious why the OP has two interfaces on same subnet, but there are reasons to do this without bonding.

I don't think either will be inactive by default. This would be easy enough to prove by connecting via ssh to both ip addresses (provided ssh is listening on both/all interfaces).

Having two interfaces on same LAN can allow two services to listen on same port number. You could run Nginx and Apache both on port 80 using different
interfaces. I'm sure there are many more reasons, but this is just an example.

---

