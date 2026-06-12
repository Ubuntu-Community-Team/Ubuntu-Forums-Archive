---
title: "KVM Ubuntu Guest Not Seeing Network"
date: 2009-03-04
forum: Virtualisation
---

### Post by gushy on 2009-03-04
I've got a new install of Ubuntu Server 8.10 with KVM.  I've followed the instructions in the guide/docs and the instructions on the wiki and howtoforge; however I still cannot get a jeos guest (I've not tried other OSes) to see the network in bridged mode. And nothing on the network can connect to the VM.

I'm sure it's typo in a config file or install, but I can't figure it out and it's annoying me.  

Help!.

Relevant config files, outputs etc below.

/etc/network/interfaces```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet manual

# Bridiging Network Interface
auto br0
iface br0 inet static
	address 192.168.1.18
	network 192.168.1.0
	netmask 255.255.255.0
	broadcast 192.168.1.255
	gateway 192.168.1.254
	bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off
```

ifconfig```
br0       Link encap:Ethernet  HWaddr 00:01:29:a3:ef:44  
          inet addr:192.168.1.18  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:29ff:fea3:ef44/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7707 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6473 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:823229 (823.2 KB)  TX bytes:2556992 (2.5 MB)

eth0      Link encap:Ethernet  HWaddr 00:01:29:a3:ef:44  
          inet6 addr: fe80::201:29ff:fea3:ef44/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:149271 errors:0 dropped:9 overruns:0 frame:0
          TX packets:102509 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24652459 (24.6 MB)  TX bytes:23837418 (23.8 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:45694 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45694 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:383151180 (383.1 MB)  TX bytes:383151180 (383.1 MB)

vnet0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::9498:80ff:febe:b800/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:657 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30330 (30.3 KB)  TX bytes:468 (468.0 B)
```

~/VMBuilder/plugins/libvirt/templates/libvirtxml.tmpl```
<domain type='kvm'>
  <name>$hostname</name>
  <memory>#echo $mem * 1024 #</memory>
  <vcpu>1</vcpu>
  <os>
    <type>hvm</type>
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
    <interface type='bridge'>
      <source bridge='br0'/>
    </interface>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' listen='127.0.0.1'/>
#for $disk in $disks
    <disk type='file' device='disk'>
      <source file='$disk.filename' />
      <target dev='hd$disk.devletters()' />
    </disk>
#end for
  </devices>
</domain>
```

VM install script```
#!/bin/bash
sudo vmbuilder kvm ubuntu --suite intrepid --flavour virtual --arch i386 -o --libvirt qemu:///system --ip 192.168.1.250 --gw 192.168.1.254 --dns 192.168.1.21 --part vmbuilder.partition --user administrator --name Administrator --pass changeme --addpkg unattended-upgrades --addpkg acpid --addpkg vim-nox --mirror http://192.168.1.18:9999/ubuntu --tmpfs - --firstboot boot.sh --firstlogin login.sh --mem 256 --hostname $1 --dest machines/$1-vm
```

---

### Post by gushy on 2009-03-04
ok so I fixed it but I can't figure out the cause of the problem.

It seems when I created a test1 vm, the test1.xml created in /etc/libvirt/qemu had the default network settings.  So it seems that even though I ran my install script from within ~/VMBuilder it ignored ~/VMBuilder/plugins/libvirt/templates/libvirtxml.tmpl.

Anyone know why?

---

### Post by gushy on 2009-03-04
Apparentely I should try harder before posting.  Seems I was running the create command from ~/VMBuilder when I should have been running it from ~

---

