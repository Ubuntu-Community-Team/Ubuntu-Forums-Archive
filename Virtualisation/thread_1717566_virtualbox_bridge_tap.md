---
title: "virtualbox bridge tap"
date: 2011-03-30
forum: Virtualisation
---

### Post by ctarsoaga on 2011-03-30
Hi everybody,

I want to setup an ubuntu 10.10 server into a virtualbox vm. So I will need access from host to the vm and also from vm to the outside world.

As far as I understand, this is only possible by using a bridged network setup.

So, I read and followed instructions here:
[http://www.virtualbox.org/wiki/Advanced_Networking_Linux](http://www.virtualbox.org/wiki/Advanced_Networking_Linux)

Everything is working after doing these steps:
# create a tap
tunctl -t tap1 -u <user>
ip link set up dev tap1
f
# create the bridge
brctl addbr br0
brctl addif br0 tap1

# set the IP address and routing
ip link set up dev br0
ip addr add 10.1.1.1/24 dev br0
ip route add 10.1.1.0/24 dev br0

But I wonder about some things.

1. What happened here? I created a bridge device br0 and attached the tap1 port/interface to it. Also, routes were updated so that everything that goes to 10.1.1.0 will be routed through 10.1.1.1. Right?

2. As I understand, a bridge connects 2 or more network segments. But what did I just connected here? tap1 with what?

3. Once I did the steps above, I saw two new network interfaces using ipconfig -a (br0 and tap1) and the new route (10.1.1.0).
After rebooting, I don't see these interfaces anymore and also I don't see the route. Still, everything is running smooth (bidirectional network access)

So the bottom line is: everything works, but I simply don't understand how/why.

Thanks,
chris

---

