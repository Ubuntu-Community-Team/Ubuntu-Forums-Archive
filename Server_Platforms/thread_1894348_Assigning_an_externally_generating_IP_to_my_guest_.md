---
title: "Assigning an externally generating IP to my guest VM while using KVM."
date: 2011-12-12
forum: Server Platforms
---

### Post by covertcj on 2011-12-12
I'm using a configuration of KVM and Virsh to manage some VMs on my server without a GUI, and haven't had any trouble getting them set up; however, I can't seem to figure out how to give my VM a true bridged network connection. Whenever I start my VM, it is assigned an IP address of 192.168.xxx.xxx, and I'm looking for a way to have it assigned an IP from the DHCP server on my campus instead.

EDIT: My VM was created with ubuntu-vm-builder using a command like:

```

ubuntu-vm-builder kvm hardy \
                  --domain newvm \
                  --dest newvm \
                  --hostname ahostname \
                  --mem 512 \
                  --user john \
                  --pass doe \
                  --components main,universe \
                  --addpkg vim \
                  --addpkg openssh-server \
                  --libvirt qemu:///system ;

```

I currently have tried creating a bridged interface on my server (my /etc/network/interfaces looks like the following):

```

auto lo
iface lo inet loopback

auto br0
iface br0 inet dhcp
        bridge_ports eth0
        bridge_stp on
        bridge_fd 0
        bridge_maxwait 0

```

and then I changed the default <iterface type='network'> tag to the following:

```

<interface type='bridge>
    <mac address='52:54:00:3a:e6:5e'/>
    <source bridge='br0'/>
<interface type='bridge>

```

With this setup, my VM *is* actually assigned a proper IP (137.112.xxx.xxx at the moment); however, it has very strange network connectivity issues. Logging into the VM via ssh and pinging google.com works, but pinging some other sites (ex ping security.ubuntu.com) won't work. Also, pinging <hostname of vm>.example.com from outside the host machine doesn't work either.

Is there something I'm doing wrong? Or perhaps, is there another way I can make my machine accessible from outside the Host machine, as that is really my end goal here.

EDIT: I'm using Oneiric for both the host and guest machines, if that helps.

Thanks,
Chris Covert

---

### Post by covertcj on 2011-12-12
It turns out that the network was blocking my VM's internet traffic, and that the problem wasn't with my configuration.

---

