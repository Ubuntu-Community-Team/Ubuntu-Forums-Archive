---
title: "KVM: how do I correctly clone a guest image?"
date: 2018-02-21
forum: Virtualisation
---

### Post by vasa1 on 2018-02-21
This is what I started with:```
$ virsh list --all
 Id    Name                           State
----------------------------------------------------
 -     generic                        shut off
 -     XubuBionic                     shut off
```
where "generic" is Xubuntu 16.04 and "XubuBionic" *was* Xubuntu 18.04.

After that, I clearly did something wrong:
```
$ sudo virt-clone --original XubuBionic --name LuXuBionic
[sudo] password for vasa1: 

Clone 'LuXuBionic' created successfully.
```
This took just a few seconds to complete.

And
```
$ virsh list --all
 Id    Name                           State
----------------------------------------------------
 -     generic                        shut off
 -     LuXuBionic                     shut off
 -     XubuBionic                     shut off
$
```
I opened LuXuBionic, ran *sudo apt-get update* and *sudo apt-get dist-upgrade* without any errors. I then ran *sudo apt-get install lubuntu-desktop*. That too went off okay.

On reboot, I could log into into Lubuntu.

Where I've obviously gone wrong is that all I installed in LuXuBionic has also been installed in XubuBionic :( I thought that XubuBionic would remain a clean Xubuntu 18.04.

I don't mind starting over, but what is the correct way to clone and then modify the clone and not the "parent"?

My host is Kubuntu 16.04.

```
$ kvm --version
QEMU emulator version 2.5.0 (Debian 1:2.5+dfsg-5ubuntu10.22), Copyright (c) 2003-2008 Fabrice Bellard
$
```

---

### Post by TheFu on 2018-02-21
There are 2 parts to cloning, IMHO.
* Storage
* VM Setup

**qemu-img** is how I'd clone the storage.  Perhaps virsh has a clone method?  ... yep, according to the manpage, **virsh vol-clone** is there. I've never used it.
I'd use virsh dumpxml to get a copy of the VM settings, then modify those to be unique/different, and use **virsh define** to put the modified XML into the repo.

Whether these are "the best" methods, I don't know.

If you are using qcow2 storage, you can have a base qcow2 file as the first layer and do overlays for each VM, I believe.  Sorta like using LVM with different snapshots for each VM.

Of course, cloning the storage doesn't change the hostname, domainname, or any network MAC addresses which will cause issues on a LAN.  Last time I cloned a VM, I was careful to only have the new VM running until I'd modified the MAC, hostname, and network settings inside the VM.

And as always, the manpages for each command is the documentation for them. There are subtle aspects for every command that are probably important to understand.  Being flexible also means having unexpected edge cases.

---

