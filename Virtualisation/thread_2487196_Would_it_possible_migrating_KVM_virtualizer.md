---
title: "Would it possible migrating KVM virtualizer"
date: 2023-05-27
forum: Virtualisation
---

### Post by satimis on 2023-05-27
Hi all,

Would it be possible to migrate the complete KVM including guests from one drive to another drive in the same PC.

**[COLOR="#FF0000"]Drive-1: 2TB PCIe3.0 MVNe SSD[/COLOR]**
OS - Ubuntu 22.04 desktop
Virtualizer - VirtualBox
Virtualizer - KVM will be installed
[B][COLOR="#FF0000"]
Drive-2: 500G SATA3 SSD[/COLOR][/B]
OS - Ubutu 22.04 desktop
Virtualizor - KVM
KVM guests;
2 debian guests
3 ubuntu 22.04 guests
2 linux mint edge guests
2 window 10 guests
2 windows 10 pro guests

All KVM guests are for testing software, not for production.  Nether the PC is open to public.

If possible, please guide me HOW?  It would save me lot of time rather than migrating KVM guests, one by one.

Thanks

Regards

---

### Post by TheFu on 2023-05-27
Yes, it is possible.

The storage locations are stored in the XML file for each VM.  However, the type of backend storage used makes answering your question different.  For example, I moved 15 VMs from hadar to istar a few weeks ago.  Because I use LVM2-based storage for all the VMs, I had to manually migrate that to the new system.  If you use file-based storage, like qcow2 files, then you'd just need to 
[LIST=1]
[*]shutdown each VM
[*]copy those files from the old location to a new location
[*]modify the VM XML file definition
[/LIST]
Another option would be to mount additional storage directly to the place that KVM + libvirt expect it to be.  I do this for play, file-based, VMs.
```
Filesystem                        Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg01-libvirt--01      ext4  134G  131G     0 100% /var/lib/libvirt

```
134G was specifically added to there KVM+libvirt store VMs in  /var/lib/libvirt.

To modify the storage location in the xml files, use the **virsh edit ** command.  For example:
```
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw' cache='none' io='native'/>
**      <source dev='/dev/hadar-vg/lv-vpn09'/>**
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x09' function='0x0'/>
    </disk>

```
That's the line that needs modification.  You'll need to do this 1 VM at a time, but chances are that a little sed script can modify the storage line in each VM's XML trivially. Modifying the XML files directly won't work. Some mode of **virsh edit** or (**virsh dumpxml** + **virsh define**) must be used.  You could dump the XML for all VMs to /tmp, then sed modify the lines, then batch define them again.

If you use shared storage, it is possible to use a live migration, but that isn't possible with a dual boot setup.

BTW, it isn't safe to have 2 hypervisors installed within the same OS.  Their kernel drivers conflict. Don't do it.

---

### Post by Dennis N on 2023-05-27
That's a lot of VMs. You must be spending a lot of time keeping them all up to date. 

What you mean when you say "migrate the complete KVM" together with "rather than migrating KVM guests, one by one" isn't clear, so I will just relate my own experience as an ordinary user:

Several years ago I transferred 3 vms to a new machine. All these used qcow2 file-based storage. I just copied the qcow2 storage files to the new location, and imported them one by one with virt manager using "create a new virtual machine" with the "import existing disk image" option. I didn't transfer or edit any .xml files. It made new ones. Each vm took only a few minutes to import. All my programs and customizations were intact after importing. Simple enough.

I now use logical volume based storage for a vm. How to go about moving such an animal, I'm not sure. But, I have no plans to do that.

---

### Post by satimis on 2023-05-27
> **TheFu said:**
> Yes, it is possible....

- snip -

BTW, it isn't safe to have 2 hypervisors installed within the same OS.  Their kernel drivers conflict. Don't do it.
Hi,

Lot of thanks for your detailed advice.

Also it is not my idea running 2 hypervisors on the same drive.  

The storage space of the 500G SATA3 SSD is nearly full. To buy a new 2TB SSD ?

This daily working PC, Ryzen 5 AMD 8 cores CPU, is already 5 years old.  Graphic comes from the CPU and with 32G DDR3 RAM on board.  I prefer to build a new Ryzen 9 AMD CPU PC with 12 or 16 cores and wtih 64G DDR5 RAM on board.  I already have a component list prepared.

Where shall I post my component list on Ubuntu forum seeking for opionion?  Hardware Forum ?

Regards

---

### Post by satimis on 2023-05-27
> **Dennis N said:**
> That's a lot of VMs. You must be spending a lot of time keeping them all up to date.

- snip -

Hi,

The VMs are for testing only.  I don't need to update all of them daily.

I have experience migrating/moving VirtualBox VMs in group from old PC to new PC.  But I don't have experience on KVM guests.  I need TheFu's instruction after having my new PC built.

Regards

---

### Post by SeijiSensei on 2023-05-27
All the KVM machine images live in /var/lib/libvirt/images unless you specified a custom location. You should be able to migrate them to a different location using sudo.

