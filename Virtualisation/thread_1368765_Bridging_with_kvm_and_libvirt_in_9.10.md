---
title: "Bridging with kvm and libvirt in 9.10"
date: 2009-12-31
forum: Virtualisation
---

### Post by uopjohnson on 2009-12-31
I've been messing with bridging for a couple of days now and I'm not getting any results. 
The host is 9.10 following the instructions at [https://help.ubuntu.com/community/KVM/](https://help.ubuntu.com/community/KVM/) on a clean upgraded amd64 server install.
The bridge works fine and I can ping out from the host.  When I create a new guest with python-vm-builder it works just fine using the default network interface, however as soon as I switch it over to bridged the guest can't get an address from dhcp.  If I give it a static address the guest can ping the host, but nothing outside of the host (gateway, other lan machines, yahoo).  

I had this working in an 8.10 install on this machine so I know it can be done, I just don't understand what the problem might be.  If I import known good guests from the previous install they do not work either so the problem must be on my host install.
I can't find any relevant log entries anywhere so I don't even know where to start.  At this point some validation that SOMEONE has successfully used bridged networking with Karmic, libvirt, and kvm would be a big help.

Edit:  I did a fresh 8.04 install and everything bridged and worked as expected.

---

### Post by geekshlby on 2009-12-31
Please post the interface section of the VM's xml.

Thanks.

---

### Post by uopjohnson on 2009-12-31
Have you gotten this working?  Because I don't think it is a configuration problem unless something has changed that was not reflected in the server guide or the wiki.  But I hope I'm wrong because then I would have this fixed.  Let me know if I need to provide anything else.

On the host:
```
auto br0 
iface br0 inet static
 address 10.10.1.51
 netmask 255.255.255.0
 network 10.10.1.0
 broadcast 10.10.1.255
 gateway 10.10.1.1
 bridge_ports eth0
 bridge_fd 9
 bridge_hello 2
 bridge_maxage 12
 bridge_stp off
```

ubuntu.xml
```
<interface type='bridge'>
  <mac address='52:54:00:c1:46:23'/>
  <source bridge='br0'/>
  <model type='virtio'/>
</interface>
```

on the guest
```
auto br0 
iface br0 inet static
 address 10.10.1.52
 netmask 255.255.255.0
 network 10.10.1.0
 broadcast 10.10.1.255
 gateway 10.10.1.1
```

pinging host from guest
```

$ ping 10.10.1.51
64 bytes from 10.10.1.51: icmp_seq=1 ttl=64 time=2.43 ms
64 bytes from 10.10.1.51: icmp_seq=2 ttl=64 time=2.41 ms

```

pinging gateway from guest
```

From 10.10.1.52 icmp_sql=1 Destination Host Unreachable
From 10.10.1.52 icmp_sql=2 Destination Host Unreachable

```

I also completely disabled the firewall (iptables -F; iptables -X) and shutdown apparmor on the host thinking maybe they were doing something hinky, but still doesn't work.

---

### Post by geekshlby on 2009-12-31
Why run a bridge in the guest?  There can be many reasons why, I have done so to run a LXC container, UML container, or openvz container on a KVM guest.

On your guest's network configuration, the example interfaces file you posted does not indicate you are bridging the physical interface of the guest to the internal bridge of the guest.

Two options exist:
1.  Do away with the bridge inside the guest unless it is needed for other reasons, and assign ip information to eth0 inside the guest
2.  Bridge eth0 to br0 inside the guest so the physical interface will be able to talk to the network

Typically you would have the following configuration:
guest eth0 -> host bridge ->host interface

But you have:
guest br0 -> no physical guest interface -> host bridge -> host interface

Your host interface appears to be configured correctly, your networking inside the guest is a bit mangled.

To move further along in problem determination, please let us know why you are using a bridge inside the guest.

--thanks

---

### Post by uopjohnson on 2009-12-31
I'm not, I just mistyped that.  Hard to copy from virt-viewer.  Should have been
guest /etc/network/interfaces
```
auto eth0 
iface eth0 inet static
 address 10.10.1.52
 netmask 255.255.255.0
 network 10.10.1.0
 broadcast 10.10.1.255
 gateway 10.10.1.1

```

I have also done 
```
auto eth0 
iface eth0 inet dhcp

```
Which results in the dhcp lookup timing out without ever getting an address.

---

### Post by geekshlby on 2009-12-31
Thanks for the updated information.

<stumped>it really does work :)</stumped>

