---
title: "Allocating physical disk drives to KVM's (using libvirt)"
date: 2009-12-21
forum: Virtualisation
---

### Post by cveilleux on 2009-12-21
I really don't get that libvirt thing and documentation is so confusing.

I successfully installed my virtual machine inside an image file. This virtual machine is an OpenFiler NAS. I would like to make available two physical hard drives to the VM in order to configure a RAID and export some shares.

I just don't understand how I can make those 2 physical drivers (/dev/sdc and /dev/sdd) available to the VM. Any help?

---

### Post by geekshlby on 2009-12-22
Here's an example.  I use the LVM for my block device and virtio drivers, so your target dev and bus type may differ e.g. hda and 'ide' 

    <disk type='block' device='disk'>
      <source dev='/dev/Virtual/HomeServerOS'/>
      <target dev='vda' bus='virtio'/>
    </disk>
    <disk type='block' device='disk'>
      <source dev='/dev/Virtual/HomeServerData'/>
      <target dev='vdb' bus='virtio'/>
    </disk>

substitute source dev= for the host disk you want to provide to the guest

---

### Post by cveilleux on 2009-12-22
Many, many thanks.

It works like a charm.

Made the two physical drives available to the guest and been able to setup a software raid. To my great surprise, I see no noticeable performance drop!

Thanks again!

---

