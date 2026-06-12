---
title: "Attach NTFS drive to Virtual Box"
date: 2015-12-19
forum: Virtualisation
---

### Post by May_Masters on 2015-12-19
Hi all,

I'm running Ubuntu 15.10 as hosting OS with Virtual box that hosts Win7 64.
Now, I want to take my old data-disk from my former windows box and attach it to the Linux machine.
I want to access the data on the disk from Linux and Windows as well, so not another virtual disk should be created.

Is that possible ... and if so, how ?

---

### Post by sudodus on 2015-12-19
Welcome to the Ubuntu Forums :-)

1. If you activate USB in VirtualBox, you can connect your data-disk via USB.

2. If you install openssh-server (into the host operating system), you can connect to the drive via sftp (or some file browser, that can connect via 'ssh' which is doing the same thing under the hood. This way you can connect to all the mounted partitions in the host computer (on internal disks as well as external disks and pendrives).

---

### Post by May_Masters on 2015-12-19
Hi sudodus, thanks for the reply.

I've attached the "old disk" to my SATA controller and it is accessible via Ubuntu (NFS mount)
Now, is there a way to make it "directly" accessible - no file transfer protocol stuff - to the Win7 entity inside the virtualbox ?
Or - I don't like the sftp solution - create a cifs/nfs share and mount it with the guest system ?

Edit: or connect it via iSCSI ?

---

### Post by sudodus on 2015-12-19
I like ssh/sftp better than cifs/nfs, but both are possible, so yes, I think you can use cifs/nfs.

There are people around here, who know more about servers than I. Let us hope someone will see this thread and help you.

---

### Post by SeijiSensei on 2015-12-19
You can use "shared folders" to access the drive from within the VM.  You need to have the Extension Pack installed, I believe.  I have a machine with Win7 as the host and Kubuntu as the guest.  I can access the data disk on the Win7 host (G:\ in my case) via shared folders.

---

### Post by May_Masters on 2015-12-19
@[**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195"). Not sure ... aren't there any performance impacts doing so ? I mean, VB is translating the FS calls from win to linux and then back again to access the ntfs FS of the other disk ...
Or am I wrong here ?

I tried to create a "raw" vmdk 
```
VBoxManage internalcommands createrawvmdk -filename ntfs_disk.vmdk       -rawdisk /dev/sdd -partitions 4
```

problems is/are:
you can only successfully execute the command with 'sudo'. But then the resulting file is owned by root and VB can't open it.
So changing the ownership to 'user:user' (1000:1000) works, but VB still complains:
Die Plattenabbilddatei /vm-fs/ntfs_disk-pt.vmdk konnte nicht geöffnet werden.

Permission problem accessing the file for the medium '/vm-fs/ntfs_disk-pt.vmdk' (VERR_ACCESS_DENIED).

Fehlercode:VBOX_E_FILE_ERROR (0x80BB0004)
Komponente:MediumWrap
Interface:IMedium {4afe423b-43e0-e9d0-82e8-ceb307940dda}
Callee:IVirtualBox {0169423f-46b4-cde9-91af-1e9d5b6cd945}
Callee RC:VBOX_E_OBJECT_NOT_FOUND (0x80BB0001)

I guess this is because VB runs as 'user' (and not root) and still can't access /dev/sdb directly ...
I don't think it's such a good idea to run VB as root - right ?

Any ideas ?

(/dev/sdb4 is/was never mounted while executing the steps above)

---

### Post by sudodus on 2015-12-19
It would be straightforward to use drives in the host computer, if you run a linux KVM virtual machine instead of VirtualBox. See this link

[https://help.ubuntu.com/community/KVM/VirtManager](https://help.ubuntu.com/community/KVM/VirtManager)

[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

[https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation)

[http://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/](http://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/)

For example: That way you can easily boot from a USB pendrive, or if you wish from an image file of a USB pendrive, not only an iso file. All the mass storage devices, internal and external are easy to access. I don't know how much overhead there is, but it seems quite efficient for me.

---

### Post by SeijiSensei on 2015-12-20
Shared folders in VirtualBox use SMB networking I believe via the localhost interface.  I think they incorporate a stripped-down version of Samba on the host and an SMB client on the guest.  In practice you won't notice any performance issues.  I can easily stream HD video off the drive represented by the shared folder.

---

### Post by May_Masters on 2015-12-20
@sudodus: year, I thought about it. But I was told that KVM is great for more text based OS rather than with a lot of GUI (like Win). And qemu would emulate the underlying HW instead of talking directly to it. VirtualBox "should" (?) be able to do that ...
I don't have a actual perf-chart handy to compare KVM vs. VB vs. Xen, but the last one I saw put VB in the lead when Win was the guest OS.
But maybe this has changed now ...

@SeijiSensei: OK, I'll give it a try ... Additionally I'll do a performance test ;)


I also was told that Xen is the most sophisticated solution and has  the best performance results. But it would also be the most difficult to  install/configure ...
Does anyone has some experience with iSCSI ? ....

---

### Post by SeijiSensei on 2015-12-20
Are you planning on doing some type of heavy processing on this machine?  If not, why are you so concerned about "performance?"  Whatever differences you might measure will usually be invisible as an ordinary user.

In fact, if you're really concerned about performance you should be running on bare metal and not using a virtualization solution at all.

Over at [Linode]("http://www.linode.com/") where I rent virtual machines, they have been migrating from Xen to KVM for performance reasons, but their machines are hosting dozens of VMs.  For a single user running a VM, I'd make ease of use the priority over performance.

---

### Post by May_Masters on 2015-12-30
@SeijiSensei: Yes, I'm doing some heavy byte crunching on this box. Video editing
However, I made a performace test and copied a 10GB file from ext4 to the shared folder (also an underlying ext4 FS) and afterwards the same file from inside the Win VM to the shared folder.

the difference was just marginal. 
Copy from ext4 -> ext4 took 1 min 1 sec
Copy from VM NTFS -> ext4 took 1 min 6 sec

---

