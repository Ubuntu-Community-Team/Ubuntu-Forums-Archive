---
title: "How can I give my VM guests a dedicated IP address?"
date: 2013-07-02
forum: Virtualisation
---

### Post by c3ntury on 2013-07-02
Here is an image of my virtual MAC (OVH) -
[IMG]http://i.imgur.com/F4eSY1D.png[/IMG]

Here's an image of my Windows set-up -
[IMG]http://i.imgur.com/9P7jdvC.png[/IMG]

Here is a copy of my /etc/network/interfaces -
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static
        address 46.105.127.19
        netmask 255.255.255.0
        network 46.105.127.0
        broadcast 46.105.127.255
        gateway 46.105.127.254


iface eth0 inet6 static
        address 2001:41D0:2:EE13::1
        netmask 64
        post-up /sbin/ip -f inet6 route add 2001:41D0:2:EEff:ff:ff:ff:ff dev et$
        post-up /sbin/ip -f inet6 route add default via 2001:41D0:2:EEff:ff:ff:$



The guest OS is Windows Server 2012, the host is Ubuntu 12.04, running the latest version of KVM.

I'm trying to give my guest OS a dedicated IP address (as shown above), but I'm really stuck on how to go about it. Could anyone please help me out? Thanks.

---

### Post by TheFu on 2013-07-02
I'm actually very concerned that you have a public IP inside your Windows setup. Do you have a router between the internet and your PC?  If not, you are living extremely dangerously.  I'd ask how often you've been hacked.  A router is the 1st line of defense against all that is bad on the internet.  If you don't have a router, then you cannot just "use" any public IP address. You need to contact the network provider to get more and follow their instructions.

Static IP addresses are controlled through a GUI on Ubuntu desktops - Network Manager is the name, I think.
For "servers" (systems without a GUI), the /etc/network/interfaces file controls this.  **man interfaces** will explain the options, but something like:

```
auto lo
iface lo inet loopback


auto eth0
# iface eth0 inet dhcp
iface eth0 inet static
  address 192.168.1.99
  gateway 192.168.1.1
  netmask 255.255.255.0
  dns-nameservers 192.168.1.1
```
is probably what you need.

Of course, your network will dictate the specific values, so don't just copy these settings. It could be bad, very bad, if you do without understanding.

You can setup a NAT subnet for all your VMs and let those systems be on the same subnet.  Follow the instructions provided by the VM tools you are using.  NAT'd networks are great. I use them all the time and leverage "RFC 1918" addresses. Google that to learn more.

If you are at a college/university, how to get more IPs or setup a router is something others in your school can help with.

Learning a little bit about networking is easy. There are tutorials on the internet - pages, how-to guides, videos, and complete courses [https://ipv6.he.net/certification/](https://ipv6.he.net/certification/) to bring understanding to whatever level you want/need.

---

