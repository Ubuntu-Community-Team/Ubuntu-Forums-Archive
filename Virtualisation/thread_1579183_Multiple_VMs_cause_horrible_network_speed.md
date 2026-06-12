---
title: "Multiple VMs cause horrible network speed?"
date: 2010-09-21
forum: Virtualisation
---

### Post by fowie on 2010-09-21
I'm using qemu to run four Windows Server 2003 VMs simultaneously on a dual quad-core XEON server with a 1GB ethernet connection.  I set up a bridge (br0) so ifconfig (when the VMs are running) looks like:
```


br0       Link encap:Ethernet  HWaddr 00:22:19:5a:a7:08
          inet addr:192.168.1.30  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:19ff:fe5a:a708/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:824020 errors:0 dropped:0 overruns:0 frame:0
          TX packets:304939 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:56439141 (56.4 MB)  TX bytes:339501150 (339.5 MB)

eth0      Link encap:Ethernet  HWaddr 00:22:19:5a:a7:08
          inet6 addr: fe80::222:19ff:fe5a:a708/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:743053 errors:0 dropped:0 overruns:0 frame:0
          TX packets:319771 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:111468760 (111.4 MB)  TX bytes:81531399 (81.5 MB)
          Interrupt:37 Memory:ec000000-ec012800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4800 (4.8 KB)  TX bytes:4800 (4.8 KB)

tap0      Link encap:Ethernet  HWaddr 16:26:dd:1b:e7:53
          inet6 addr: fe80::1426:ddff:fe1b:e753/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32518 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63074 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:2166751 (2.1 MB)  TX bytes:89029314 (89.0 MB)

tap1      Link encap:Ethernet  HWaddr 5a:f2:9b:6d:9a:84
          inet6 addr: fe80::58f2:9bff:fe6d:9a84/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39513 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76421 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:2792581 (2.7 MB)  TX bytes:107634643 (107.6 MB)

tap2      Link encap:Ethernet  HWaddr b6:59:07:ae:ae:2b
          inet6 addr: fe80::b459:7ff:feae:ae2b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3457 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6673 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:438758 (438.7 KB)  TX bytes:4163295 (4.1 MB)

tap3      Link encap:Ethernet  HWaddr 86:09:1a:a2:f5:19
          inet6 addr: fe80::8409:1aff:fea2:f519/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:57354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94298 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:4696892 (4.6 MB)  TX bytes:119237696 (119.2 MB)

```

but in this configuration, if, say, I'm downloading a file on all four VMs, only one VM at a time seems to get any internet access, and the others just sit and spin until that one is done.  Is something not set up correctly so that they will properly share the network?  My qemu line looks like:
```


qemu-system-x86_64 -hda /srv/VirtualMachines/img/DBear.img -net nic -net tap,script=/etc/qemu-ifup -vnc 192.168.1.30:1 -smb /mnt/vmshare &
qemu-system-x86_64 -hda /srv/VirtualMachines/img/Lightwave.img -net nic -net tap,script=/etc/qemu-ifup -vnc 192.168.1.30:2 -smb /mnt/vmshare &
qemu-system-x86_64 -hda /srv/VirtualMachines/img/Tackaboo.img -net nic -net tap,script=/etc/qemu-ifup -vnc 192.168.1.30:3 -smb /mnt/vmshare &
qemu-system-x86_64 -hda /srv/VirtualMachines/img/Maltby.img -net nic -net tap,script=/etc/qemu-ifup -vnc 192.168.1.30:4 -smb /mnt/vmshare &

```

---

### Post by TheFu on 2010-09-22
You'll need to know exactly which network chips your system is using and be very specific about which virtual network hardware you present to each VM.  This applies to all VM solutions, not just KVM.  You may need/want to go to the extra effort of installing the virtio network drivers too.  [http://www.linux-kvm.org/page/Virtio](http://www.linux-kvm.org/page/Virtio)

Here's a Qemu version [http://www.carfax.org.uk/docs/qemu-virtio](http://www.carfax.org.uk/docs/qemu-virtio)  Can't tell how current this advice is. I don't use Qemu.

---

### Post by fowie on 2010-09-22
Ok, I do know what network chips are in my machine, I'm using the virtio interfaces already (my line now has -net nic,model=virtio), is there anything else I can do?  I was looking into putting each vm on a separate vlan, but that just removed network connectivity from every vm whose vlan != 0...

---

