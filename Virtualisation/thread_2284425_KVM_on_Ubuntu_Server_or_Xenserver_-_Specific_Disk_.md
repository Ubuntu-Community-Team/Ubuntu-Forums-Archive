---
title: "KVM on Ubuntu Server or Xenserver - Specific Disk requirements"
date: 2015-06-29
forum: Virtualisation
---

### Post by npinn001 on 2015-06-29
So I've been playing around with my N54L HP Microserver, and decided to wipe windows from it which was running as a server OS for me.

I'm debating a couple of options, with some specifics around the Virtualisation elements if I may be so bold as to ask for your knowledge....

(I need to be able to run a couple of windows VMs and a NAS type VM on top of whatever base I choose.)

I did install Xenserver, as Type 1 bare metal seemed to fit my needs. However, because the N54L doesnt support passthrough, it meant all the hard drives would be virtual drives and not native drives. 

(My storage solution is to keep the Data disks seperate and mount them in the VM to use, so that if I change OS I still keep the data).

I have considered using Ubuntu as the base and installing either Xen or KVM on top to allow me to mount the drives.

Questions - will i notice much difference in speed between type 1 and the type 2 above?
                am I missing a trick?
                Xen or KVM?

Ideally, whatever solution I use I would need to be able to manage remotely via CLI or web interface. Ilnow Xen supports this.

Thanks

---

### Post by TheFu on 2015-06-29
All the type-1/2 stuff is marketing. With recent-gen servers, with reasonable amounts of RAM, those labels mean next than nothing.  It would be better to say "limited hostOS support" or "complete hostOS support" as a comparison.  IMHO.

KVM. No question.  If you are that sensitive to performance and not making this stuff available over the internet, then use LXC. Ah - Windows - sorry.

For storage, use NFS if your HW doesn't support IOMMU + VT-d (i.e. pci passthru). On a home GigE network, that is generally fast enough.  BTW, about the only thing I would never run from a VM is storage servers.


IMHO.

---

### Post by npinn001 on 2015-06-30
> **TheFu said:**
> All the type-1/2 stuff is marketing. With recent-gen servers, with reasonable amounts of RAM, those labels mean next than nothing.  It would be better to say "limited hostOS support" or "complete hostOS support" as a comparison.  IMHO.

KVM. No question.  If you are that sensitive to performance and not making this stuff available over the internet, then use LXC. Ah - Windows - sorry.

For storage, use NFS if your HW doesn't support IOMMU + VT-d (i.e. pci passthru). On a home GigE network, that is generally fast enough.  BTW, about the only thing I would never run from a VM is storage servers.


IMHO.

TheFu - as ever your help is greatly appreciated. I hadnt actually thought of using NFS but will now.

Think I'll just go with an Ubuntu or Debian base and store all my files on that, with KVM on top and run the VMs through that. Had considered proxmox but dont like their implementation.

---

### Post by jason_gibson2 on 2015-06-30
Is the better choice. I played with the XenServer 6.5 for awhile, it was ok and easy to manage with the Windows console but it lacked flexibility I thought. In the end I moved to Ubuntu with KVM for a few things, and the host direct boots to Kodi for htpc purposes.

```
[COLOR=#000000]Ideally, whatever solution I use I would need to be able to manage remotely via CLI or web interface. Ilnow Xen supports this.[/COLOR]
```

Can do command line. If you are running a linux desktop or something there is Virt-Manager. Since I've gone to Windows on my laptop I found and use [Kimchi]("https://github.com/kimchi-project/kimchi"). Easy to install, easy to use web interface, it's a win all around.

---

### Post by KillerKelvUK on 2015-07-02
All good points above, I'm running Ubuntu host OS and KVM and have both Windows and Linux guest...all great.

One thing that may be of interest is that you don't need passthrough hardware capability (Vt-d) to assign a full HDD to a VM.  If you have a PCI raid card then passthrough is definitely the way to go but if you just have your disks on the SATA bus of your host you could pass the entire disk through to a VM.  From this your vm can become responsible for mdadm/software raid as well as file share e.g. NFS or Samba, I ran such a setup previously and performance was satisfactory for my needs...depends how much config and services you want on the host.

---

