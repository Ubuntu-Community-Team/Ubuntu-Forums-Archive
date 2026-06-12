---
title: "KVM VM migration from 10.04 host to 12.04.3 host failing"
date: 2013-10-06
forum: Virtualisation
---

### Post by TheFu on 2013-10-06
It is time to migrate a few older KVM VMs from an Ubuntu 10.04 hsotOS to a newer, better, faster, 12.04.x hostOS.  Migrated 2 Linux VMs and everything is fine. Went very smooth.

Tried to migrate a Windows7 Ultimate x32 VM and it will not boot.  Used boot-repair, gparted and the original Win7 DVD - each in turn. None of these tools was able to convince it to boot.

I used 
```
virsh dumpxml Win7Ult > /tmp/win7ult.xml
```
to export the machine settings.  Moved the raw disk and XML file over to the new hostOS, modified the XML for the new location of the raw.img file, used
```
virsh define /tmp/win7ult.xml
``` to get the VM settings into the new libvirt environment, and tried to boot it.  That produced and error in the /var/log/libvirt/libvirt.log about needing a newer HVM type and it suggested using **libvirt-migrate-qemu-machinetype** as a fix. No joy.

Now I'm not seeing any log messages at all - just "no OS found" after booting the VM. This is shown in the BIOS text on the console.

Tried to google. Didn't find anything.  Sorta stuck on things to try.  At least I haven't wiped the old VM off the other box yet, but I really need to migrate that hostOS to 12.04.

One of the main reasons people use virtualization is to hide the physical machine changes, right? Well, if that doesn't actually work ... er ...

Ideas for things to try?  The last resort is to reinstall fresh.  I'd rather NOT lose all the Windows Media Center settings, prior recording history, auto-record settings.  Windows doesn't handle backing up this stuff well at all.

---

