---
title: "a VM for my 2nd storage device"
date: 2021-09-18
forum: Virtualisation
---

### Post by Skaperen on 2021-09-18
i want to run an install of Xubuntu 20.04 (guest) on my 2nd (of 3) storage device in a virtual machine under my existing Xubuntu 18.04 system (host).  both will be x86_64.  i plan to do a re-install under the VM so the device perspective will be correct (*sda* instead of *sdb*).   which VM would be best for this?  i am currently looking over QEMU/KVM and Oracle VirtualBox for this, but am not limited to this.  the one that i do *not* want to use is Xen.  what guidance on this do *you* have (if you have *knowledge* of this kind of thing)?

---

### Post by MAFoElffen on 2021-09-19
On both, the storage device/virtual disk, is a "file". With either KVM or VirtualBox, you can store that file anywher eyou want, as long as you configure where you want to put it when you create the Virtual Machine.

When a VM starts, whichever is the first VM disk device will appear as the first drive device. If you configure as Virtio, it will be labeled as "vda." If you confgure the storage as SATA, the first drive device will be labeled as "sda".

---

### Post by Skaperen on 2021-09-20
i will configure [FONT=courier new]/dev/sdb[/FONT] on the host system to allow the VM user to have read and write access.  i will configure the VM to use [FONT=courier new]/dev/sdb[/FONT] as its only storage device (and maybe also the ISO file as a read-only DVD).  in the normal startup, i expect it to start the VM with that device as the first and only storage device from which it will boot.

what i'm asking is if any particular VM software works better in this kind of setup.  one that simplifies the configuration to one line as very good and another that has to be configured by many statements defining what device addresses are where and do what.  one that could just do it all in one command "[FONT=courier new]vm /dev/sdb[/FONT]" would impress me if no others can.

years ago i played around with [FONT=courier new]qemu[/FONT] and found it to be awkward to configure but i managed to script around that.  today, things have changed and the scripts no longer work.  maybe it is easier, today.  maybe some other is easier.  i'm just asking.  but i described what i am doing in case that affects the particular ease of use.

---

### Post by MAFoElffen on 2021-09-22
I don't think you read and understood my post (#2) about virtual disks...

You could certainly physically pass-through your second hard disk completely to a VM, but "why" would you want to. when you don't really need to? And you do not seem to understand that you start to limit your possibilities by doing so?

Permissions and user access can be set many ways when dealing with Linux and Virtual Machines. As with KVM, you add the user to groups. To use a VM, then then there also the User permissions of the user.

If you were looking for "growth" and future expansion. But I think, as noticing your signature line... I am a System Admin, Developer/Programmer, Enterprise Infrasture Architect. If you want to mange your resources "smartly" for you and your users... First install LVM2, if you haven't already, and partion the drive as an LVM type. Add sdb1 as a PV, Create a VG separated from your other systems. Create a LV. Create a shared directory in that LV for your KVM VM's. Set your permissions of everything under that directory to the kvm and libvirt groups. Then reset your KVM's default default  pool for your Virtual Disks to a directory in that Volume Group, instead of the default being in /var/lib/libvirt/images. 

Use cow2 thin provisioned VM disk images. They start out as whatever they have used space on the install, and growing to what the size was you created them as. They can be grown in size, or shrank. If you run low on disk in your storage pool, you can hot-add more Physical Extents and grow your storage pool. With LVM, if you plan it right, you can also take LVM snapshots. 

If you just pass-through the physical disk and dedicate it to a VM, you tie you hands from being flexible like that... And if you are doing that with the same OS, with pysical pass-throughs, then one has to ask the question why are you doing VM? Because Linux is a mulituser OS. You could just add the other user and set their permissions and access limitations to what is already there. Right?

The one answer you may have it that you want that user shielded from the host. Something that can be controlled and isolated. But giving them an physical disk doesn't shied you from them (when you start passing through devices physically). If you pass through a physical device to a VM, then it is no longer accessible form the host. As a system Admin, that is not smart, because then you have to go through the VM to manage it and want is on it. As a part of a storage pool, using VM images, you still have administrative control and can manage it from your host. The advantage of a VM Host is to be able to share resources, and be able to manage them.

Does that make more sense now? And why I am having a time trying to understand why you would want to do that?

---

### Post by Skaperen on 2021-09-25
i want the guest system to see every sector of the disk identically mapped as a single device so that the guest can partition the disk, install to it, and make it bootable even for the physical hardware.  likewise, if i do partition and install to it using the physical hardware (booted with a USB memory stick with the bootable image dd'd to it), the VM will be able to boot from that and see all partitions as being on the same device.  it makes sense to attach the whole device as a whole device.

it comes up as /dev/sdb in the host system.  having it be /dev/sda in the virtual machine makes sense.  then i could configure a file to be first so the whole device i am working on comes up 2nd just like it does on the physical hardware.

this is not for "growth".  this is for having a 2nd system i can boot on the physical hardware that i can do maintenance and testing on while my primary system is up and running.  VM is just a utility for this.

cow2 makes no sense for this except for that added first disk.  but this disk will be very small with no intended usage other than as a place holder to bump the whole disk attachment to /dev/sdb if the VM does not have a way to fake it (the mainframe VM i worked on way back in the 1970s could do it).

> And why I am having a time trying to understand why you would want to do that?

i suspect it is more likely the case that you are assuming my purpose is more like why others use VMs.  for many purposes like that, i would use containers.  i have used VMs more recently as an embedded development tool  i worked from bootloader to init on emulated ARM and other architectures.  i had as many as 4 eval boards on my desk to run final and detail testing on.  VMs were for preprocessor and linker steps if the compilations i was frequently doing.  the i ran tests in a VM most of the time (sometimes on a board).

FYI, i have 21 users that i use, logged in, on my laptop.  one is letting me edit and post this.  another has an edit going where i am tweaking a Python3 script to do a specialized deep recursive conversion of UTF-8 to Unicode code points.  another is paused in a Curiosity Stream video.  another is dedicated to genealogy research (Ancestry dot com, Wikitree, and several others).  another just let me finish reading my email a couple hours ago.  each of the 21 users has its own instance of Xorg running (so each has a desktop with 10 virtual work spaces).  the kernel-based virtual consoles are not being used at all (i used to use them but these days graphical terminal emulators are fast enough).  i'm still a mostly CLI kind of user.  no MSFT anything in my home.

---

