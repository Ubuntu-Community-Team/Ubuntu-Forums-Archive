---
title: "ubuntu, libvirt and virtio block devices, oh my"
date: 2013-03-05
forum: Virtualisation
---

### Post by dreamgear on 2013-03-05
Hi. I'm running 12.04 LTS. I created some virtual machines using vmbuilder, and then migrated those from their .qcow files to lvm. However, those virtual machines are still using disk type "file":
```
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw'/>
      <source file='/dev/vg1/lvname'/>
      <target dev='hda' bus='ide'/>
      <alias name='ide0-0-0'/>
      <address type='drive' controller='0' bus='0' unit='0'/>
    </disk>
```

Now I've noticed that this disk should probably have type "block" - using this is supposed to provide superior performance.  It would also make Berteaud's virt-backup script happy and willing to snapshot the lvm making the backup very quick.  So I tried setting up the disk like this:

```
<disk type='block' device='disk'>
      <driver name='qemu' type='raw'/>
      <source dev='/dev/vg1/lvname'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </disk>
```

I had to edit fstab to look for the disk on vda instead of hda but it came up.  However performance was terrible.  It seemed like it was going to lock up, although it never did.

So my questions are:

1.  How should I be setting up my LVM-based virtual machines to use virtio block devices ?

and 

2.  Is there any way to get vmbuilder to do this for me?  The documentation refers to vmbuilder config files, but seems to have been thrice abandoned, leaving nothing to find.

---

### Post by dreamgear on 2013-03-08
So a followup question, I guess:  **Does anyone here who is using KVM on Ubuntu have a VM's disk set up with type='block' and target bus='virtio' ?**  It doesn't seem to work, and the folks over in the libvirt-user mailing list don't seem to have any idea of what I'm talking about.

---

### Post by dreamgear on 2013-04-10
So it's been a month.  Can  anyone suggest a support resource ?  At this point I'll even consider paying.  They're ignoring me real hard over on the libvirt list too.

---

### Post by Doug S on 2013-04-12
I do not know how to make your hard disk device type "block".
I do have virtio as the bus type on VM's I have craeted. I do not use vmbuilder, yet. I am only learning, and only got to the virt-install way so far.
I used:```
sudo virt-install -n virt64_01 -r 2048 --disk path=/var/lib/libvirt/images/virt64_01.img,[COLOR=#ff0000]bus=virtio[/COLOR],size=12 -c ubuntu-12.04.2-server-amd64.iso --network network=default,model=virtio --graphics vnc,listen=0.0.0.0 --noautoconsole -v --vcpus=4
```and ended up with:```
...
  <devices>
    <emulator>/usr/bin/kvm</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw'/>
      <source file='/var/lib/libvirt/images/virt64_01.img'/>
      <target dev='vda' [COLOR=#ff0000]bus='virtio'/[/COLOR]>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </disk>
    <disk type='block' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
      <address type='drive' controller='0' bus='1' unit='0'/>
    </disk>
...
```

---

### Post by Doug S on 2013-04-12
> **Doug S said:**
> I do not know how to make your hard disk device type "block".Well, ... maybe I do.
It seemed to me that in order to "block" a device, you would need the entire device, so I made a virtual computer and allocated an entire disk partition to it.
The command used was:```
sudo virt-install -n virt64_02 -r 2048 [COLOR=#ff0000]--disk path=/dev/sdb3,bus=virtio [/COLOR]-c ubuntu-12.04.2-server-amd64.iso --network network=default,model=virtio --graphics vnc,listen=0.0.0.0 --noautoconsole -v --vcpus=4
```and the related part of the resulting .xml file was:```
  <devices>
    <emulator>/usr/bin/kvm</emulator>
    <[COLOR=#ff0000]disk type='block' [/COLOR]device='disk'>
      <driver name='qemu' type='raw'/>
      <source [COLOR=#ff0000]dev='/dev/sdb3'/[/COLOR]>
      <target dev='vda' [COLOR=#ff0000]bus='virtio'/>[/COLOR]
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </disk>
    <disk type='block' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
      <address type='drive' controller='0' bus='1' unit='0'/>
    </disk>
```

---

### Post by dreamgear on 2013-05-02
So I went back to the block configuration.  The config now looks like this (below).

So everything works fine except for ssh sessions.  Occasionally I will get a very long period of unresponsiveness - sometimes as much as 30 seconds.  There is no underlying network problem, as I've seen this on 4 different servers on 4 different networks and only on those servers when using the "disk type = 'block'".  Further, during these periods of unresponsiveness a VNC session to a text-mode console on the guest in question responds normally.   Very puzzling.  More evidence that it's just SSH is from the fact that one of my guests is a Bacula backup director server, which communicates over TCP to start backup jobs and receive catalog data.  None of these connections has ever timed out since I switched to block mode.  Not even once, and there have been hundreds of jobs.

The host systems in each case are Xeon E3s with solid state disks, and are all very close to idle.



```
<domain type='kvm' id='4'>  <name>kiskadee</name>
  <uuid>9e6a569b-4333-a5f0-07cf-fbd4e93a4b4a</uuid>
  <memory>2097152</memory>
  <currentMemory>2097152</currentMemory>
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
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw'/>
      <source dev='/dev/harrier/kiskadee'/>
      <target dev='vda' bus='virtio'/>
      <alias name='virtio-disk0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </disk>
    <interface type='bridge'>
      <mac address='52:54:00:cd:93:8c'/>
      <source bridge='br0'/>
      <target dev='vnet0'/>
      <model type='virtio'/>
      <alias name='net0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='5900' autoport='yes' listen='0.0.0.0'>
      <listen type='address' address='0.0.0.0'/>
    </graphics>
    <video>
      <model type='cirrus' vram='9216' heads='1'/>
      <alias name='video0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <memballoon model='virtio'>
      <alias name='balloon0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </memballoon>
  </devices>
  <seclabel type='dynamic' model='apparmor' relabel='yes'>
    <label>libvirt-9e6a569b-4333-a5f0-07cf-fbd4e93a4b4a</label>
    <imagelabel>libvirt-9e6a569b-4333-a5f0-07cf-fbd4e93a4b4a</imagelabel>
  </seclabel>
</domain>
```

---

### Post by Doug S on 2013-05-03
I still have the virtual machine I made for my reply of a couple of weeks ago. I talk to it from a windows computer a SSH sesssion on top of a putty SSH session to the host.
I turned on logging on putty and ran the following command:```
netstat -tc
```To continuoulsy, once per second, list the tcp sessions. My thinking was that if there was some delay on ssh then it should show in the send queue. After 17 hours there was only ever a maximum of 160 bytes in the send Q, which I think means 2 lines of the previous seconds listing. Although two times those 160 byte queue sizes came in blocks, repeating in each second for many seconds.
Conclusion: I do not see any big SSH gap on mine.

---

