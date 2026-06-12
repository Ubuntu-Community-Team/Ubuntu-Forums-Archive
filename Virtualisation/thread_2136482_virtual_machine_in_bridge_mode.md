---
title: "virtual machine in bridge mode"
date: 2013-04-17
forum: Virtualisation
---

### Post by alanc_yang on 2013-04-17
I created two KVM virtual machines VM1 and VM2 in bridge mode.  The brctl and ifconfig info in the following shows the br0 and vnet0/1 interfaces.
But only vm2 respond to arp request but not vm1.  
Any specific configuration for multiple virtual machines in bridge mode to work?  

Thanks in advance.

---

br0       Link encap:Ethernet  HWaddr e0:db:55:93:76:40  
          inet addr:192.168.1.19  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e2db:55ff:fe93:7640/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:858634 errors:0 dropped:0 overruns:0 frame:0
          TX packets:384880 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1197115849 (1.1 GB)  TX bytes:33889357 (33.8 MB)


eth0      Link encap:Ethernet  HWaddr e0:db:55:93:76:40  
          inet6 addr: fe80::e2db:55ff:fe93:7640/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:866131 errors:0 dropped:0 overruns:0 frame:0
          TX packets:384844 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1212256988 (1.2 GB)  TX bytes:33965755 (33.9 MB)
          Interrupt:41 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10165 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1131178 (1.1 MB)  TX bytes:1131178 (1.1 MB)


vnet0     Link encap:Ethernet  HWaddr fe:54:00:76:a7:2c  
          inet6 addr: fe80::fc54:ff:fe76:a72c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:1 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


vnet1     Link encap:Ethernet  HWaddr fe:54:00:9b:a1:97  
          inet6 addr: fe80::fc54:ff:fe9b:a197/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2040 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11642 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:172564 (172.5 KB)  TX bytes:3927012 (3.9 MB)

# brctl
bridge name	bridge id		STP enabled	interfaces
br-ex		0000.ca8db2a4c34a	no		qg-4437477c-a9
br-int		0000.be86bc44a140	no		qr-e7d98d75-8c
						        	tap1281d678-fd
br0		8000.e0db55937640	no		eth0
                 						vnet0
		         					vnet1

---

### Post by alanc_yang on 2013-04-18
Not sure why it is working now: both vm1 and vm2 has internal and internet access.  
I destroyed vm1 and re-generate vm1 KVM image with vmbuilder.  Bridge configuration configured earlier has not changed.    
(earlier problem with wireshark seems to indicate vm1 was not responding to arp request)

List related file for your reference.

_vm1.xmlcon_

<!--
WARNING: THIS IS AN AUTO-GENERATED FILE. CHANGES TO IT ARE LIKELY TO BE 
OVERWRITTEN AND LOST. Changes to this xml configuration should be made using:
  virsh edit vm1
or other application using the libvirt API.
-->


<domain type='kvm'>
  <name>vm1</name>
  <uuid>320eecab-16e7-2200-3f77-db0c310051cc</uuid>
  <memory>262144</memory>
  <currentMemory>262144</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc-1.0'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
  </features>
  <clock offset='utc'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
  <devices>
    <emulator>/usr/bin/kvm</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/var/lib/libvirt/images/vm1/ubuntu-kvm/tmpDVqBFa.qcow2'/>
      <target dev='hda' bus='ide'/>
      <address type='drive' controller='0' bus='0' unit='0'/>
    </disk>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/var/lib/libvirt/images/vm1/ubuntu-kvm/tmpuLxnlq.qcow2'/>
      <target dev='hdb' bus='ide'/>
      <address type='drive' controller='0' bus='0' unit='1'/>
    </disk>
    <controller type='ide' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <interface type='bridge'>
      <mac address='52:54:00:05:71:b0'/>
      <source bridge='br0'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes' listen='127.0.0.1'>
      <listen type='address' address='127.0.0.1'/>
    </graphics>
    <video>
      <model type='cirrus' vram='9216' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </memballoon>
  </devices>
</domain>

_vmbuilder_

vmbuilder kvm ubuntu --suite=precise --flavour=virtual --arch=amd64 --mirror=http://de.archive.ubuntu.com/ubuntu -o --libvirt=qemu:///system --ip=192.168.1.101 --gw=192.168.1.254 --dns=192.168.1.254 --part=vmbuilder.partition --templates=mytemplates --user=user --pass=vm123 --addpkg=vim-nox --addpkg=unattended-upgrades --addpkg=acpid --addpkg=openssh-server --addpkg=avahi-daemon --firstboot=/var/lib/libvirt/images/vm1/boot.sh --mem=256 --hostname=vm1 --bridge=br0

---

### Post by HermanAB on 2013-04-19
In the earlier setup, only one machine had an IP address and netmask.  Always check the basics, before you try something complicated that sits on top!

---

