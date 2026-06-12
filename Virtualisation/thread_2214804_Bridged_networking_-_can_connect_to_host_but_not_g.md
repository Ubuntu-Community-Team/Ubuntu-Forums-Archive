---
title: "Bridged networking - can connect to host but not gateway / anything else"
date: 2014-04-03
forum: Virtualisation
---

### Post by Antony_Nikrooz on 2014-04-03
I don't usually ask questions like this, but I've been banging my head against this one for a couple of days now:
HOST: Ubuntu 13.04 Server,  Virtualbox Version 4.2.10_Ubuntu
GUEST: Ubuntu 13.04 server also.

HOST ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:01:c0:0b:c8:7d  
          inet addr:192.168.2.220  Bcast:192.168.2.255  Mask:255.255.255.0
```

- Networking to/from host works fine.

GUEST networking: set to bridged, eth0, promisuous deny (tried all of these).
I'm running vboxheadless+phpvirtualbox, manually set IP on eth0 192.168.2.221 (netmask and gateway present and correct).

From the host, I can ping guest 192.168.2.221 fine. Can also SSH fine to the guest.
From the guest, I can ping host 2.220. But cannot ping the gateway or any other machines even on the subnet:

```
ant@n:~$ ping 192.168.2.220
PING 192.168.2.220 (192.168.2.220) 56(84) bytes of data.
64 bytes from 192.168.2.220: icmp_req=1 ttl=64 time=0.434 ms
^C
--- 192.168.2.220 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.434/0.434/0.434/0.000 ms
```



```
ant@n:~$ ping 192.168.2.254
PING 192.168.2.254 (192.168.2.254) 56(84) bytes of data.
From 192.168.2.221 icmp_seq=1 Destination Host Unreachable
From 192.168.2.221 icmp_seq=2 Destination Host Unreachable
From 192.168.2.221 icmp_seq=3 Destination Host Unreachable
^C
--- 192.168.2.254 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 3002ms
```


I have tried changing the user the VM is running as, checking vboxnetflt, even setting up old-skool TAP adapters, but nothing seems to help.
Setting adapter to NAT does allow it to contact outside, but this is a server and double-NATing the ports to/from ports over 1024 is horrible (listening on ports less than 1024 only works when running as root)

Any thoughts? Thanks!

---

### Post by TheFu on 2014-04-03
I don't use vbox on Linux (prefer KVM, especially for servers), but what does the host bridge config look like?

$ brctl show

Does vbox use the std Linux bridging?

---

### Post by Antony_Nikrooz on 2014-04-04
At the moment brctl shows an empty table. Guest machine is using virtualbox's vboxnetflt to bridge straight on to eth0.
I did have it looking a bit like this at one point, and pointing the guest to br0, but that didn't work either:

```
auto lo
iface lo inet loopback

iface eth0 inet manual

auto br0
iface br0 inet static
  address 192.168.2.220      
  netmask 255.255.255.0
  gateway 192.168.2.254


  bridge_ports eth0
```

Even tried adding:
tunctl_user vbox

---

### Post by Antony_Nikrooz on 2014-04-17
Well I rebuilt the VM with the host config back to normal and it worked... same OS, same VBox settings.

And then went with OpenVZ, much better for linux-on-linux. Only went down the virtualbox path because I thought it would be handy to be able to boot it up on Windows. And my current host (FitPC) is 32-bit which rules out the other VM environments

And unfortunately I need to do 10 posts before this forum will let me edit my display name. Sorry everybody

---

### Post by TheFu on 2014-04-17
Well, in that case - please realize that 13.04 has been out of support since JANUARY.  At this point, loading up 14.04beta2 makes the most sense. Normal update/upgrade processing will turn that version into the released LTS in a week or so.  That's 5 yrs of support/patches.  13,10 support ends in June, so it isn't a good choice either.

I'm curious - why openvz when lxc exists?  On a KVM host, lxc will co-exist and can be managed by libvirt. The downside is that virt-manager will not create LXC container, just manage them AFTER creation.

VIrtualbox has a slick interface and if desktop-on-desktop virtualization is desired, it is a fine choice.  For servers ... not so much.

---

### Post by Iowan on 2014-04-17
> **Antony_Nikrooz said:**
> And unfortunately I need to do 10 posts before this forum will let me edit my display name. Sorry everybody
100 posts won't enable you to change your username. 
All that is required is a thread in the [Resolution Centre]("http://ubuntuforums.org/forumdisplay.php?f=123").
Please read the [sticky]("http://ubuntuforums.org/showthread.php?t=1178721") first. :)

---