When the guest is up and running, does the bridge on the host see the mac of the guest?
brctl showmacs br0

Have you attempted to redefine the guest?
virsh define path_to_guest_xml

Is guest eth0 truly guest eth0? 
Does /etc/udev/rules.d/70-persistent-net.rules list eth0 as having the same mac as what the xml states?

---

### Post by uopjohnson on 2009-12-31
So you have successfully done bridging with 9.10?
> When the guest is up and running, does the bridge on the host see the mac of the guest?
brctl showmacs br0

```

brctl showmacs br0
  2	52:54:00:c1:46:23	no		   7.04 <- the guest
  2	d2:bb:50:9f:2e:31	yes		   0.00 <- vnet0

```
I assume that vnet0 is being created and used to connect the guest to the bridge.  

> Have you attempted to redefine the guest?
Yes.  Several times.  Even undefined and defined again.

> Is guest eth0 truly guest eth0?
Does /etc/udev/rules.d/70-persistent-net.rules list eth0 as having the same mac as what the xml states?
No. But I was messing with the MAC address on the guest to see if that was causing a problem.  I edited 70-persistent-net.rules and rebooted the guest, still doesn't work.  Does changing this file fix the problem, or is that a symptom of a udev problem somewhere else?

This is the first time I have seen anything different though so I'm going to build a second guest and see if the MAC address is correct in the new guest.

---

### Post by uopjohnson on 2010-01-01
> **uopjohnson said:**
> 
This is the first time I have seen anything different though so I'm going to build a second guest and see if the MAC address is correct in the new guest.
Ok built a new guest and the udev rules are correct.  The previous problem was a result of me messing with the mac address.  
I'm still stymied here and looking for some validation that someone is successfully doing bridging with 9.04 or 9.10.

---

### Post by uopjohnson on 2010-01-06
Bump...  if anyone has setup bridging with a 9.10 Karmic host please let me know.  Just knowing it is possible would be nice.

---

### Post by nebajoth on 2010-01-14
bump

I want to know too.  I had this working on 32-bit, but it isn't working on 64-bit.

---

### Post by pedricus on 2010-01-16
Hey,

i'm fairly new to linux and not much programming experience so be gentle.

This is a slightly bizarre situation, but I can confirm that i am running ubuntu 9.10, fresh install, successfully running bridging with kvm and libvirt on 64bit with a guest winxp station. bridging works everytime even after rebooting the host.  I can successfully ping from the guest system to the host, and all the way to the internet and the host can successfully ping to the guest and out to the internet. BUT for whatever reason, the host network manager applet thinks it does not have a network connection, and the host is unable to resolve any DNS. Occasionally when the host boots, it can't ping out at all.

I followed the 9.10 server help pages off the ubuntu website.  seemed pretty straight forward, but I can't figure out why my DNS isn't sticking on the host machine.  on the rare occasion running sudo dhclient will fix this issue, but most of the time it doesn't.  Not sure if we can somehow work together to fix eachother's issues or not, but at least I can confirm this works... sortof...

---

### Post by chakoshi on 2010-01-16
I also found this situation, bridging nics of 9.10 guest and a 9.10 host is not working, the host even cant see the guest mac address, exactly the same configuration by 9.04 on 9.04 works for me so I think it may be some thing retelated to 9.10. I've also trie 9.04 guest on the 9.10 host and it works with no problem.

---

### Post by pedricus on 2010-01-17
I seem to have gotten it working and stable... not sure if i just got lucky for now or if something's actually changed.... so here's what i did...

-installed setup br0 in /etc/network/interfaces
-installed bridgeutils
-installed kvm/libvirt
-created guest winxp system

at this point, the guest system can ping to the net with no issues, but the host system can only ping internally (seemed to be unable to resolve dns past the router, even though the guest could?)

-much forum reading...
-uninstalled networkmanager
-everything seems to work manually
-reinstalled networkmanager (Same situation as before)
-edited /etc/network/interfaces to:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet dhcp
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

```and now everyone seems happy.   i've rebooted several times and behaviour is always consistent.  although networkmanager thinks i'm disconnected, although i'd be willing to bet if i had a second nic in there it would be able to control that with no problems.

again, perhaps i just missed something, but i wonder if there is some sort of dhcp/dns conflicting settings going on between networkmanager and bridgeutils, or something of that nature.  if anyone has any other ideas for testing my config, i'd be happy to try them.

---

