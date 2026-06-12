---
title: "does python-vm-builder work with ESXi?"
date: 2008-10-27
forum: Virtualisation
---

### Post by carpeme on 2008-10-27
[https://help.ubuntu.com/community/JeOSVMBuilder](https://help.ubuntu.com/community/JeOSVMBuilder) states that "the currently supported hypervisors are KVM, Xen and VMware". I just wanted to confirm that by supporting VMware, this means that they're supporting ESXi?

---

### Post by Cerin on 2012-08-10
I'm also interested in this. Unfortunately, the docs for vm-builder are frustratingly terrible if not non-existent.

These links I found hint that there is some support, but it's not clear to me how to access it:

[http://rtroy.com/2008/12/31/jeosvmbuilder-and-vmware-esx/](http://rtroy.com/2008/12/31/jeosvmbuilder-and-vmware-esx/)
[http://packages.ubuntu.com/lucid-updates/all/python-vm-builder/filelist](http://packages.ubuntu.com/lucid-updates/all/python-vm-builder/filelist)

Specifically, the file /etc/vmbuilder/vmware/esxi.vmx.tmpl in Ubuntu's python-vm-builder package seems explicitly created for VMWare ESXi.

---

### Post by geeksmith on 2012-09-11
Yep, it does build an ESXi image with no problem:

[FONT="Courier New"]sudo vmbuilder esxi ubuntu --suite precise[/FONT]

--
@@ron

---

