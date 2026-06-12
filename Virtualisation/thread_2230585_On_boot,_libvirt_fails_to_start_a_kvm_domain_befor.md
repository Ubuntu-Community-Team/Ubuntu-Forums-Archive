---
title: "On boot, libvirt fails to start a kvm domain before bridge is up"
date: 2014-06-20
forum: Virtualisation
---

### Post by Erik-NA on 2014-06-20
I have a KVM domain which libvirt cannot start when the KVM host boot due to the fact that the network bridge is not yet started. It takes a while before the bridge is up, about 10-20 seconds.
One solution is to change that libvirt bin shall wait for the bridge before starting, but all instructions about that assumes a startup job, but libvirt-bin startup is a common init-script.
[PHP]
#! /bin/sh
#
# Init script for libvirtd
#
# (c) 2007 Guido Guenther <agx@sigxcpu.org>
# based on the skeletons that comes with dh_make
#
### BEGIN INIT INFO
# Provides:          libvirt-bin libvirtd
# Required-Start:    $network $local_fs $remote_fs $syslog
# Required-Stop:     $local_fs $remote_fs $syslog
# Should-Start:      hal avahi cgconfig
# Should-Stop:       hal avahi cgconfig
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: libvirt management daemon
### END INIT INFO[/PHP]

How do I solve this problem? The bridge name is br2.

Using ubuntu 14.04

---

### Post by TheFu on 2014-06-22
How is/was the bridge created?
I don't see this issue by creating bridges in the /etc/networking/interfaces file.

---

### Post by Erik-NA on 2014-06-22
The bridge is configured in /etc/networking/interfaces. When you are mentioning this it is can related to that link speed is only 100 Mbit/s when it should be 1000 Mbit/s. I have swapped to a new network card (Intel) so the hardware should be correct. The other end is a Dovado Pro router (in bridged LTE mode) and the result is 100 Mbit/s link speed on all ports (1-4). If I force the network link speed to 1000 Mbit/s I have no connection.

/etc/networking/interface
[PHP]auto eth2
iface eth2 inet manual
        up ifconfig eth2 0.0.0.0 promisc up
        down ifconfig eth2 down

auto br2
iface br2 inet manual
   bridge_ports eth2
   bridge_stp off
   bridge_fd 5
   bridge_hello 1
   bridge_maxwait 0
[/PHP]

---

### Post by TheFu on 2014-09-02
Well - you can't force 1 side of a link to be faster than the other side can handle.  100Mbps is the best you'll ever get until you update the port where the computer connects. For LAN connections, you can drop in a cheap $20 GigE switch and connect all PCs to it on the same LAN, then connect 1 port from that switch to the router.  All the PCs on the switch will talk GigE if their hardware supports it.

I wouldn't set br2 to manual. Why would you do this?

Sorry if I'm missing other parts - just read the last message and I've completely forgotten everything else. Slept since this started.

---

### Post by Erik-NA on 2014-09-02
Something is wrong in the setup somewhere, but I cannot find where. The switch where the NIC is connected to has support for up to 1Gbit/s and for some reason the bridge takes soo long to establish which causes libvirt failing to start the VM at kvm host boot.

I suspect it may be related to an attempt on my part to set up the network interface so the virtual instance has exclusive access to the network card - an attempt that I was not successful with.

My last solution is a reinstall...

---

