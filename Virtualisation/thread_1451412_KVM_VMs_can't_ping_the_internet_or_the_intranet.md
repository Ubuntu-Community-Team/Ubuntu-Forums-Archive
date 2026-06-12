---
title: "KVM VMs can't ping the internet or the intranet"
date: 2010-04-10
forum: Virtualisation
---

### Post by RoboJ1M on 2010-04-10
Hi,

I've got a 10.04 beta server running ebox 1.5 performing the network infrastructure duties (network config, dns, dhcp, firewall)

The local LAN is 192.168.88.0/24

I'm using virt-manager to manage my virts. :)

I've created a routed virtual network,  192.168.77.0/24

The firewall is supposedly open across all the internal networks.

If I create a VM, it boots and gets an IP address and has functioning DNS. It can ping the gateway (88.1 and 77.1) but cannot ping anything else in 88.0/24 nor anything on the internet.

Anything on the local LAN (this laptop for instance) uses the same gateway, 88.1, can access the internet. 

Anything on the local LAN can ping anything in 77.0/24.

There is nothing in the firewall logs to show that it is blocking 77.2's (the one VM) access to anything else.

I have no idea where to look next, can anybody assist?

Thanks,

Jim.

Edit: I can't get the logs to log everything in ebox. For instance, ping works but adding a log ICMP rule to ebox does nothing. It logs drops (the VM keeps asking for windows file shares over broadcast) but not accepts. :(

Edit2: Creating a second virtual network, this time NAT'ed, allows me access to the outside world. Except now I can't get back in.

---

### Post by TheR on 2010-04-11
I don't know anything about routed network settings, but the right way to enable guests to access outside network is trough network bridge.

by
TheR

---

### Post by RoboJ1M on 2010-04-11
So I read, but configuring VMs with virt-manager only lets you choose NAT or routed.

According to ebox I have:

eth0
virbr0
vnet0
wlan0

eth0 is wired to the LAN
wlan0 is no longer used
virbr0 and vnet0 are created by libvirt

I don't know why, but even though I've configured a static IP on virbr0, it does not appear in the interfaces file. Only eth0 is in the interfaces file.

J.

---

### Post by TheR on 2010-04-12
Install bridge-utils (apt-get install bridge-utils).

Go to /etc/networking and update interfaces to something like this:

auto eth0
iface eth0 inet manual

# Bridge for eth0
auto br0
iface br0 inet static
        address 192.168.2.201
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.2.125
        dns-search mydomain.com

        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off
        bridge_maxwait 0

Basicly everything what goes under eth0 goes under br0. 


by
TheR

---

### Post by RoboJ1M on 2010-04-13
I tried creating the bridge before, but when the networking came back up I no longer had any outside access to the machine itself.

I'm loath to try that again because I ended up frying the OS and having to blat it and re-install.

Does anybody know what virt-manager is doing when you select NAT or routed? 

Looks like I've got 2 ways of settings this up:

Manually: virsh + virt-install + hacking interfaces file.
Automatically: virt-manager + ebox

I think manually will require a re-install so I can set up the bridge prior to installing ebox. I tried setting up the bridge after ebox last time and it just failed completely.

I'd prefer automatically because it's starting to look really good and it's designed really well. But it just doesn't seem to work very well yet!

Maybe I'll just wipe it and try again with 10.04 beta 2 :\

J.

---

