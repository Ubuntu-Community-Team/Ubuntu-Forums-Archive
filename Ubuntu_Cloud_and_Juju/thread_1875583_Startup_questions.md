---
title: "Startup questions"
date: 2011-11-05
forum: Ubuntu Cloud and Juju
---

### Post by ELMIT on 2011-11-05
I tried the cloud on a flashdrive. 

My desktop shows: netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth2
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth2
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth2
192.168.122.0   0.0.0.0         255.255.255.0   U         0 0          0 virbr0


I start the image with sudo kvm -hda binary.img -m 1024
since testdrive only works with iso

I follow the instruction in the GetingStarted manual and the last line ssh fails.

After nova-setup.sh I see for netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         10.0.2.2        0.0.0.0         UG        0 0          0 eth0
10.0.2.0        0.0.0.0         255.255.0.0     U         0 0          0 eth0
192.168.122.0   0.0.0.0         255.255.255.0   U         0 0          0 virbr0


I am sure my mistake is at:
Note: adjust bridge_interface if you are using a different interface ...

If I just follow through with the guide and do as it says, the only error comes up at the last line ssh ... 


What do I need to adjust to get it working? and where? novarc?

The system can go to the Internet with the browser, but I have not found a way to the system from my desktop.

How can I exchange data? How can I mount a local drive to it?


The last words from the guide is funny:
All Done:

I don't think so, here it starts !!! ;-)

bye

Ronald

---

### Post by ELMIT on 2011-11-10
Can anybody give me a hand on that, please.

I started the kvm machine already 50 times but so far never succeeded to ssh into it, neither from the kvm (guest) machine nor from another machine (host).

---

