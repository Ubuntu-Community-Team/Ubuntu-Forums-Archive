---
title: "ubuntu 10.04; kvm bridged networking not working with public ip addresses"
date: 2011-01-10
forum: Virtualisation
---

### Post by senor_smile on 2011-01-10
I have a dedicated hosted server box with ubuntu 10.04 64 bit installed.  I would like to run kvm with ubuntu 8.04 installed for some php 5.2 compatible apps(they don't work right with php 5.3, the default in ubuntu 10.04).  

I installed KVM as instructed at [https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation) .  I installed the vm using virt-manager.  I never could figure out how use virt-install or any of those automated installers.  I just installed it using the disc.  I set up bridged networking as per [https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking) . However, the bridged connection doesn't work.  

Here's my /etc/network/interfaces on the host, running ubuntu 10.04.    (with specific public ip blanked)

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address xx.xx.xx.xx
        netmask 255.255.255.248
        gateway xx.xx.xx.xa
        bridge_ports eth0
        bridge_stp on
        bridge_fd 0
        bridge_maxwait 10
```


Here's my /etc/network/interfaces on the guest, running ubuntu 8.04.  

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address xx.xx.xx.xy
netmask 255.255.255.248
gateway xx.xx.xx.xa
```


The two vm's can communicate to each other.  But, the guest vm can't access anyone in the real world.  

Here's my /etc/libvirt/qemu/store_804.xml

```
<domain type='kvm'>
  <name>store_804</name>
  <uuid>27acfb75-4f90-a34c-9a0b-70a6927ae84c</uuid>
  <memory>2097152</memory>
  <currentMemory>2097152</currentMemory>
  <vcpu>2</vcpu>
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
      <source file='/var/lib/libvirt/images/store_804.img'/>
      <target dev='hda' bus='ide'/>
    </disk>
    <disk type='block' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
    </disk>
    <interface type='bridge'>
      <mac address='52:54:00:26:0b:c6'/>
      <source bridge='br0'/>
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
    <sound model='es1370'/>
    <video>
      <model type='cirrus' vram='9216' heads='1'/>
    </video>
  </devices>
</domain>
```


Any idea where I've gone wrong?

---

### Post by binaryhat on 2011-01-30
Did you get it to work?

---

### Post by senor_smile on 2011-01-31
> **binaryhat said:**
> Did you get it to work?

No, I didn't.  It's still sitting there not working.  I haven't found any information on how to fix it.  Anyone have any ideas?

---

### Post by binaryhat on 2011-01-31
Try these steps:  [http://wiki.libvirt.org/page/Networking#Debian.2FUbuntu_Bridging](http://wiki.libvirt.org/page/Networking#Debian.2FUbuntu_Bridging)

Skip the part on Disabling NetworkManager.

I think the key step is : 

Finally add the '/etc/sysctl.conf' settings 
 net.bridge.bridge-nf-call-ip6tables = 0
net.bridge.bridge-nf-call-iptables = 0
net.bridge.bridge-nf-call-arptables = 0
And then load the settings with 
  sysctl -p /etc/sysctl.conf

Thats what fixed it for me.

The docs provided by Ubuntu do not work, they are dated.

---

### Post by binaryhat on 2011-02-02
Any luck?

---

### Post by shulegaa on 2011-02-08
Without better bridged networking (config) documentation (with examples), KVM sure seems DOA for me.  Bummer ... 

I was just trying to consolidate physical servers into a bunch of VM's with static (bridged) IPs.  It looks like more than a few folks are not getting very far with KVM.

---

### Post by tomgibson on 2011-03-03
I have managed to get a setup working on Ubuntu 10.04 with kvm guests and bridged networking albeit on a LAN with DHCP (not static public IPs), though I don't understand how as I certainly didn't follow all the instructions on the wiki.

Two things I notice about your config files that differ from mine:

1) In your /etc/network/interfaces you have an entry for eth0 and br0. I only have br0 in mine, now I'm not an expert in how this file works so you may have the eth0 entry for good reason, but as far as I know only the br0 entry is required.

2) In your vm .xml you specify the guest network interface using the lines

```
    <interface type='bridge'>
      <mac address='52:54:00:26:0b:c6'/>
      <source bridge='br0'/>
      <model type='virtio'/>
    </interface>
```Try removing the <model /> line, I do not think this is necessary for bridged interfaces.

Not promising this will solve your problem, just a couple of things I noticed that differ from my own configs.

Only other thing I can suggest is perhaps your host firewall is interfering. The qemu faq has instructions on how to make this not happen:

[http://qemu-buch.de/cgi-bin/moin.cgi/FrequentlyAskedQuestions#head-c0035a813d6eda29ba3e1d4e27fe430c118b8b60](http://qemu-buch.de/cgi-bin/moin.cgi/FrequentlyAskedQuestions#head-c0035a813d6eda29ba3e1d4e27fe430c118b8b60)

Hope that helps.

---

### Post by TheR on 2011-03-06
It looks more like a gateway problem. 

You have a strange (very narrow) gateway mask. Is it the same as computers on the outside world?

Is gateway address same as gateway address of outside computers?

by
TheR

---

