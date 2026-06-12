---
title: "remove non existent interface eth0 (server 14.04)"
date: 2016-02-06
forum: Server Platforms
---

### Post by doktor2 on 2016-02-06
Hello,

my server has only one Ethernet interface originally called eth0.

after some lxc bridged network configuration running ifconfig -a output is 3 interfaces: lo eth0 rename.
the eth0 mac is FF:FF:FF:FF:FF:FF and rename interface has the correct interface mac address.

I’ve changed rename to lan but was wondering how can remove that eth0

I’ve tried to troubleshoot this after removing the lxc package with cleanup and all the config files deleted
 tried to delete everything added to /etc/network/interfaces , rn /etc/udev/rules.d/70-persistent-net.rules , iptables -F 

please assist,
Doktor

---

### Post by TheFu on 2016-02-06
Network device assignment happens in  /etc/udev/rules.d/70-persistent-net.rules  based on the MAC address for each device.
a) it is safe to remove all the lines and at the next boot, eth0 will be reassigned.
b) it is safe to change the eth? for the MAC as you like.

Bridge settings can happen in a few different places. I've always put it into /etc/network/interfaces, but there are a few others too.  Use brctl to manage bridges. /etc/network/interfaces.d/ could be somewhere to look.  Also, I know that libvirt sets up vnet0, 1, 2 interfaces and those are controlled either through a GUI (virsh or virt-manager) or by the config files under /etc/libvirt.  There is an lxc,.conf file in there. Also found,  /etc/libvirt/qemu/networks/default.xml and an empty "autostart" directory.  Don't recall today, but thought I removed everything from autostart last year - I like to control everything on the network here.

I don't know enough about LXC to write intelligently about it, but I won't let that stop me. ;) Thought each container got to name the network device in the lxc-config file for that container.  Though LXC network devices were tied to the bridge named lxcbr0 by default. Found my notes ...  /var/lib/lxc/ is where the settings are put by default for each container. There's an lxc.network.link option inside the file.

Hope that helps.  BTW, at this point, I wouldn't use any LXC/Docker or similar container on the internet for anything important.  Sure, hosting cat videos might be fine, since being hacked doesn't really harm anyone, but if you have real users, I consider the risks and unknowns for all containers too great of a risk today.  Maybe in 2020, when the security model has been better tested by others?

---

### Post by MAFoElffen on 2016-02-07
Wouldn't it better for others to see what is actually going on, so they could recommend anything on that info?

If we could see what your output is for your (you could dummy it up for security)
```

ifconfig -a
sudo lshw -class network
sudo brctl show

```
And the opening screen on an ssh connect... which shows what network devices, ip assignments, and any bridges that are active for that server... Then someone would not have to guess at all the possibilities that could be. (Narrow the scope)

I'm sort of leaning to what TheFu was concerned about... on if you disable eth0, that would/should disable any bridges bound to that also. If bound to a bridge, whether that bridge is for Docker, LXC, KVM, etc, then you usually tell it to come up as auto, manual, then bind the bridge to the device. Someone could tell me I'm wrong, but my understanding says it has to be active and up for the bond devices to be able to bridge across it. It can't bridge across a device that is not enabled. Following that same logic-- Disabling would be like expecting a connection to something, even though a network cable was unplugged, right?

---

### Post by darkod on 2016-02-09
Are you actually still running bridge configuration or not?

Because if you are, I don't think you can remove/disable the underlying physical interface. The bridge still needs it.

On the other hand, if you deleted your bridge config but there are some leftovers interfaces, you need to dig deeper to solve it I guess. Did you remove any bridge config properly? That should "liberate" your eth0 to be used as standard physical interface again. But I haven't worked with LXC at all, so I can't really advise in details.

It might also help to post the current content of /etc/network/interfaces to see what's there. And assuming LXC puts its config there.

---

### Post by TheFu on 2016-02-09
> **darkod said:**
>  
It might also help to post the current content of /etc/network/interfaces to see what's there. And assuming LXC puts its config there.

LXC does not put configs in there, but it can use those settings; mainly using a manually created bridge instead of using their automatically created bridge from LXC installation-time.

---

### Post by MAFoElffen on 2016-02-09
LOL... That is why I asked for what I did, which included:
```

sudo brctl show

```
If he showed the output I asked for and if he removed lxc in an obscure kind of manner, and lxcbr0 was still coming up ... then the Op should look for the presence of:
```

ls /etc/init/lxc-net.conf
ls /etc/dnsmasq.d/lxc
ls /etc/defaults/lxc.conf

```
During upstart, the script lxc-net.conf dynamically creates, configs and binds the bridge lxcbr0. Besides creating that standalone lxcbr0 bridge, it also sets up dnsmasq to serve dhcp on this bridge on the 10.0.3.0/24 subnet and sets up a few iptables rules (masquerade) so the containers have internet access. It also has a number of flags to enable domains, change subnets etc... That lxc.conf file in /etc/defaults/ is the system default of created containers. In the network section of that file, would bind that net to a bridge, whether the default, or if the OP changed that. For containers, it's in /var/lib/lxc/<containerName>/lxc.conf.

In those "2" lxc.conf files, if using a hardwired bridge, then it binds using the logical device name and the hardware mac address of that device...

So, yes ... still waiting on output from the OP.

---

### Post by doktor2 on 2016-02-24
LOL, I actually changed from lxc to kvm after TheFu cat's security remark :)

since then I've successfully removed all the bridges and the eth0 remainder. 

thanks for helping,
Doktor

---

