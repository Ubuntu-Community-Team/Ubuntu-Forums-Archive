---
title: "virtio disks not working in Trusty"
date: 2014-05-03
forum: Virtualisation
---

### Post by loyhz2ayj-jeff on 2014-05-03
On Precise I have the disks on my virtual machines set up like this:



    ```
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw'/>
      <source dev='/dev/harrier/heron_a'/>
      <target dev='vda' bus='virtio'/>
      <alias name='virtio-disk0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </disk>
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw'/>
      <source dev='/dev/harrier/heron_b'/>
      <target dev='vdb' bus='virtio'/>
      <alias name='virtio-disk1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </disk>
```

Where /dev/harrier/heron_a, et al are logical volumes.

This does not work on Trusty.  Any idea why?

---

### Post by Doug S on 2014-05-04
For my VM's, originally created in 12.04 precise, I had to change the machine type for them to work in 14.04 trusty. I had to change this:```
  <os>
    <type arch='x86_64' machine='pc-1.0'>hvm</type>
    <boot dev='hd'/>
  </os>
```to this:```
  <os>
    <type arch='x86_64' machine='pc-i440fx-1.7'>hvm</type>
    <boot dev='hd'/>
  </os>
```This is a long shot suggestion for you as my issues were with video (and did get documented in [the trusty release notes]("https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes")).

---

### Post by loyhz2ayj-jeff on 2014-05-06
I created new virtual machines in Trusty using vmbuilder, so the machine type is as you suggest.  They work fine (and fstrim actually works inside a vm inside LVM!) but, if I switch to the virtio disk driver it won't boot.

---

### Post by Doug S on 2014-05-06
All I can say is that virtio has been working for me. None of my current VM's use a complete volume, so I made a test one just now, and it seems to be fine. Here is the disk section of the .xml file:```
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw'/>
      <source dev='/dev/sdc1'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </disk>
```The only thing I do not have is your alias line. Also, I do not know how to have a device name similar to what you have.
Just for completeness, I created this VM (using an ISO I had lying around) with this command line:```
sudo virt-install -n v_desk07 -r 8192 --disk path=/dev/sdc1,bus=virtio -c trusty-desktop-amd64-20140417.iso --network bridge=br0,model=virtio --video=vmvga --graphics vnc,listen=0.0.0.0 --noautoconsole -v --vcpus=4
```

Edit: By the way, use and mention of "vmbuilder" has been removed from [the 14.04 Serverguide]("https://help.ubuntu.com/14.04/serverguide/virtualization.html") , which might indicate it wasn't tested much with QEMU 2.

---

### Post by loyhz2ayj-jeff on 2014-05-06
Thanks.   Yeah vmbuilder had a few problems but they were easily patched around.   I will give your virt-install thing a try and if it works I should be able to transplant the generated xml into my vmbuilder templates.

So in your example /dev/sdc1 is a physical disk on the host?  In mine [COLOR=#000000][FONT=Ubuntu Mono]/dev/harrier/heron_a is an LVM volume.


[/FONT][/COLOR]

---

### Post by Doug S on 2014-05-06
> **loyhz2ayj-jeff said:**
> So in your example /dev/sdc1 is a physical disk on the host?  In mine [COLOR=#000000][FONT=Ubuntu Mono]/dev/harrier/heron_a is an LVM volume.[/FONT][/COLOR]Yes, mine is a physical disk (SSD, actually) that I had lying around. If it comes to it, I can try to make it an LVM volume and try to install a VM again.

---

### Post by loyhz2ayj-jeff on 2014-05-16
Ok, well I've got it working.

First, I switched to using virt-install instead of vmbuilder.  Virt-install started with this script created a machine with virtio disks *but* fstrim did not work!```
virt-install \
        -n newt \
        -r 2048 \
        --disk path=/dev/egret-vg/newt,bus=virtio \
        -c /root/ubuntu-14.04-server-amd64.iso \
        --network bridge=br0,model=virtio \
        --video=vmvga  \
        --graphics vnc,listen=0.0.0.0 \
        --noautoconsole \
        -v \
        --vcpus=2
```
So just for a test I did it like this and got IDE disks and fstrim *did *work:```
virt-install \
        -n phoebe \
        -r 2048 \
        --disk path=/dev/egret-vg/phoebe,bus=ide \
        -c /root/ubuntu-14.04-server-amd64.iso \
        --network bridge=br0,model=virtio \
        --video=vmvga  \
        --graphics vnc,listen=0.0.0.0 \
        --noautoconsole \
        -v \
        --vcpus=2
```

So I think ***rats ***this isn't going to work.

Then I remember reading about virtio-scsi.. a paravirtualized scsi adapter.  It's documented at [http://www.ovirt.org/Features/Virtio-SCSI](http://www.ovirt.org/Features/Virtio-SCSI).  *and* it turns out it's in Ubuntu 14.  So I followed the directions and I now have a scsi disk with a paravirtualized scsi bus, and fstrim in the vm works.  

[SIZE=5]**Question: **Does anyone know why fstrim doesn't work with the normal virtio disks?
[/SIZE][SIZE=1][SIZE=3]
[SIZE=2]Here's the device section of my current vm definition.  Most of this virsh edit wrote for me:
[/SIZE][/SIZE][/SIZE]
  ```
<devices>
    <emulator>/usr/bin/kvm-spice</emulator>
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw'/>
      <source dev='/dev/egret-vg/newt'/>
      <target dev='sda' bus='scsi'/>
      <alias name='scsi0-0-0-0'/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <disk type='block' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
      <alias name='ide0-1-0'/>
      <address type='drive' controller='0' bus='1' target='0' unit='0'/>
    </disk>
    <controller type='usb' index='0'>
      <alias name='usb0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'>
      <alias name='pci.0'/>
    </controller>
    <controller type='ide' index='0'>
      <alias name='ide0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <controller type='scsi' index='0' model='virtio-scsi'>
      <alias name='scsi0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </controller>
    <interface type='bridge'>
      <mac address='52:54:00:e3:84:09'/>
      <source bridge='br0'/>
      <target dev='vnet0'/>
      <model type='virtio'/>
      <alias name='net0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
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
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='vnc' port='5900' autoport='yes' listen='0.0.0.0'>
      <listen type='address' address='0.0.0.0'/>
    </graphics>
    <video>
      <model type='vmvga' vram='9216' heads='1'/>
      <alias name='video0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <memballoon model='virtio'>
      <alias name='balloon0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </memballoon>
  </devices>
```

---

### Post by loyhz2ayj-jeff on 2014-05-16
I should also add that any performance testing remains to be done.

---

