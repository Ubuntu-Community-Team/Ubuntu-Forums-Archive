---
title: "virt-install stops when connected to domain"
date: 2011-03-16
forum: Server Platforms
---

### Post by KarelV on 2011-03-16
I have succesfully installed Ubuntu 10.10 server and want to install a virtual machine with the same OS. 

For installation purpose, I mounted a cdrom drive, keyboard and monitor.
On my attempt to do the installation, I get the following sequence:
```
sudo virt-install \
>               --connect qemu:///system \
>               --name sweb \
>               --ram 512 \
>               --disk path=/var/lib/libvirt/images/sweb.img,size=20 \
>               --network bridge=br1 \
>               --cdrom /dev/cdrom
[sudo] password for karelv:


Starting install...
Creating domain...                                                 0 B 00:03
Connected to domain sweb
Escape character is ^]

```At the end of this sequence I hear the cdrom drive spins up, so the domain must be booting from the cdrom. However, there is no further response on the console. 

Upon entering the escape character I get:
```
Domain installation still in progress. You can reconnect to
the console to complete the installation process.
```Hereafter, I can make a dump of the xml definition:
```

<domain type='kvm' id='4'>
  <name>sweb</name>
  <uuid>5a1f2b3d-6b7a-4507-6713-5499c85276d0</uuid>
  <memory>524288</memory>
  <currentMemory>524288</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc-0.12'>hvm</type>
    <boot dev='cdrom'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <pae/>
  </features>
  <clock offset='utc'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>destroy</on_reboot>
  <on_crash>destroy</on_crash>
  <devices>
    <emulator>/usr/bin/kvm</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw'/>
      <source file='/var/lib/libvirt/images/sweb.img'/>
      <target dev='hda' bus='ide'/>
      <alias name='ide0-0-0'/>
      <address type='drive' controller='0' bus='0' unit='0'/>
    </disk>
    <disk type='block' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <source dev='/dev/cdrom'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
      <alias name='ide0-1-0'/>
      <address type='drive' controller='0' bus='1' unit='0'/>
    </disk>
    <controller type='ide' index='0'>
      <alias name='ide0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <interface type='bridge'>
      <mac address='52:54:00:fc:4c:b7'/>
      <source bridge='br1'/>
      <target dev='vnet0'/>
      <alias name='net0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </interface>
    <serial type='pty'>
      <source path='/dev/pts/1'/>
      <target port='0'/>
      <alias name='serial0'/>
    </serial>
    <console type='pty' tty='/dev/pts/1'>
      <source path='/dev/pts/1'/>
      <target type='serial' port='0'/>
      <alias name='serial0'/>
    </console>
    <memballoon model='virtio'>
      <alias name='balloon0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </memballoon>
  </devices>
  <seclabel type='dynamic' model='apparmor'>
    <label>libvirt-5a1f2b3d-6b7a-4507-6713-5499c85276d0</label>
    <imagelabel>libvirt-5a1f2b3d-6b7a-4507-6713-5499c85276d0</imagelabel>
  </seclabel>
</domain>

```I have tried the procedure from the physical console as well as from remote (using Putty on a windows machine) in a SSH window.
I also tried to install from an iso file on disk in stead of the cdrom. All with the same result.

I hope someone can help me to get the install process going.

---

### Post by falko on 2011-03-16
You must connect to the VM using virt-manager or virt-viewer to complete the installation process (as shown on [http://www.howtoforge.com/virtualization-with-kvm-on-a-debian-squeeze-server-p2](http://www.howtoforge.com/virtualization-with-kvm-on-a-debian-squeeze-server-p2) ).

---

### Post by KarelV on 2011-03-17
Thanks for the link. 
For that purpose I had installed Ubuntu desktop on an old pentium pc. Although slow, I can use virt-manager. 
I followed the steps carefully, but end up with the message: Cannot open a connection to the libvirt management deamon.

I keep trying.

---

### Post by falko on 2011-03-17
You must enable the root account on the server...

```
sudo su
passwd root
```

... and then connect from virt-manager to the server as root.

---

### Post by KarelV on 2011-03-18
@ falko,
I have my VM running. Thanks for the advise to choose an alternative route to install a VM.

---

