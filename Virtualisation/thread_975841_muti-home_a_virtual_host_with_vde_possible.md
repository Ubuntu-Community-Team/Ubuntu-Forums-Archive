---
title: "muti-home a virtual host with vde: possible?"
date: 2008-11-08
forum: Virtualisation
---

### Post by hexamon on 2008-11-08
I've read the excellent doc [https://help.ubuntu.com/community/KVMFeisty](https://help.ubuntu.com/community/KVMFeisty)  However, it seems that I can find no documentation on how to properly multi-home a machine to vde.

```

[Machine1](eth0)--(p1)[VDE_SWITCH]
(eth1)                   (p2)
  |________________________|

```

(hope the drawing comes out right).

  I have tried specifying multiple -net statements such as
```

vdeq kvm BLAH.img -m 256 -serial telnet:localhost:2001,server,nowait -localtime -nographic -net nic -net vde,sock=/tmp/vde0,port=1 -net nic -net vde,sock=/tmp/vde0,port=2

```

I would expect that this creates two wires.
(1) single wire from eth0 to port1 on the VDE switch
(2) single wire from eth1 to port2 on the VDE switch

Unfortunately,  what actually happens is that some type of radioshack splitter is used instead.
(1) wire from eth0 goes to port1 AND port 2 of VDE switch
(2) wire from eth1 goes to port1 AND port 2 of VDE switch.

This of course causes some nasty behavior with MAC addresses shifting around from port to port and data gets replicated from each machine port to each VDE port

Check out the how the IN and OUT statistics match exaclty for both ports.

```

vde: port/allprint
0000 DATA END WITH '.'
Port 0001 untagged_vlan=0000 ACTIVE - Unnamed Allocatable
 IN:  pkts         26          bytes                 1315
 OUT: pkts          1          bytes                   53
  -- endpoint ID 0007 module unix prog   : vdeqemu user=rpimentel PID=12896  SOCK=/tmp/vde0.12896-00000
Port 0002 untagged_vlan=0000 ACTIVE - Unnamed Allocatable
 IN:  pkts         26          bytes                 1315
 OUT: pkts          1          bytes                   53
  -- endpoint ID 0009 module unix prog   : vdeqemu user=rpimentel PID=12896  SOCK=/tmp/vde0.12896-00001
.
1000 Success

```

Is there any way to get a multi-homed virtual host to map to a single VDE port per interface?

Thanks a ton, in advance!

---

### Post by hexamon on 2008-11-08
I may have found a reference to this problem here: [http://markmail.org/message/ku47e7mgyp6t2xt6#query:vde%20multiple%20nics+page:1+mid:jtz4g32mibo36a3u+state:results](http://markmail.org/message/ku47e7mgyp6t2xt6#query:vde%20multiple%20nics+page:1+mid:jtz4g32mibo36a3u+state:results)  but no fix spelled out.

---

### Post by hexamon on 2008-11-09
If any one knows of an active vde forum that might be able to help, that would be equally awesome.  Thanks

---

### Post by hexamon on 2008-11-09
Just wanted to offer a heads up.  If you intend to use multicast with your hosts in any way, don't use kvm.  It doesn't support it. Stick to qemu if you need multicast to work. Nothing I tried could get vde_switch to behave the right way.  Right now, I'm running with many bridges and many taps instead of vde switch.

---

