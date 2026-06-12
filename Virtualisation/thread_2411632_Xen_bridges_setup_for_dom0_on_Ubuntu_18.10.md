---
title: "Xen bridges setup for dom0 on Ubuntu 18.10"
date: 2019-02-01
forum: Virtualisation
---

### Post by stevenvsi2 on 2019-02-01
Hi All Xen experts,

I hope I can start using Xen with Ubuntu since Xen Centos community does not really exist anymore.
I have been running it for almost 20 years now and have relatively old VMs I would like to run as is IF possible.

I got started with this link:
[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)

I am trying to setup the bridge BUT as of late Ubuntu all network configuration files are made with the infamous YAML syntax (equate nightmare and hours lost).
The above document is for the old syntax and assume DHCP, which we will not be using.

An additional pain seems to be that somehow the eth0 now is named eno1: I assume it is a o and not a zero AND it is a 1 not a lower case L, see already how helping this adds to the YAML issues!

eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 142.44.136.79  netmask 255.255.255.0  broadcast 142.44.136.255
        inet6 fe80::a6bf:1ff:fe1e:8de2  prefixlen 64  scopeid 0x20<link>
        ether a4:bf:01:1e:8d:e2  txqueuelen 1000  (Ethernet)
        RX packets 802076  bytes 1115505036 (1.1 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 120995  bytes 15878802 (15.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device memory 0xa0b00000-a0bfffff

Now after re enabling the old network management with ifdown I get all kind of error messages:

ifdown: interface enol not configured
ifup: missing required variable: address
ifup: missing required configuration variables for interface xenbr0/inet
ifup: failed to bring up xenbr0

It seems pretty basic stuff to me BUT with all these new changes to syntax to Ubuntu and the old documentation I wonder if anyone found a way to configure the bridge either with the old syntax of the new one?

Any help will be appreciated. 

Best Regards,

Steven,

---

### Post by stevenvsi2 on 2019-02-10
Well, it looks like no distribution bothers with Xen anymore.

Tried: Opensuse, Ubuntu, Fedora, Centos, Citrix...the all have no updated documentation AND no portability unless one is willing to invest 500 hours to decode the messy notes across forums etc.

I am keeping an old Centos 6 running while I decide what to do.

Open source has its limits apparently.

Regards,

---

### Post by heiko_s on 2019-02-18
Sorry for the late reply. I have been using Xen until late 2015. I'm currently using kvm on Linux Mint 19.1, which is Ubuntu 18.04 based.

If it's only configuring the network bridge, you could use the Network Manager to set it up. Have a look here: [https://heiko-sieger.info/define-a-network-bridge-using-ubuntus-linux-mints-network-manager-application/]("https://heiko-sieger.info/define-a-network-bridge-using-ubuntus-linux-mints-network-manager-application/"). This requires a desktop GUI, of course.

Hope it helps.

---

