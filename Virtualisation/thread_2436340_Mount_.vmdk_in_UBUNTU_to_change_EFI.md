---
title: "Mount .vmdk in UBUNTU to change EFI"
date: 2020-02-04
forum: Virtualisation
---

### Post by coerrace on 2020-02-04
Hello I have a .vmdk file and I need to change the boot.efi from it. How can I. lint the EFI partition of that .vmdk so I can change the boot.efi?

Note: Vmware can mount to /mnt/ the .vmdk but I don&#8217;t see the EFI partition where is located the boot.efi, then how can I access to that EFI partition/directory?

For example if I give this command: 
[COLOR=#000000]
vmware-mount -p my.vmdk
[/COLOR]
It will show the two partitions perfect the EFI partition is visible but how can I access it? Because if I give the command:

[COLOR=#000000]vmware-mount my.vmdk /mnt

[/COLOR]
It mounts something but is not the EFI partition. How can I then mount that EFI partition there in the .vmdk file?

Thank you

---

### Post by TheFu on 2020-02-05
Seems like a very specific VMware question.  Since they have paid support, I'd suggest calling them.

On a KVM hypervisor, I'd use **kpartx** to map the partitions to DMs and mount it that way.  Don't know if vdmk files are supported. Sorry.  After mounted, then a chroot environment will probably be necessary.

---

### Post by kevdog on 2020-02-06
Aren't you just booted to an EFI rescue prompt?

---

### Post by coerrace on 2020-02-08
> **kevdog said:**
> Aren't you just booted to an EFI rescue prompt?

Nop,it doesn’t boot in virtualbox.

---

### Post by deadflowr on 2020-02-08
Shouldn't you be setting the partition number when trying to mount?
Something like
```
vmware-mount /path/to/vmdk-file 1 /mountpoint
```
For reference: [https://pubs.vmware.com/vsphere-50/index.jsp?topic=%2Fcom.vmware.vddk.utils.doc_50%2Fdiskutils_mount.4.4.html]("https://pubs.vmware.com/vsphere-50/index.jsp?topic=%2Fcom.vmware.vddk.utils.doc_50%2Fdiskutils_mount.4.4.html")
Set the partition to which ever is the efi partition.

---

