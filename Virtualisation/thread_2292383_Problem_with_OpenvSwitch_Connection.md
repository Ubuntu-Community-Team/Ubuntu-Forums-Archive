---
title: "Problem with OpenvSwitch Connection"
date: 2015-08-27
forum: Virtualisation
---

### Post by bennyfung8 on 2015-08-27
I am a beginner of SDN.

I try to implement the following topology on VMware ESXi

Controller (eth1) <=====> (eth3) Ubuntu:OpenvSwitch (eth1) <=====> (eth1) Ubuntu:Host1
                                                                                    (eth2) <=====> (eth1) Ubuntu:Host2

I try to install OpenvSwich on top of Ubuntu

The installation is not difficult as there are many tutorial online already.

I create the bridge (sw1) on top of OpenvSwitch and add the port eth3 to the bridge.

the controller can ping to the OpenvSwitch.

However, when i start to add both eth1 and eth2 to the sw1, the connection between the controller and OpenvSwitch is not working.

I ask host1 to ping host2, I can see host2 receive the ARP broadcast and try to reply to host1. 

However, host1 cannot receive the reply message and just keep sending the ARP request message.

I have no idea how to fix this issues.

Here is the "ovs-vsctl show" result
=============================
598dd255-a0f8-4fb2-bb37-3915d8ca217f
    Bridge "sw1"
        Controller "tcp:172.16.81.3:6633"
        fail_mode: standalone
        Port "eth3"
            Interface "eth3"
        Port "eth1"
            Interface "eth1"
        Port "sw1"
            Interface "sw1"
                type: internal
        Port "eth2"
            Interface "eth2"
=============================

---

