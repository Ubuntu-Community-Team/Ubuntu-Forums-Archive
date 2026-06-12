---
title: "Multiple IPs + bridge for KVM"
date: 2009-09-02
forum: Server Platforms
---

### Post by Khao8 on 2009-09-02
Hi all,
I'm trying to setup my Ubuntu 9.04 server to do virtualization following this guide : [http://www.howtoforge.com/virtualization-with-kvm-on-ubuntu-9.04](http://www.howtoforge.com/virtualization-with-kvm-on-ubuntu-9.04)

To do so, I need to create a bridge with my network interface, but the tutorial shows how to do it when your network is configured with one IP and I have 2 IPs configured on my server. I tried to change the config myself and well.. I failed to do so and my server was unreachable (fortunately I had backuped my working configuration, and asked my host's support to just replace the file and reboot)

I tried googling, and couldn't find help so if you guys could help me configure my network it would be great. Here's my working configuration with the 2 IPs :

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 66.197.167.84
        netmask 255.255.255.192
        network 66.197.167.64
        broadcast 66.197.167.127
        gateway 66.197.167.65
        dns-nameservers 4.2.2.1
        dns-search MYHOST.com
        post-up iptables-restore < /etc/iptables.up.rules
        # dns-* options are implemented by the resolvconf package, if installed

auto eth0:1
iface eth0:1 inet static
        address 66.197.167.85
        netmask 255.255.255.192
        network 66.197.167.64
        broadcast 66.197.167.127
        gateway 66.197.167.65

```

Thanks!

---

### Post by jakekatz on 2009-09-30
Basically for bridging, you put your primary interface (eth0) into Manual mode, so it does not get configured at boot time.

You replace your eth0 with br0 (This is the bridge for kvm guests to use)  And you configure your bridge (br0) as if you're configureing your primary interface

It should look something like this.

You can 'tinker' with the line  **[COLOR=Blue]bridge_ports eth0 -> eth0:1[/COLOR]**, but like I mentioned, I'm not using any host OS virtual interfaces, so I'm not sure this would work with bridging.

```

/etc/network/interfaces:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address 66.197.167.84
        netmask 255.255.255.192
        network 66.197.167.64
        broadcast 66.197.167.127
        gateway 66.197.167.65
        [COLOR=Blue]**bridge_ports eth0**[/COLOR]
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0
        dns-nameservers 4.2.2.1
        dns-search MYHOST.com
        post-up iptables-restore < /etc/iptables.up.rules
        # dns-* options are implemented by the resolvconf package, if installed

auto eth0:1
iface eth0:1 inet static
        address 66.197.167.85
        netmask 255.255.255.192
        network 66.197.167.64
        broadcast 66.197.167.127
        gateway 66.197.167.65

#EOF

```I hope this helps you out.  It took me a day to figure out the kvm wiki, if they had just used the layman terms (replace eth0 with br0) it would have saved me much tinkering :)

---

