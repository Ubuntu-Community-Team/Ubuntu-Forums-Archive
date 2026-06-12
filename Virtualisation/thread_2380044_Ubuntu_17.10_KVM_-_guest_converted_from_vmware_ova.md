---
title: "Ubuntu 17.10 KVM - guest converted from vmware ova, permission denied"
date: 2017-12-12
forum: Virtualisation
---

### Post by getut on 2017-12-12
I have a newly installed machine that I'm trying to get set up to run KVM guests. I have a Vmware Workstation guest that I exported as an .ova and then imported using virt-v2v. When I try to start it I get a very long error message that basically says that it could not open the disk file, that permission is denied.

[LIST]
[*]Quirks that I have seen. virt-v2v always failed unless I ran it as root. Currently the virtual disk file is owned by root:root.
[*]Originally the vmware VM had spaces in the name. I reran the convert using the -on option of virt-v2v and remade it in a domain with no spaces in its name.
[/LIST]

I'm stuck and need some help. I've exhausted everything I can find searching the web.

---

### Post by ODTech on 2017-12-13
Have you tried to convert with qemu-img?

```
qemu-img convert <source file> <destination file>
```

---

### Post by KillerKelvUK on 2017-12-13
Have you tried simply changing the owner of the disk file so its user and group are either your user/group account combo or to 'kvm:libvirt-qemu' assuming you're using KVM with/via libvirt?

```

sudo chmod *user:group* [I]disk-file.xxx
[/I]
```

---

### Post by getut on 2017-12-13
> **KillerKelvUK said:**
> Have you tried simply changing the owner of the disk file so its user and group are either your user/group account combo or to 'kvm:libvirt-qemu' assuming you're using KVM with/via libvirt?



Yes, I tried both changing to 777 permissions and changing owner to my user:group. Neither worked. I'm still unclear if a brand new virtual machine (as opposed to a converted one) will actually run from that folder. I created a shell of a VM using the PXE boot option because I had no iso for any other install or testing available. virt-manager corrrectly created the disk file with root:root permissions, so I ultimately changed the converted VM back to root:root also since that appeared to be what it was supposed to be. My new VM test never actually wrote anything into the disk file though so it may not have been working. I'll try to do more confirmation on that.

I WAS able to simply move the disk file for the converted VM into my home folder and the VM starts up fine.

---

### Post by KillerKelvUK on 2017-12-13
Have you configured virsh to run your guests as the root user?  Would recommend against this entirely!  Disk files for me are owned by me when the guest runs and then revert to root:root when I stop the guest, this is normal and expectde behaviour because of where and how I created the disk files.  I have also modified my /etc/libvirt/qemu.conf to use my user instead of the default kvm:libvirt-qemu.

As for your original post this sounds like its a search permission issue to the folder containing the disk file as you've proven that by moving it to your home folder it works.  When using virt-manager to configure storage it usually applies an acl to the folder so that the kvm user can access both the folder and the contained files to work.  If you've modified the user configurations however then this might not work.  If you still can get it working after looking at the folder permissions please can you elaborate on any changed libvirt config since you installed it?

---

