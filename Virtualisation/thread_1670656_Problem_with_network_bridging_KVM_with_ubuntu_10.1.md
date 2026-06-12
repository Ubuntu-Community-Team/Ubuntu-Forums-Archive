---
title: "Problem with network bridging KVM with ubuntu 10.10 host and fedora 8 client"
date: 2011-01-19
forum: Virtualisation
---

### Post by Bradderz on 2011-01-19
I've read many guides, forum posts and wikis over the last few days  but I've hit a brick wall on this so hoping someone may be able to shed some light on my problem!! Basically I'm running Ubuntu 10.10 as the host OS running KVM and trying to setup full network bridging on a second NIC to my fedora 8 client.

I'll try best to describe my config, I've followed the guide in [https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking) (and others!) for setting up the host. My xml config file under /etc/libvirt/qemu contains the following setup:


    <interface type='bridge'>
      <mac address='52:54:00:34:16:04'/>
      <source bridge='br1'/>
      <model type='ne2k_pci'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>


My interfaces file contains the following:


# The primary network interface
auto eth0
iface eth0 inet dhcp
        metric 0
###############################

auto eth1
iface eth1 inet manual

auto br1
iface br1 inet static
        address 135.86.195.46
        network 135.86.195.0
        netmask 255.255.255.192
        broadcast 135.86.195.63
        gateway 135.86.195.62
        bridge_ports eth1
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0
        metric 1
###############################


And if I do an ifconfig I get the following:


br1       Link encap:Ethernet  HWaddr 20:cf:30:06:88:ce
          inet addr:135.86.195.46  Bcast:135.86.195.63  Mask:255.255.255.192
          inet6 addr: fe80::22cf:30ff:fe06:88ce/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:297 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:130499 (130.4 KB)  TX bytes:45527 (45.5 KB)

eth0      Link encap:Ethernet  HWaddr 20:cf:30:06:88:9f
          inet addr:135.86.202.239  Bcast:135.86.202.255  Mask:255.255.255.0
          inet6 addr: fe80::22cf:30ff:fe06:889f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30827 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37771 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2754270 (2.7 MB)  TX bytes:36262176 (36.2 MB)
          Interrupt:18 Memory:fbce0000-fbd00000


eth1      Link encap:Ethernet  HWaddr 20:cf:30:06:88:ce
          inet6 addr: fe80::22cf:30ff:fe06:88ce/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4951 errors:0 dropped:0 overruns:0 frame:0
          TX packets:537 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:415200 (415.2 KB)  TX bytes:77633 (77.6 KB)
          Interrupt:19 Memory:fbde0000-fbe00000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:136386 errors:0 dropped:0 overruns:0 frame:0
          TX packets:136386 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:201037363 (201.0 MB)  TX bytes:201037363 (201.0 MB)

virbr0    Link encap:Ethernet  HWaddr fe:0a:d1:f7:b8:b4
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::fc0a:d1ff:fef7:b8b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:113 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:14062 (14.0 KB)

vnet0     Link encap:Ethernet  HWaddr fe:54:00:34:16:04
          inet6 addr: fe80::fc54:ff:fe34:1604/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2075 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:528 (528.0 B)  TX bytes:173114 (173.1 KB)


So this does all appear to look good!!

The problem is (before booting up the VM machine), if I attempt an ssh connection from another machine on the network to 135.86.195.46 (the static IP address of the VM), I get a connection to the host, is this right?

If I then start up my guest, with static ip setting for eth0 using the 135.86.195.46 address, I get an error saying that the ip address is already in use, which I guess is correct as the host seems to be hogging it but I just can't see what I'm doing wrong here.

I'm hoping someone can push me in the right direction, thanks!!

---

### Post by Bradderz on 2011-01-21
UPDATE:

Right, I appear to have got things working, by doing things with DHCP rather than static addresses. I'm working with a very limited address pool so had to assign specific IP addresses to the hardware MAC address on the dhcp server.

The way I've got this to work is assign 1 IP address to the br1 adaptor on the host and 1 IP address to the virtual MAC address assigned to the guest OS. Everything works fine!! Now logically this makes sense but I'm completely new to this VM stuff and I was under the impression that the host bridge didn't actually take its own IP address, is this right?? 

Have I implemented full bridging correctly as I need as little an overhead on network performance in this setup as possible?

Any comments would be greatly appreciated :D

---

### Post by gtoff on 2011-01-26
Hi,

I'd like to know how exactly did you manage to get it working with DHCP.

I'm trying to do the same thing with static addresses and a software bridge (for the moment I'm just trying to get VMs to talk to each other through a bridge, I'll get to the internet later on).
It seems on ubuntu 10.10 I cannot even get a software bridge to work correctly, or software bridge is simply not working. 
It seems odd nobody noticed this, so I must be definitely doing something wrong.

Here's how I do it:

1. create sw bridge
sudo brctl addbr extbr0

2. start VM ttylinux on bridge
sudo virsh create ttylinux.xml

Here's the XML:<domain type='kvm'>
  <name>ttylinux</name>
  <uuid>41886810-27b4-11e0-91fa-0800200c9a66</uuid>
  <memory>501576k</memory>
  <vcpu>1</vcpu>
  <os>
    <type arch="x86_64">hvm</type>
  </os>
  <clock sync="localtime"/>
  <devices>
    <emulator>/usr/bin/qemu-system-x86_64</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw'/>
      <source file='/home/tof/apps/virtual-machines/ttylinux.img'/>
      <target dev='hda'/>
    </disk>
    <interface type='bridge'>
      <source bridge='extbr0'/>
      <mac address='99:16:3e:5d:e7:b7'/>
      <target dev="ttylinux"/>
    </interface>

     <graphics type='vnc' port='-1' keymap='it'/>
  </devices>
</domain>

3. check that the VM is up and connected to bridge
sudo brctl show
bridge name    bridge id        STP enabled    interfaces
extbr0        8000.fe163e5de7b7    no        ttylinux

4. start other VM ttylinux2
sudo virsh create ttylinux2.xml

Here's the ttylinux2.xml

<domain type='kvm'>
  <name>ttylinux2</name>
  <uuid>3119f8b0-28a7-11e0-91fa-0800200c9a66</uuid>
  <memory>501576k</memory>
  <vcpu>1</vcpu>
  <os>
    <type arch="x86_64">hvm</type>
  </os>
  <clock sync="localtime"/>
  <devices>
    <emulator>/usr/bin/qemu-system-x86_64</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw'/>
      <source file='/home/tof/apps/virtual-machines/ttylinux.img'/>
      <target dev='hda'/>
    </disk>
    <interface type='bridge'>
      <source bridge='extbr0'/>
      <mac address='77:16:3e:5d:a7:a7'/>
      <target dev="ttylinux2"/>
    </interface>

     <graphics type='vnc' port='-1' keymap='it'/>
  </devices>
</domain>

5. check it's up and connected to extbr0
bridge name    bridge id        STP enabled    interfaces
extbr0        8000.fe163e5da7a7    no        ttylinux
                                             ttylinux2

If I now login to the VMs (through vncviewer) I can manually set IPs (this ttylinux has no dhcp client)
I use 192.168.0.1 for ttylinux and 192.168.0.2 for ttylinux2.

There is no way the two VMs ping each other, no ARP messages going through, no way they get the MAC address of the other VM.
I have no firewall rules or anything else that could get in the way:

sudo iptables -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


AFAIK the same thing works like a charm in Debian Lenny.

What am I doing wrong?

Thanks in advance for any help.

---