Otherwise you can use virsh: [https://www.unixarena.com/2015/12/linux-kvm-change-libvirt-vm-image-store-path.html/](https://www.unixarena.com/2015/12/linux-kvm-change-libvirt-vm-image-store-path.html/)

---

### Post by satimis on 2023-05-27
> **SeijiSensei said:**
> All the KVM machine images live in /var/lib/libvirt/images unless you specified a custom location. You should be able to migrate them to a different location using sudo.

Otherwise you can use virsh: [https://www.unixarena.com/2015/12/linux-kvm-change-libvirt-vm-image-store-path.html/](https://www.unixarena.com/2015/12/linux-kvm-change-libvirt-vm-image-store-path.html/)
Hi,

Thanks

The migration looks similar to migrating VMs in group.  I have done it several times in the past, just copying the VM images on 'VirtualBox VMs" folder

Regards

---

### Post by MAFoElffen on 2023-05-28
I have answered this a few times on KVM migrations... satimis, you fill storage very fast. Maybe you should save up for 8TB drives...

I keep my VM storage on their own drives which I mount into the system.

KVM stores VM images into storage pools. The default location of the storage pools is defined as being at /var/lib/libvirt/images, named in the defines as pool name "default" as type "directory path". Their are many types that KVM can be.

The VM XML defines for each machine are located in directory /etc/libvirt/qemu/...

To make it easy to be able to migrate storage for KVM from machine to machine, with just a default looking machine, create a disk with a partition with two folders-- One for your VM xml defines, and one for images. Create two folders in that partition: images and xml. Set the ownership of the partition and all it's contents to libvirt-qemu:kvm... Label the disk as KVM-POOL. 

Create a mountpoint:
```

sudo mkdir /kvm-pool
sudo chown -R libvirt-qemu:kvm /kvm-storage 

```
Then find the UUID of user libvirt-qemu, and the guid of kvm on you machine
```

mafoelffen@Mikes-B460M:~$ getent group libvirt-qemu
libvirt-qemu:x:64055:libvirt-qemu
mafoelffen@Mikes-B460M:~$ getent group kvm
kvm:x:109:mafoelffen

```
Add this to your fstab, modifying to what you found in the last commands:
```

LABEL=KVM_POOL     /kvm-pool    ext4   uid=6405,gid=109,umask=022 0 1

```
After a default install of KVM, remove these two directories and replace them with these two links
```

sudo rm -r /var/lib/libvirt/images
sudo ln -s /kvm-pool/images /var/lib/libvirt/images
sudo rm -r /etc/libvirt/qemu
sudo ln -s /kvm-pool/xml /etc/libvirt/qemu

```
Everything will be wired to the semi-portable, migrated drive...

You can change the names to what makes sense to you, and what you can remember. Things are not locked in stone. That way, in the future, you never have to change anything, line by line, in your XML VM defines, to have to do a migration.

EDIT: To convert vbox, Hyper-V or VMware disk images to KVM, I convert to either raw or qcow2 using the qemu-img utility, using the convert option.

Yes, I love KVM...

---

### Post by satimis on 2023-05-28
Hi SeijiSensei,

Further to my posting #7

Just checked the 500G SATA3 SSD

$ sudo ls /var/lib/libvirt/images/
[sudo] password for satimis: ```

Mint00.qcow2                     ubuntu20.04-clone.qcow2  win10_02.qcow2
mintedge00.qcow2                 ubuntu20.04.qcow2        win10pro_00.qcow2
mintedge01.qcow2                 vm1-clone.qcow2          win10pro_01.qcow2
ubuntu20.04-clone-clone-1.qcow2  vm1.qcow2
ubuntu20.04-clone-clone.qcow2    win10_01.qcow2

```

All VM/Guest images of KVM are there.  I'll find a spare SSD for testing;
1. Install Ubuntu 22.04 desktop
2. Install KVM
3. Copy and paste 2/3 images to /var/lib/libvirt/images/
4. Start KVM -> Create a new virtual machine -> Import exiting disk image - Forward etc.

It looks similar to migrating VMs of VirtualBox.  The images folder is 'VirtualBox VMs'

Regards

---

### Post by TheFu on 2023-05-29
With Windows VMs, if you change the virtualized motherboard, then the registration will fail.  You may need to perform a fresh install of Windows.  Linux doesn't care ... or at least I don't think it does, but I've been burned by Windows VMs.  The virtual hardware needs to look **exactly** like it did before, though changing the CPU from Intel to AMD has worked for me on Win7.  I don't know about any later MSFT OSes.

---

### Post by QIII on 2023-05-29
For one MS Windows VM at a time from time to time, I have been able to call MS , tell them I moved or have to re-install a VM, and they have talked me through the process of re-authorization/registration of machines on a different virtual motherboard.  Bear in mind that the installations are recorded in their super-secret, watching-eye databases, so don't try to pull anything funny.  They do have a legitimate right to make sure that each authorized DVD is installed on only one machine at a time -- whether or not I agree with them keeping that in in their all-seeing data.  That is their big concern and I have had no problem assuring them that I am complying in the full spirit of their EULA.

YMMV.

---

