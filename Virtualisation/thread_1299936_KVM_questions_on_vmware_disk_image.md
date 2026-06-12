---
title: "KVM questions on vmware disk image"
date: 2009-10-24
forum: Virtualisation
---

### Post by sdowney717 on 2009-10-24
does KVM support usb?
i tried using a vmware disk image but am getting boot errors as you can see
i followed this guide here
[https://help.ubuntu.com/community/KVM/FAQ](https://help.ubuntu.com/community/KVM/FAQ)

so what am i doing wrong?
contents of the xml file

> <domain type='kvm'>
  <name>minixp</name>
  <uuid>5798fae9-f6a2-4bd3-bf24-98b117c269ed</uuid>
  <memory>524288</memory>
  <currentMemory>524288</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type arch='i686' machine='pc-0.11'>hvm</type>
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
      <source file='/home/scott/vm/ixp/ixp.vmdk'/>
      <target dev='hda' bus='ide'/>
    </disk>
    <interface type='network'>
      <mac address='00:0c:29:5f:94:56'/>
      <source network='default'/>
    </interface>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes' listen='127.0.0.1'/>
    <video>
      <model type='cirrus' vram='9216' heads='1'/>
    </video>
  </devices>
</domain>

---

### Post by sdowney717 on 2009-10-24
[http://tombuntu.com/index.php/2008/04/14/virtualization-with-virt-manager-and-kvm-in-ubuntu-804/](http://tombuntu.com/index.php/2008/04/14/virtualization-with-virt-manager-and-kvm-in-ubuntu-804/)

i did find this graphical virt manager
however i wonder if it supports usb dongles. there is mention of usb hard drives.

---

### Post by sdowney717 on 2009-10-24
[http://inspirated.com/2009/03/15/howto-use-usb-devices-in-virtual-machine-manager-with-qemu](http://inspirated.com/2009/03/15/howto-use-usb-devices-in-virtual-machine-manager-with-qemu)

trying this for adding usb devices. They still do not show up in the quest os. windows xp with sp2

any ideas?

---

### Post by sdowney717 on 2009-10-24
[http://www.linux-kvm.com/content/improved-support-usb-virt-manager-07](http://www.linux-kvm.com/content/improved-support-usb-virt-manager-07)

this should work with 0.7.0 so I am going to try another OS source
kvm needs an iso of a cdrom or dvd to install an os
to convert a cdrom image to an iso file do this
[http://www.cyberciti.biz/tips/linux-creating-cd-rom-iso-image.html](http://www.cyberciti.biz/tips/linux-creating-cd-rom-iso-image.html)
my device is sr0. make sure not mounted 
scott@scott-desktop:~$ umount dev/sr0
umount: dev/sr0 is not mounted (according to mtab)

this makes the iso in /tmp
scott@scott-desktop:~$ dd if=/dev/sr0 of=/tmp/cdimg1.iso
5991368+0 records in
5991368+0 records out
3067580416 bytes (3.1 GB) copied, 232.362 s, 13.2 MB/s


to stop kvm modules from loading and interfering with vmware
vmware just will not run with these loaded.
these steps to temporarily unload the KVM module 


sudo /etc/init.d/libvirt-bin stop

less /proc/modules and search for kvm... I have an Intel chip so I had two hits: kvm-intel and kvm .. next, simply remove them in order:


sudo modprobe -r kvm_intel
sudo modprobe -r kvm

These modules will return after a reboot or by running the modprobe commands again to load the modules:

sudo modprobe kvm_intel
sudo modprobe kvm
sudo /etc/init.d/libvirt-bin start

---

