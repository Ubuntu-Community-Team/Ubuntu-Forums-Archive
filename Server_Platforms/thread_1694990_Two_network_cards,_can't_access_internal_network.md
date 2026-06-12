---
title: "Two network cards, can't access internal network"
date: 2011-02-25
forum: Server Platforms
---

### Post by lybbe on 2011-02-25
Hi,

I've installed Ubuntu Server 10.10 with two network cards. One for external, and one internal.

My problem is that as soon as i activate eth1 (external), i can't access the server from the internal network (eth0)

/etc/network/interfaces:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.2.XX
        netmask 255.255.255.0
        #gateway 192.168.2.XX

auto eth1
iface eth1 inet static
        address XX.XXX.XXX.XX
        netmask 255.255.255.224
        gateway XX.XXX.XXX.XX
        dns-nameservers 8.8.8.8

With these settings i can't reach the internal network from inside

If i disable the gateway on eth1 and enable the gateway on eth0, it works.

Any clues?

Thanks in advance

---

### Post by HugoSerrano on 2011-02-25
Hi.

is your internal network in the same network address, 192.168.2.0/24? You got your eth0 connected to switch or a router?

If you are on the same network, you should be able to ping that IP. 

Regards.

---

### Post by lybbe on 2011-02-25
Hi,

Yes, my internal network is 192.168.2.0/24. I'm trying to ping the server from another machine, but it doesn't work.

I can ping from the server to other servers on 192.168.2.0/24 though.

ufw is disabled, and apparmor aswell.

Thanks

---

### Post by elico on 2011-02-25
the question was about the other interface ip.

what idoes  XX.XXX.XXX. means?
auto eth1
iface eth1 inet static
        address XX.XXX.XXX.XX

try another thing just to see if its your ip settins.

change to this:
> 
auto eth1
iface eth1 inet dhcp
#address XX.XXX.XXX.XX
#netmask 255.255.255.224
#gateway XX.XXX.XXX.XX
        #dns-nameservers 8.8.8.8


and try to ifup the interface.

if it works fine then your settings of the ip are bad.

also if you can give us output of the command:
> route -n

---

### Post by HugoSerrano on 2011-02-25
> **lybbe said:**
> Hi,

Yes, my internal network is 192.168.2.0/24. I'm trying to ping the server from another machine, but it doesn't work.

I can ping from the server to other servers on 192.168.2.0/24 though.

ufw is disabled, and apparmor aswell.

Thanks


hummm... you got any service running in that machine? try to do:
$ telnet IP.of.the.server Serviceport

see if it open something or if it says "connecting..."

Regards

---

### Post by gsgleason on 2011-02-25
On which network is the device from which you cannot reach the server?

If you're trying from anywhere other than the same network as eth0 (192.168.2.0/24), it's not going to work, because that server is going to try to send any traffic to any network other than those to which it's directly attached to the gateway via eth1.

If that be the case, you'll need to add some static routes for the other private networks.

---

### Post by lybbe on 2011-02-25
Guys, 

I did a reinstall of the server, and now it's working. Don't know if it was a typo or what it was, but now it works.

Thanks to ya all for trying to help. Really great community out there!

---

