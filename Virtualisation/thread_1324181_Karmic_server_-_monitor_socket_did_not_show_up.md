---
title: "Karmic server - monitor socket did not show up"
date: 2009-11-12
forum: Virtualisation
---

### Post by sakubas on 2009-11-12
Hi, im using kvm in ubuntu 9.10.
i folow the guide [https://help.ubuntu.com/community/JeOSVMBuilder](https://help.ubuntu.com/community/JeOSVMBuilder) and the thread   [[all variants] kvm not able to connect to guest?]("http://ubuntuforums.org/showthread.php?t=1027550")  but does not work.

This is what I used to create the guest:

```


#libvirtxml.tmpl

<domain type='kvm'>
  <name>$hostname</name>
  <memory>#echo int($mem) * 1024 #</memory>
  <vcpu>$cpus</vcpu>
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
#if $mac
      <mac address='$mac'/>
#end if
#if $virtio_net
      <model type='virtio'/>
#end if
    </interface>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='5900' listen='192.168.10.180'/>
#for $disk in $disks
    <disk type='file' device='disk'>
      <source file='$disk.filename' />
      <target dev='hd$disk.devletters()' />
    </disk>
#end for
  </devices>
</domain>


```

```


#server.cfg

[DEFAULT]
arch = i386
ip = 192.168.10.180
part = vmbuilder.partition
user = user
name = user
pass = default
tmpfs = - 
firstboot = boot.sh
firstlogin = login.sh 
templates = ~/server/templates
[ubuntu]
mirror = http://ubuntu.unlp.edu.ar/ubuntu
suite = intrepid 
flavour = virtual
addpkg = unattended-upgrades, acpid
ppa = nijaba 

[kvm]
libvirt = qemu:///system 


```


I create a vm using ```
vmbuilder kvm ubuntu -c server.cfg
```

At the end of the creation process i run: ```
#virsh start ubuntu
Connecting to uri: qemu:///system
error: monitor socket did not show up.: Connection refused
```

Log file shows:

```


LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin /usr/bin/kvm -S -M pc-0.11 -m 128 -smp 1 -name ubuntu -uuid 1068653f-5ff3-1486-8cb4-e6e3553dbb3a -monitor unix:/var/run/libvirt/qemu/ubuntu.monitor,server,nowait -boot c -drive file=/home/useradmin/server/ubuntu-kvm/disk0.qcow2,if=ide,index=0,boot=on -net nic,macaddr=52:54:00:08:43:a5,vlan=0,model=virtio,name=virtio.0 -net tap,fd=17,vlan=0,name=tap.0 -serial none -parallel none -usb -vnc 192.168.10.180:0 -vga cirrus 
inet_listen: bind(ipv4,192.168.10.180,5900): Cannot assign requested address
inet_listen: FAILED


```

Any help would be really (REALLY) appreciated. :-)

(sorry my english is horrible - :))


Thanks everyone...

---