### Post by TheFu on 2015-07-02
[https://libvirt.org/storage.html#StorageBackendLogical](https://libvirt.org/storage.html#StorageBackendLogical) ... 

IMHO, managing storage from INSIDE the VM is the least recommended method because it adds the overhead of going through a VM layer.  With the hostOS running Linux, we have access to all the storage models that Linux supports and can make use of those for or VMs based on our specific requirements. Plus with shared storage available to multiple VM hosts, live migrations are possible. VERY cool. 

I think a best practice is to have a LV per guestOS - this means snapshots can be used for backups. Very nice. [https://www.howtoforge.com/linux_lvm_snapshots](https://www.howtoforge.com/linux_lvm_snapshots)

Extremely flexible, to say the least.

---

### Post by npinn001 on 2015-07-06
> **KillerKelvUK said:**
> All good points above, I'm running Ubuntu host OS and KVM and have both Windows and Linux guest...all great.

One thing that may be of interest is that you don't need passthrough hardware capability (Vt-d) to assign a full HDD to a VM.  If you have a PCI raid card then passthrough is definitely the way to go but if you just have your disks on the SATA bus of your host you could pass the entire disk through to a VM.  From this your vm can become responsible for mdadm/software raid as well as file share e.g. NFS or Samba, I ran such a setup previously and performance was satisfactory for my needs...depends how much config and services you want on the host.

This is useful - how would I go about this please (assigning a disk to the vm)?

---

### Post by KillerKelvUK on 2015-07-06
See here...[https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Virtualization_Administration_Guide/sect-Virtualization-Adding_storage_devices_to_guests-Adding_hard_drives_and_other_block_devices_to_a_guest.html](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Virtualization_Administration_Guide/sect-Virtualization-Adding_storage_devices_to_guests-Adding_hard_drives_and_other_block_devices_to_a_guest.html)...for a summary.  Pretty basic xml entry using virsh.  If you're going to try this heed TheFu's comments above as well as the 'Important' message at the bottom of the linked page, like I said for my needs at the time this worked so may fit for yours however I now manage filesystems and network shares from the host.

---

### Post by npinn001 on 2015-07-07
> **TheFu said:**
> All the type-1/2 stuff is marketing. With recent-gen servers, with reasonable amounts of RAM, those labels mean next than nothing.  It would be better to say "limited hostOS support" or "complete hostOS support" as a comparison.  IMHO.

KVM. No question.  If you are that sensitive to performance and not making this stuff available over the internet, then use LXC. Ah - Windows - sorry.

For storage, use NFS if your HW doesn't support IOMMU + VT-d (i.e. pci passthru). On a home GigE network, that is generally fast enough.  BTW, about the only thing I would never run from a VM is storage servers.


IMHO.

The Fu - how do you find NFS/Samba. I've set my system up the way you have kindly suggested, but my connecting my mac to NFS is proving problematic. Thinking that I might have to revert to SMB  - have you any guidance if this would be a worse idea?

---

### Post by TheFu on 2015-07-07
NFS you must have an NFS client and use mounts. Don't know how to do that on OSX - the Apple people never use normal names for stuff like this.  For example, they don't call ssh "ssh" - they call it something friendly that makes NO SENSE at all.  I had a Mac for a few weeks - gave it away over all the little issues like that. The complete lack of select/paste drove me crazy. There is some amazing consistency in OSX, so I get why people like/prefer it. I just already had my muscle-memory set and don't want to change. I hear the Apple hardware runs Ubuntu and Fedora great!
NFS storage behaves just like local storage - same groups, same file permissions, hardlinks, symlinks ... those all work.  Can't do any of that stuff on Samba. Oh - and NFS is faster.  Inside any file manager, NFS storage that has been mounted appears like local storage on the system.

Samba ... I wouldn't use it between Unix systems. You can browse using any file manager. smb:// to start the URL.

---

### Post by npinn001 on 2015-07-07
> **TheFu said:**
> NFS you must have an NFS client and use mounts. Don't know how to do that on OSX - the Apple people never use normal names for stuff like this.  For example, they don't call ssh "ssh" - they call it something friendly that makes NO SENSE at all.  I had a Mac for a few weeks - gave it away over all the little issues like that. The complete lack of select/paste drove me crazy.
NFS storage behaves just like local storage - same groups, same file permissions, hardlinks, symlinks ... those all work.  Can't do any of that stuff on Samba. Oh - and NFS is faster.  Inside any file manager, NFS storage that has been mounted appears like local storage on the system.

Samba ... I wouldn't use it between Unix systems. You can browse using any file manager. smb:// to start the URL.

Couldnt agree more about apple, but its a family members machine so I have to connect it. But I think I'll stick to NFS based on the features you just mentioned. Thanks for the advice.

---

### Post by KillerKelvUK on 2015-07-08
> **npinn001 said:**
> Couldnt agree more about apple, but its a family members machine so I have to connect it. But I think I'll stick to NFS based on the features you just mentioned. Thanks for the advice.

If you're using Mac then you may want to consider AFP...I set up a TimeMachine on my ubuntu server once...worked a treat.

[http://outcoldman.com/en/archive/2014/11/09/ubuntu-as-home-server-part-3-afp-server/](http://outcoldman.com/en/archive/2014/11/09/ubuntu-as-home-server-part-3-afp-server/)

---

