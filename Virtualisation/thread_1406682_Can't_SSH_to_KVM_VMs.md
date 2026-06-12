---
title: "Can't SSH to KVM VMs"
date: 2010-02-14
forum: Virtualisation
---

### Post by robinharvey on 2010-02-14
Hi,

I want to use bridged networking with KVM/virsh but this wont work.  I *think* I followed the Ubuntu docs to the letter, i.e those here :  [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM).  Here's my /etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet dhcp
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

```
...and my resolv.conf...
```

nameserver 192.168.122.1
nameserver 8.8.8.8
nameserver 8.8.4.4

```
...and the command to create the VM...
```

sudo ubuntu-vm-builder kvm intrepid \
    --arch 'amd64' \
    --mem '256' \
    --rootsize '4096' \
    --swapsize '1024' \
    --kernel-flavour 'server' \
    --hostname 'vm1' \
    --domain 'local' \
    --mirror 'http://archive.ubuntu.com/ubuntu' \
    --components 'main' \
    --name 'Robin Harvey' \
    --user 'robin' \
    --pass 'yeahright' \
    --mac '54:52:00:08:DC:C6' \
    --bridge 'br0' \
    --libvirt 'qemu:///system' \
    --addpkg 'openssh-server'

```
...The VM starts fine in virsh..
```

virsh # list
 Id Name                 State
----------------------------------
  3 vm1                  running

```
...When the VM is started I can see the new interface for it...
```

robin@robin-desktop:~$ ifconfig 
br0       Link encap:Ethernet  HWaddr 9a:3b:e4:6c:60:0b  
          inet addr:192.168.1.15  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e2cb:4eff:febb:9907/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:424181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:248552 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:598319290 (598.3 MB)  TX bytes:18229027 (18.2 MB)

eth0      Link encap:Ethernet  HWaddr e0:cb:4e:bb:99:07  
          inet6 addr: fe80::e2cb:4eff:febb:9907/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:424172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:248703 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:604262076 (604.2 MB)  TX bytes:18238897 (18.2 MB)
          Interrupt:36 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2143 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2143 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:282608 (282.6 KB)  TX bytes:282608 (282.6 KB)

virbr0    Link encap:Ethernet  HWaddr 96:f8:91:64:d4:fc  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:5931 (5.9 KB)

vnet0     Link encap:Ethernet  HWaddr 9a:3b:e4:6c:60:0b  
          inet6 addr: fe80::983b:e4ff:fe6c:600b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54 errors:0 dropped:0 overruns:0 frame:0
          TX packets:136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:3308 (3.3 KB)  TX bytes:11608 (11.6 KB)

```

When I try to SSH in the NS lookup fails, for 'ssh vm1' it fails fast and for 'ssh vm1.local' it fails after a few seconds.  I notice that the vnet0 interface has no IP address and the MAC address is different to that specified in the ubuntu-vm-builder command.  The file at /etc/libvirt/qemu/vm1.xml *does* have the correct MAC address.

I'm on Karmic, can anyone spot any mistakes?

MTIA,
--Robin

---

### Post by robinharvey on 2010-02-14
Some more info, I think the problem here is that the DNS changes don't seem to have kicked in, I can SSH to the IP address of the VM just not the name.  Maybe I've got the name wrong, "vm1.local" is just a guess really?!  The output from netstat -an would suggest that the virbr0 interface is running some kind of DHCP service:
```

robin@robin-desktop:~$ netstat -an | grep -v unix
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 192.168.122.1:53        0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
...ETC...

```
Since my last post I've removed (via aptitude purge) NetworkManager and switched my bridge interface in to STP=YES mode, are either of these likely to have had an influence on matters?

Thanks,
--Robin

---

### Post by robinharvey on 2010-02-14
It gets weirder...

I've noticed that my VPN client (the proprietary Cisco one) doesn't like the bridged networking stuff much, so once I seemed have the KVM VM up and running I tried connecting to the VPN.  This worked, and while I was hooked up to the VPN I could still get to the VPN on it's IP - great.  However, when I disconnected the VPN my network went down - I could still see the interfaces in ifconfig, but stopping and starting the network from init scripts and from ifup/ifdown didn't help.

So, I rebooted my computer, and now that it's back up 2 things happened:

1) The br0 and eth0 interfaces did not come up at boot time.  I could start these manually so why didn't they come up at boot?

2) Virsh now refuses to load my VPN, it's dies with the following message:
```

robin@robin-desktop:~$ sudo virsh -c qemu:///system
Connecting to uri: qemu:///system
Welcome to virsh, the virtualisation interactive terminal.

Type:  'help' for help with commands
       'quit' to quit

virsh # connect /etc/libvirt/qemu/vm1.xml
error: Failed to connect to the hypervisor
error: no hypervisor driver available for /etc/libvirt/qemu/vm1.xml

virsh #

```

????   Any ideas?

Thanks,
--Robin

---

