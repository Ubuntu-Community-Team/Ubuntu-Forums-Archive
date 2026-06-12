---
title: "KVM Bridge issues, no connection"
date: 2014-04-25
forum: Virtualisation
---

### Post by npinn001 on 2014-04-25
So I have installed KVM on my remote server, and am using virt-manager to configure a new VM.

Prior to that, I had a static IP on the server of 192.168.1.10 on eth0 as:

```
auto lo eth0
iface lo inet loopback
iface eth0 inet static
	address 192.168.1.10
	netmask 255.255.255.0
	gateway 192.168.1.1
```

I then added a bridge as br0 by typing  # brctl addbr br0

I then did  # brctl addif br0 eth0

And then went in to /etc/network/interfaces and made it say:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address 192.168.1.10
        netmask 255.255.255.0
        gateway 192.168.1.1
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0
```

I can now connect to the host server at 192.168.1.10 - great.

But, when I start a VM, using the br0 bridge, it has no network connection? What am I doing wrong?

Thanks

---

### Post by heiko_s on 2014-04-25
Try this one (adopt to your needs):
```
auto lo
iface lo inet loopback

auto xenbr0

iface xenbr0 inet static
# IP of Linux Mint dom0:
address 192.168.0.120
broadcast 192.168.0.255
netmask 255.255.255.0
# IP of router or modem:
gateway 192.168.0.1
# IP of the DNS name server (if you don't know, use the Google DNS server below):
dns-nameservers 8.8.8.8
bridge_ports eth0
# disable Spanning Tree Protocol - optional:
bridge_stp off
# bridge_waitport 0   # no delay before a port becomes available - optional
# bridge_fd 0    # no forwarding delay - optional
```

Check with ifconfig after restarting the network.

---

### Post by jasonvp on 2014-04-25
It would seem that these lines:

> 
```

        address 192.168.0.10
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.1.1

```


indicate your network should never work.  You've set the default route (gateway) to an address on a different subnet.

---

### Post by npinn001 on 2014-04-26
> **jasonvp said:**
> It would seem that these lines:



indicate your network should never work.  You've set the default route (gateway) to an address on a different subnet.

Thanks - that was a typo on my part, the actual settings seem to be right. Woops!

---

### Post by npinn001 on 2014-04-26
> **heiko_s said:**
> Try this one (adopt to your needs):
```
auto lo
iface lo inet loopback

auto xenbr0

iface xenbr0 inet static
# IP of Linux Mint dom0:
address 192.168.0.120
broadcast 192.168.0.255
netmask 255.255.255.0
# IP of router or modem:
gateway 192.168.0.1
# IP of the DNS name server (if you don't know, use the Google DNS server below):
dns-nameservers 8.8.8.8
bridge_ports eth0
# disable Spanning Tree Protocol - optional:
bridge_stp off
# bridge_waitport 0   # no delay before a port becomes available - optional
# bridge_fd 0    # no forwarding delay - optional
```

Check with ifconfig after restarting the network.

Thanks - I've matched all the settings, but still no network connection on the guest. Wondered if it was in KVM settings:

When I select the bridge it says:

```
Host device eth0 (Bridge 'br0')
```

Which looks right?

Device model says Virtio. Other options are pcnet, e1000, net2k_pci, rtl8139. It also has its own mac address.

I know i must be close, but cant work out whats not right?

---

### Post by jasonvp on 2014-04-26
> **npinn001 said:**
> Thanks - that was a typo on my part, the actual settings seem to be right. Woops!

OK, I see you corrected some of the post.  What about the *broadcast* setting on the br0 interface?  Is it 192.168.0 or 192.168.1?

---

### Post by npinn001 on 2014-04-27
> **jasonvp said:**
> OK, I see you corrected some of the post.  What about the *broadcast* setting on the br0 interface?  Is it 192.168.0 or 192.168.1?

I just look again, and i havent set the broadcast on br0, I'd managed to paste 2 bits together when typing the post. When i check ifconfig, the broadcast is 192.168.1.255 which is right.

Should I specify this for br0?

---

### Post by npinn001 on 2014-04-27
So its a firewall issue. I have ufw enabled, and when I just disabled it for a second I got network access.

Why is it blocking the bridge if I can get online on the host?

---

