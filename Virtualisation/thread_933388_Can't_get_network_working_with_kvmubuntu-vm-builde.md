---
title: "Can't get network working with kvm/ubuntu-vm-builder"
date: 2008-09-29
forum: Virtualisation
---

### Post by epicac on 2008-09-29
Hi there!

Trying to follow this guide
[https://help.ubuntu.com/community/KVM]("https://help.ubuntu.com/community/KVM")
but I can't get the default networking to work. My /etc/network/interfaces looks as follows:

auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address 192.168.0.30
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.0.6
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

When i restart the network with
sudo /etc/init.d/networking restart i get:
"Waiting for br0 to get ready (MAXWAIT is 20 seconds)." I don't know if that's the cause of the problems.

I use this command to create a vm:
sudo ubuntu-vm-builder kvm hardy --verbose --domain 'localhost' --arch 'amd64'  --mem '128'  --rootsize '4096'  --swapsize '1024'  --kernel-flavour 'generic'  --hostname 'roger'  --mirror 'http://archive.ubuntu.com/ubuntu'  --components 'main'  --addpkg 'vim openssh-server'  --name 'roger'  --user 'roger'  --pass 'roger' --libvirt 'qemu:///system' ;

I can start it in virsh and see that it's running in virsh, but I can't ping or connect with ssh. I guess the address of the virtual server should default to 192.168.122.2

The domainfile roger.xml looks as follows:
<domain type='kvm'>
  <name>roger</name>
  <uuid>a226fca6-bf32-5a61-08ea-568619113637</uuid>
  <memory>131072</memory>
  <currentMemory>131072</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type>hvm</type>
    <boot dev='hd'/>
  </os>
  <clock offset='utc'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
  <devices>
    <emulator>/usr/bin/kvm</emulator>
    <disk type='file' device='disk'>
      <source file='/home/omnitor/ubuntu-vm-hardy-amd64/root.qcow2'/>
      <target dev='hda' bus='ide'/>
    </disk>
    <interface type='network'>
      <mac address='52:54:00:89:ba:bb'/>
      <source network='default'/>
    </interface>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' listen='127.0.0.1'/>
  </devices>
</domain>


Hope you can help me.
/Christer

---

### Post by cleentrax on 2008-10-10
I'm having a similar problem. My VM can see the network, but the network can't see the VM.

---

### Post by Yann2 on 2008-10-11
Looking at your XML file you are trying to use NAT, but it seems what you want is bridging. Have a look at [https://help.ubuntu.com/community/KVM#Converting%20an%20existing%20guest](https://help.ubuntu.com/community/KVM#Converting%20an%20existing%20guest)  ; change the network definition in the /etc/libvirt/.. XML file, run "sudo virsh 
> define /etc/libvirt/qemu/yourvm.xml" 

And restart the VM.

---

### Post by ktulu73 on 2008-10-15
> **epicac said:**
> 

I can start it in virsh and see that it's running in virsh, but I can't ping or connect with ssh. I guess the address of the virtual server should default to 192.168.122.2


No, the address is not automaticly .2

But you can grep for the address of your guest system in your daemon.log:
```
cat /var/log/daemon.log |grep 192.168.122
```
or
```
cat /var/log/daemon.log |grep roger
```

---

