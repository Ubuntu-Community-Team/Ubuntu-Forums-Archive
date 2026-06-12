---
title: "qemu network problems"
date: 2009-01-21
forum: Virtualisation
---

### Post by Mooie on 2009-01-21
I'm having problems with kqemu and networking on my system.  The host is ubuntu, and I am emulating redhat 5.1.

Although this works perfectly, it is really slow;
 ```
sudo qemu rh.img -m 1024 -std-vga -net nic -net tap -soundhw all
```

When I try using kvm, it speeds up the system, but I am unable to connect to a network
```
sudo kvm rh.img -m 1024 -std-vga -net nic -net tap -soundhw all
```

The only thing I can think of is that it may try to use my actual network card, which requires a newer kernel than the redhat kernel supports.

any ideas? all help is appreciated.

---

### Post by redbrain on 2009-01-25
k/Qemu/KVM networking can be pretty confusing at the moment, the easiest way i find is via bridged networking.

So there are a few cool ways of doing this. If you have 2 network cards esp! Because you can set qemu/KVM to put all virtual machines networking through 1 of your network cards and leave the other for your host!

So yeah i'll guess your only having 1 network card like most people :) 

So yeah if your in ubuntu what you should do is:

```

sudo gedit /etc/qemu-ifup

```

add in:
```

#!/bin/sh
set -x
 
switch=br0
 
if [ -n "$1" ];then
        /usr/bin/sudo /usr/sbin/tunctl -u `whoami` -t $1
        /usr/bin/sudo /sbin/ip link set $1 up
        sleep 0.5s
        /usr/bin/sudo /usr/sbin/brctl addif $switch $1
        exit 0
else
        echo "Error: no interface specified"
        exit 1
fi

```

Oh and you will need to:
```

sudo chmod +x /etc/qemu-ifup

```

You may need to install:
```

sudo apt-get install bridge-utils  uml-utilities

```

Then thats all you need for your qemu/kvm stuff.
So your host networking forget what ubuntu network manager so do:

```

sudo gedit /etc/network/interfaces

```

edit it so it looks like:
```

auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto br0
iface br0 inet dhcp
bridge_ports eth0
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off

```

If you where to have 2 network cards what you would do is something like: add in the auto eth1 bla and change the bridge_ports eth0 to eth1 :) 

```
sudo /etc/init.d/networking restart
```

Now for starting your virtual machines do something like:
```

qemu-system-x86_64 -m <n_mem> -smp <n_cpu> -hda /path/to/hda.img -net nic,macaddr=00:0C:09:43:24:68,model=rtl8139 -net tap &

```

If you are using the ubuntu KVM packages just use kvm instead of qemu-system* I just like to run it from source :)

Oh yeah use emacs its nicer for editing those files :) but for everyone else's sake use gedit :) Let me know how it goes for you check out my blog for some kvm tutorials: 

I need to update the 2nd tutorial but hey! I need sleep :)
[http://redbrain.co.u/?page_id=29]("http://redbrain.co.uk/?page_id=29")
[http://redbrain.co.uk/?page_id=35]("http://redbrain.co.uk/?page_id=35")

The KVM wiki is pretty ok-ish... depends what your looking for: [http://kvm.qumranet.com/kvmwiki/Networking]("http://kvm.qumranet.com/kvmwiki/Networking")

---

### Post by gelimeri on 2010-10-14
And what if I want bridge wlan?

---