### Post by vasa1 on 2018-02-21
*virt-sysprep* looks interesting: [http://manpages.ubuntu.com/manpages/xenial/man1/virt-sysprep.1.html](http://manpages.ubuntu.com/manpages/xenial/man1/virt-sysprep.1.html)

---

### Post by TheFu on 2018-02-21
> **vasa1 said:**
> *virt-sysprep* looks interesting: [http://manpages.ubuntu.com/manpages/xenial/man1/virt-sysprep.1.html](http://manpages.ubuntu.com/manpages/xenial/man1/virt-sysprep.1.html)

Very nice find!  I wasn't aware of that tool, though I have used the Windows sysprep tool to migrate a Windows7 image from 1 VM to another without losing data.  Still had to call MSFT to get the license approved - changing the virtual motherboard was more than their license would accept, even though it was a retail license.
From the manpage on my main VM host which runs 14.04:
> 
virt-sysprep does not currently work on Microsoft Windows guests.

Too bad.  My other VM hosts didn't have the tool installed. It is part of the libguestfs-tools package. On 16.04, the same no-Windows-sysprep is in the manpage.

Regardless, I like to understand what is really happening underneath so when a tool fails, it isn't THAT much effort to fix over 1 small thing.

Thanks for finding this.  **man guestfs-faq** has more stuff.

---

### Post by vasa1 on 2018-02-21
Well, it turns out I didn't need to dig into *virt-sysprep* after all.

[LIST]
[*]I ran the guest OS which I wanted to clone.
[*]I shut it down to see the "Guest not running" message on the screen.
[*]I clicked on "Virtual Machine" in the menu bar and chose "Clone...".
[*]A window appeared suggesting "Xubu-Bionic-clone" as the name which I accepted.
[*]Below that, I changed "Share Disk with Xubu-Bionic" to "Clone this disk (30.0 GiB)" and pressed "Clone".
[*]A new window titled "Creating virtual machine clone 'Xubu-Bionic-clone'" appeared with a progress bar. And after a couple of minutes things were done.
[*]I completely closed down the VMM and restarted it, this time choosing to run the clone. I logged in and installed "aha", one of the smallest packages I know of. I shutdown the clone and started the parent. No "aha" there.
[/LIST]
 So I think I'm good.  My needs are pretty simple :)

Thank you TheFu for the initial push!

---

### Post by Doug S on 2018-02-21
I have only ever used virt-clone and never had a problem with it. I have only ever used [this reference]("https://help.ubuntu.com/lts/serverguide/libvirt.html#libvirt-virt-clone"), from which I gather you might not have allocated a new place for the clone. Examples:
```
sudo virt-clone -o desk_dev -n desk_test1 -f /media/newhd/desk_test1.img --check path_exists=off
sudo virt-clone -o desk_dev -n desk_test2 -f /media/newhd/desk_test2.img --check path_exists=off
```

Edit:
> This took just a few seconds to complete.I do not recall exactly how long it takes, but I think it was several minutes.

---

### Post by vasa1 on 2018-02-21
My images are here:```
/var/lib/libvirt/images $ sudo ls -l
total 25328032
-rw------- 1 libvirt-qemu kvm 48984752128 Feb 20 17:46 generic.qcow2
-rw------- 1 libvirt-qemu kvm  5274533888 Feb 21 19:51 Xubu-Bionic-clone.qcow2
-rw------- 1 libvirt-qemu kvm 32217432064 Feb 21 19:53 Xubu-Bionic.qcow2
/var/lib/libvirt/images $ 
```I don't know why there's such a size difference between the clone and the original :???:

As for the few seconds that my *virt-clone* operation took, it looks like it didn't do anything useful at all :(

---

### Post by TheFu on 2018-02-21
I suspect the clone is a sparse file - which is fine for SSD storage.  It will have a slight performance impact on spinning disks.  qemu-img can be used to see the properties of any storage.

I also suspect that your clone didn't get a different hostname nor were the udev rules cleaned up for the MAC.  OTOH, both of these things are easy to check for you (or me).  Duplicate MACs are bad on a LAN.

---

### Post by Doug S on 2018-02-21
> **vasa1 said:**
> I don't know why there's such a size difference between the clone and the original :???:(I think the cloning operation only allocates disk space actually used, and not whatever you gave the original VM. I did a clone on my system using:

```
sudo virt-clone -o desk_aa -n desk_tesst1 -f /media/vm/desk_test1.img --check path_exists=off
```It took 5 minutes and I got:
```
$ ls -l /media/vm
total 39402228
-rw------- 1 root root [COLOR="#FF0000"]53695545344[/COLOR] Feb 20 15:59 desk_aa.img
-rw------- 1 root root [COLOR="#FF0000"]16519331840[/COLOR] Feb 21 08:42 desk_test1.img
drwxr-xr-x 2 doug doug        4096 Oct  1 10:13 doug
drwx------ 2 root root       16384 Sep 27 15:33 lost+found
-rw------- 1 root root 53695545344 Feb 20 15:58 serv64_dev.img

```

---

### Post by vasa1 on 2018-02-21
> **TheFu said:**
> I suspect the clone is a sparse file - which is fine for SSD storage.  It will have a slight performance impact on spinning disks.  qemu-img can be used to see the properties of any storage.

I also suspect that your clone didn't get a different hostname nor were the udev rules cleaned up for the MAC.  OTOH, both of these things are easy to check for you (or me).  Duplicate MACs are bad on a LAN.

xml dumps show that the MAC addresses are different:```
XB       <mac address='52:54:00:21:7f:5c'/>
XBC      <mac address='52:54:00:5f:c5:7d'/>
```I don't know about the hostname or udev rules.

> **Doug S said:**
> I think the cloning operation only allocates disk space actually used, and not whatever you gave the original VM. I did a clone on my system using:

```
sudo virt-clone -o desk_aa -n desk_tesst1 -f /media/vm/desk_test1.img --check path_exists=off
```It took 5 minutes and I got:
```
$ ls -l /media/vm
total 39402228
-rw------- 1 root root [COLOR="#FF0000"]53695545344[/COLOR] Feb 20 15:59 desk_aa.img
-rw------- 1 root root [COLOR="#FF0000"]16519331840[/COLOR] Feb 21 08:42 desk_test1.img
drwxr-xr-x 2 doug doug        4096 Oct  1 10:13 doug
drwx------ 2 root root       16384 Sep 27 15:33 lost+found
-rw------- 1 root root 53695545344 Feb 20 15:58 serv64_dev.img

```
Thanks, that makes sense!

---

### Post by TheFu on 2018-02-21
Using **qemu-img info path/to/storage-file.qcow** will show if the storage is sparse or fully allocated.

```
$ qemu-img info vpn-1604.qcow2
image: vpn-1604.qcow2
file format: qcow2
virtual size: 7.0G (7516192768 bytes)
disk size: 5.1G
cluster_size: 65536
Format specific information:
    compat: 1.1
    lazy refcounts: true
```
See the virtual size and disk sizes?  On disk, it is 5.1G (using du -h). It is a sparse allocation.

An older version of that VM used fully allocated storage:
```
$ qemu-img info  ./vpn.img 
image: ./vpn.img
file format: raw
virtual size: 11G (11811160064 bytes)
disk size: 11G

```

---

### Post by vasa1 on 2018-02-21
> **TheFu said:**
> Using **qemu-img info path/to/storage-file.qcow** will show if the storage is sparse or fully allocated.
...
Thanks!```
$ sudo qemu-img info /var/lib/libvirt/images/Xubu-Bionic-clone.qcow2
[sudo] password for vasa1: 
image: /var/lib/libvirt/images/Xubu-Bionic-clone.qcow2
file format: qcow2
virtual size: 30G (32212254720 bytes)
disk size: 4.9G
cluster_size: 65536
Format specific information:
    compat: 1.1
    lazy refcounts: true
    refcount bits: 16
    corrupt: false
$ sudo qemu-img info /var/lib/libvirt/images/Xubu-Bionic.qcow2
image: /var/lib/libvirt/images/Xubu-Bionic.qcow2
file format: qcow2
virtual size: 30G (32212254720 bytes)
disk size: 6.7G
cluster_size: 65536
Format specific information:
    compat: 1.1
    lazy refcounts: true
    refcount bits: 16
    corrupt: false                                                      
$
```

---

### Post by TheFu on 2018-02-21
They are both sparse. Hope they are on an SSD.

---

### Post by vasa1 on 2018-02-21
> **TheFu said:**
> They are both sparse. Hope they are on an SSD.

No, the hard disk is the older conventional type. Would SSD offer advantages other than speed?

---

### Post by TheFu on 2018-02-21
> **vasa1 said:**
> No, the hard disk is the older conventional type. Would SSD offer advantages other than speed?

In theory, SSDs will last longer than spinning disks.
And on spinning HDDs sparse files were 30% slower than fully pre-allocated storage in my testing a few years ago.  It was enough that I only use sparse for VMs that don't have data.   I haven't retested sparse files since.

---

