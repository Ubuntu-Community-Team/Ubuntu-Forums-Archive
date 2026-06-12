---
title: "kvm guests with static public ip"
date: 2010-12-04
forum: Virtualisation
---

### Post by jepse on 2010-12-04
Hi All!

I'm despaired with kvm the last days, unfortunately without reaching my goal!

I try to setup a kvm host with a public static ip. This Host serves n guest vms. Each of them should be reached by its own static public ip. 

What settings in /etc/network/interfaces are needed on host and on guest?

do i have to bridge eth0 and creaste for each guest vm a tap and than setup the static ip at the guest system?

---

### Post by senor_smile on 2011-01-13
> **jepse said:**
> Hi All!

I'm despaired with kvm the last days, unfortunately without reaching my goal!

I try to setup a kvm host with a public static ip. This Host serves n guest vms. Each of them should be reached by its own static public ip. 

What settings in /etc/network/interfaces are needed on host and on guest?

do i have to bridge eth0 and creaste for each guest vm a tap and than setup the static ip at the guest system?

Same issue here.  Has anyone ever successfully done this?

---

### Post by shulegaa on 2011-02-08
Same issue here.  Talk about missing documentation.  This ought to be a pretty classic set up.  When physical servers get consolidated, each VM needs a public, static IP.  Surely this is possible?  Anyone have a clue?  I've been trying and trying ... what a waste of time.

---

### Post by wuhaa on 2011-11-23
Here is a possible solution that is working for me...

I'm assuming that the host server is connected to the public network through eth0 with public ip address 10.0.0.2 (10.0.0.0/24). Also make sure that network-manager is removed/disabled.

On the host server set a bridge interface br0 (or whatever)

Install needed packages

```
aptitude install bridge-utils
```

Edit network configuration

```
vim /etc/network/interfaces
```

```
...

# Main Interface
auto eth0
iface eth0 inet manual

# KVM Bridge
auto br0
iface br0 inet static
        address 10.0.0.2
        netmask 255.255.252.0
        network 10.0.0.0
        gateway 10.0.0.1
        bridge_ports [COLOR="Red"]eth0[/COLOR]
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

...
```

Restart your network

```
invoke-rc.d networking restart
```

Network bridge is configured. When you create a new guest, set it to use bridge br0. The static public ip 10.0.0.3-254 can then be configured on the guest machines and will have public access. The qemu xml will look something like this:

```
...
    <interface type='bridge'>
      <mac address='GUEST-MAC-ADDRESS'/>
      <source bridge='[COLOR="Red"]br0[/COLOR]'/>
      <model type='virtio'/>
    </interface>
...
```

Hope that helps.



[vSolo]("http://vsolo.com/") - [Sunder Design]("http://sunderdesign.ca/")

---

### Post by wuhaa on 2011-11-23
Also make sure traffic forwarding is enabled

Edit system configuration

```
vim /etc/sysctl.conf
```

Uncomment this line and save

```
net.ipv4.ip_forward=1
```

Update the system (you may need to reboot the host server)

```
sysctl -p /etc/sysctl.conf
```

Make sure your firewall allows forwarding too...



[vSolo]("http://vsolo.com/") - [Sunder Design]("http://sunderdesign.ca/")

---

### Post by kosb23 on 2013-03-26
Hi folks, my isp gives me 2 IPs from different networks on 1 wire. I did the same but have no luck.

ip1 mask1 gateway1 - assign on br0 main host
----wire----
ip2 mask2 gateway2 - assign on guest VM

The guest has no access from/to Internet.  Somebody already faced the such situation?

---

### Post by wildmanne39 on 2013-03-26
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

