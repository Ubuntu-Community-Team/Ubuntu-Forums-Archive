---
title: "virt-manager fails when assigning storage space"
date: 2008-04-24
forum: Virtualisation
---

### Post by bimmerd00d on 2008-04-24
EDIT!!!!:  I had to make sure VT was enabled in the BIOS, and for kicks i pulled the battery and held the power button for 10s or so.  Now Hardware Acceleration is kicking.  :guitar:  However, i have a 65w and a 90w adapter.  If i boot up without the 65w adapter, the BIOS or whatever kicks it into low-power mode or something and it wont run the proc with VT.  I have to either run all off battery or use the 90w adapter.

I installed kvm, libvirt-bin, and kvm and am attempting to get XP up and running in Qemu.  I launched virt-manager with the --no-fork option, and this is the info i get when i go to create the storage space.  I tried just leaving it as default 4000MB and it still gives me the same error.  This is the error, anyone have any ideas?

```
bimmerd00d@M3:~/vmachines$ virt-manager  --no-fork
Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/create.py", line 295, in forward
    if(self.validate(notebook.get_current_page()) != True):
  File "/usr/share/virt-manager/virtManager/create.py", line 915, in validate
    self._disk.virtio = self._guest.get_virtio_blk()
  File "/usr/lib/python2.5/site-packages/virtinst/FullVirtGuest.py", line 206, in get_virtio_blk
    return FullVirtGuest.OS_TYPES[self.os_type]["virtio_blk"]
KeyError: 'virtio_blk'

```

---

### Post by mr-bean on 2008-04-24
I just installed KVM + virtmanager etc...  On hardy 8.04 and I'm getting the same problem.  The virtual file is not being created.
Anyone have any ideas??

Thanks

---

### Post by mr-bean on 2008-04-24
I just found that disabling the hardware acceleration allowed the creation of the disk file, so maybe I need to check my BIOS to make sure the VT stuff is switched on.

---

### Post by bimmerd00d on 2008-04-24
> **mr-bean said:**
> I just found that disabling the hardware acceleration allowed the creation of the disk file, so maybe I need to check my BIOS to make sure the VT stuff is switched on.

I definitely have VT enabled (and support for it).  Disabling HW accel worked for me.  That kinda sucks, don't we want hardware acceleration enabled?

---

### Post by bimmerd00d on 2008-04-24
Fixed it, see edited first post.

---

### Post by Cloud79 on 2008-04-25
I get the same problem on a server with VT enabled. The last update of virt-manager is broken!

It worked with the version before (where bridging where broken)

I want to run kvm with virt-manager on our devnet but if the packages isn't working, it's kinda hard :/

---

### Post by eshattow on 2008-04-25
Reported as bug #221746.

---

### Post by Cloud79 on 2008-04-28
> **eshattow said:**
> Reported as bug #221746.

It sucks that it takes such a long time to release the fixed deb. :(

---

### Post by Devrdander on 2008-04-29
Open up Synaptic (System, Administration, Synaptic) click on Settings, goto Repositories.

Goto the Updates Tab, check Pre-Released updates (hardy-proposed)

Click the Reload button, then Search for "virtinst"

Right click on virtinst and click on upgrade.

When complete you should have ver 0.300.2-0ubuntu6

---

