---
title: "Lucid host issuing wrong ARP reply for guest VM"
date: 2010-08-06
forum: Virtualisation
---

### Post by Schmellson on 2010-08-06
Configuration

Dell R710 dual hex-core 4 nics 
Host OS - Ubuntu 10.04 server 
KVM guests OS -  Ubuntu 10.04 server

Host uses eth0 and is not bridged
Guests use bridged networking on eth1 eth2 and eth3

isolated network through dumb hub with a win xp laptop listening with wireshark

.22= host
.23 = guest vm
.25 = guest vm
.27 = guest vm
.31= laptop

ARP cache on host and guest vm's is empty

When I try to ssh from .31 to .23 I get an ARP reply from mac address for .22 stating that .23 is at .22's mac address immediately followed by an ARP reply from mac address for .23 with proper mac address for 23 but does not connect. If I immediately try again, the connection is successful. Wireshark shows the bogus ARP reply followed by the expected one, then says there is a duplicate use of .23. The symptoms range from general network instability to full-on failure. I had been researching this issue for a few weeks until I got it narrowed down to incorrect ARP information and I suspect that others are experiencing the same symptoms with the same cause. Why does the host issue an ARP reply at all let alone the wrong one? I have included a few config files, please let me know if you need more information. If I have posted too much I am sorry this is my first post. 


ifconfig of host:
br1       Link encap:Ethernet  HWaddr 82:72:40:e7:9c:10  

          inet addr:192.168.1.23  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::a6ba:dbff:fe44:9ca7/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:4304 errors:0 dropped:0 overruns:0 frame:0

          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:223135 (223.1 KB)  TX bytes:4213 (4.2 KB)



br2       Link encap:Ethernet  HWaddr 36:52:53:07:5c:20  

          inet addr:192.168.1.25  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::a6ba:dbff:fe44:9ca9/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:4301 errors:0 dropped:0 overruns:0 frame:0

          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:222888 (222.8 KB)  TX bytes:4213 (4.2 KB)



br3       Link encap:Ethernet  HWaddr a4:ba:db:44:9c:ab  

          inet addr:192.168.1.27  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::a6ba:dbff:fe44:9cab/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:4302 errors:0 dropped:0 overruns:0 frame:0

          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:224278 (224.2 KB)  TX bytes:4213 (4.2 KB)



eth0      Link encap:Ethernet  HWaddr a4:ba:db:44:9c:a5  

          inet addr:192.168.1.22  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::a6ba:dbff:fe44:9ca5/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:878 errors:0 dropped:0 overruns:0 frame:0

          TX packets:3554 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:85829 (85.8 KB)  TX bytes:233697 (233.6 KB)

          Interrupt:36 Memory:d6000000-d6012800 



eth1      Link encap:Ethernet  HWaddr a4:ba:db:44:9c:a7  

          inet6 addr: fe80::a6ba:dbff:fe44:9ca7/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:5978 errors:0 dropped:0 overruns:0 frame:0

          TX packets:764 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:479527 (479.5 KB)  TX bytes:81545 (81.5 KB)

          Interrupt:48 Memory:d8000000-d8012800 



eth2      Link encap:Ethernet  HWaddr a4:ba:db:44:9c:a9  

          inet6 addr: fe80::a6ba:dbff:fe44:9ca9/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:6142 errors:0 dropped:0 overruns:0 frame:0

          TX packets:592 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:500468 (500.4 KB)  TX bytes:59539 (59.5 KB)

          Interrupt:32 Memory:da000000-da012800 



eth3      Link encap:Ethernet  HWaddr a4:ba:db:44:9c:ab  

          inet6 addr: fe80::a6ba:dbff:fe44:9cab/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:6711 errors:0 dropped:0 overruns:0 frame:0

          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:555480 (555.4 KB)  TX bytes:4527 (4.5 KB)

          Interrupt:42 Memory:dc000000-dc012800 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:39874 errors:0 dropped:0 overruns:0 frame:0

          TX packets:39874 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:2798773 (2.7 MB)  TX bytes:2798773 (2.7 MB)



virbr0    Link encap:Ethernet  HWaddr d2:d9:8a:9a:bf:06  

          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0

          inet6 addr: fe80::d0d9:8aff:fe9a:bf06/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:0 (0.0 B)  TX bytes:5043 (5.0 KB)



vnet0     Link encap:Ethernet  HWaddr 82:72:40:e7:9c:10  

          inet6 addr: fe80::8072:40ff:fee7:9c10/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:742 errors:0 dropped:0 overruns:0 frame:0

          TX packets:4717 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:500 

          RX bytes:72426 (72.4 KB)  TX bytes:327191 (327.1 KB)



vnet1     Link encap:Ethernet  HWaddr 36:52:53:07:5c:20  

          inet6 addr: fe80::3452:53ff:fe07:5c20/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:568 errors:0 dropped:0 overruns:0 frame:0

          TX packets:4543 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:500 

          RX bytes:51296 (51.2 KB)  TX bytes:308697 (308.6 KB)


/etc/libvirt/qemu/test-23.xml:

<domain type='kvm'>

  <name>test-23</name>

  <uuid>3698c57b-f18c-d1a0-761f-6affd63fa415</uuid>

  <memory>4194304</memory>

  <currentMemory>4194304</currentMemory>

  <vcpu>4</vcpu>

  <os>

    <type arch='x86_64' machine='pc-0.12'>hvm</type>

    <boot dev='hd'/>

  </os>

  <features>

    <acpi/>

    <apic/>

    <pae/>

  </features>

  <clock offset='utc'/>

  <on_poweroff>destroy</on_poweroff>

  <on_reboot>restart</on_reboot>

  <on_crash>restart</on_crash>

  <devices>

    <emulator>/usr/bin/kvm</emulator>

    <disk type='file' device='disk'>

      <driver name='qemu' type='raw'/>

      <source file='/var/lib/libvirt/images/test-23.img'/>

      <target dev='vda' bus='virtio'/>

    </disk>

    <disk type='file' device='cdrom'>

      <driver name='qemu' type='raw'/>

      <source file='/var/lib/libvirt/images/ubuntu-10.04-server-amd64.iso'/>

      <target dev='hdc' bus='ide'/>

      <readonly/>

    </disk>

    <interface type='bridge'>

      <mac address='52:54:00:38:5d:9d'/>

      <source bridge='br1'/>

      <model type='virtio'/>

    </interface>

    <console type='pty'>

      <target port='0'/>

    </console>

    <console type='pty'>

      <target port='0'/>

    </console>

    <input type='mouse' bus='ps2'/>

    <graphics type='vnc' port='-1' autoport='yes'/>

    <video>

      <model type='cirrus' vram='9216' heads='1'/>

    </video>

  </devices>

</domain>

---

