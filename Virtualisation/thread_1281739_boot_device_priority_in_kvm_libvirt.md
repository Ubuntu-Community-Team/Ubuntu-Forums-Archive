---
title: "boot device priority in kvm libvirt"
date: 2009-10-03
forum: Virtualisation
---

### Post by uopjohnson on 2009-10-03
I would like to boot an existing working vm from an iso file.  I can add the iso to the xml file and import without a problem, but I have no idea how to set the boot device priority for the VM bios so it always boots from the disk.

---

### Post by uopjohnson on 2009-10-03
Damn, found it as soon as I asked.
In the xml file there is:
> <os>
    <type>hvm</type>
    <boot dev='hd'/>
  </os>
I just changed it to cdrom and all was well.

---

