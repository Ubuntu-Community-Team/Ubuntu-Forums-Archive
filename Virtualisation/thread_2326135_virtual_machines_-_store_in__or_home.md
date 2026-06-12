---
title: "virtual machines - store in / or /home?"
date: 2016-05-28
forum: Virtualisation
---

### Post by jub2 on 2016-05-28
About to do a fresh install of ubuntu and planning on running a VirtualBox vm running Windows 7. Should the virtual machine file be stored in root or home? That will determine how large I should make those respective partitions since the Win7 vm file will be rather large.

---

### Post by T.J. on 2016-05-28
If you mean literally, it does not matter as long as you have space.  If you are asking for an opinion, they should always be in /home. 

 The root and /home should always be on separate partitions. The main reason for using /home is that when it comes time to upgrade your OS, you can preserve VMs more easily.  The second reason is that VirtualBox is a type 2 hypervisor, that depends on data in /home to function properly.  You might as well keep all the data in one place, rather than risk deleting some of it when you upgrade, leaving your VMs worthless.


That said, I'd like to venture a further opinion, which you can feel welcome to ignore.   

If you had to ask me what is the best way to use VirtualBox, I would say: **don't.** 

 In fact, if Ubuntu dropped it from the repository *completely*, I'd be pleased to no end. It's a poor virtualization solution.

Not only is VirtualBox a deficient hypervisor with poor performance, it has longstanding bugs in the guest drivers.  It is also managed by Oracle, and frankly, Oracle does not have FOSS's best interests at heart.    Using Virt-manager and KVM is a far superior choice, and you need have no fears from patent trolls like Oracle.   If you have  secondary graphics processor, you can even do something with KVM that VirtualBox can't do - get full rendering support for video.  That means that with the proper setup,  DirectX or OpenGL in guests just works. I can even play games in the KVM, such as Fallout 4.

I don't even keep a native Windows partition or dual boot anymore because KVM does the job so well.  I stopped using VirtualBox a few years ago, and switched to KVM. It improved my time immeasurably over VirtualBox, even with just little things, like resizing drive files. 

I'll **never** go back to Oracle's crapware.

---

### Post by jub2 on 2016-05-28
That makes sense, thanks.

So if I'm doing an install where the primary drive doesn't have sufficient space for root, home and swap partitions, and I want to spread out to a secondary drive, it makes more sense to place root and swap partitions on the primary drive and place the home partition on the secondary drive?

The alternative I was thinking about was root and home on the primary drive, and swap and another partition (for the virtual machine) on the secondary drive. But given what you're saying about VirtualBox, this arrangement of the data partition with the virtual machine being separate from the /home partition may not work so well.

---

### Post by T.J. on 2016-05-28
Added more information to the original post =)


> **jub2 said:**
> That makes sense, thanks.

So if I'm doing an install where the primary drive doesn't have sufficient space for root, home and swap partitions, and I want to spread out to a secondary drive, it makes more sense to place root and swap partitions on the primary drive and place the home partition on the secondary drive?

Absolutely.  If I might say so, you might want to consider using logical volumes, if you aren't already.

> 
The alternative I was thinking about was root and home on the primary drive, and swap and another partition (for the virtual machine) on the secondary drive. But given what you're saying about VirtualBox, this arrangement of the data partition with the virtual machine being separate from the /home partition may not work so well.

It will be fine, as long as you remember that VirtualBox stores critical data settings, including drive format IDs in a hidden folder named ".VirtualBox" in your home directory.  If you lose those, even if you backed up the VM, Windows VM's may not boot or will require that you reauthorize your install.

KVMs do not have that problem.

---

### Post by kcallis on 2016-05-28
> **T.J. said:**
> Added more information to the original post =)




Absolutely.  If I might say so, you might want to consider using logical volumes, if you aren't already.



It will be fine, as long as you remember that VirtualBox stores critical data settings, including drive format IDs in .VirtualBox in your home directory.  If you lose those, even if you backed up the VM, Windows may not boot or will require that you reauthorize your install.

I am glad that your broached that topic, which saves me from asking to forum. I am currently running US 16.04. Although I am doing my virtual host on a laptop, I need to approach this from a stand point of doing this as if I were at the office with a quad Xeon quad core machine with 64G of RAM. My laptop has a 500G hard drive. I created a 50G lv / partition (along with swap). So what is the correct way of setting up the other volumes. Do I create a partition of say about 150G which would hold the images (iso, vdmk, etc) and the create another volume that it strictly for data or is there a better way to utilize lvm with kvm?

---

### Post by jub2 on 2016-05-28
> **T.J. said:**
> Added more information to the original post =)Noted!

> **T.J. said:**
> Absolutely.  If I might say so, you might want to consider using logical volumes, if you aren't already.Not sure I follow. Does it make a difference whether the various partitions are primary partitions or merely logical partitions in an extended partition? I was thinking I might use GPT partitioning.

> **T.J. said:**
> 
It will be fine, as long as you remember that VirtualBox stores critical data settings, including drive format IDs in a hidden folder named ".VirtualBox" in your home directory.  If you lose those, even if you backed up the VM, Windows VM's may not boot or will require that you reauthorize your install.
OK, so if I use VirtualBox (and I may not, given your comments), the only added issue/complexity vs using keeping all my data including VMs in /home, is to keep in mind that VirtualBox data will be split between the partition I keep VM's in and the hidden folder in /home.

So really there's no compelling reason, from a virtualization perspective, to using one partition for data or using multiple partitions for data.

---

### Post by T.J. on 2016-05-29
> **jub2 said:**
> Noted!

Not sure I follow. Does it make a difference whether the various partitions are primary partitions or merely logical partitions in an extended partition? I was thinking I might use GPT partitioning.


When I was referring to logical volumes, I was referring to Logical Volume Management (LVM).  It's far more efficient for allocating space than standard partitions if you want to be able to reallocate space.  LVM has nothing to do directly with virtualization, but it does allow you to keep a pool of unallocated slack space on the disc, allocate it as a partition and then free it as necessary.

> OK, so if I use VirtualBox (and I may not, given your comments), the only added issue/complexity vs using keeping all my data including VMs in /home, is to keep in mind that VirtualBox data will be split between the partition I keep VM's in and the hidden folder in /home.

Yes, that is correct.

> So really there's no compelling reason, from a virtualization perspective, to using one partition for data or using multiple partitions for data.

For a personal workstation, not really.  A server might be a different matter.

---

### Post by T.J. on 2016-05-29
> **kcallis said:**
> I am glad that your broached that topic, which saves me from asking to forum. I am currently running US 16.04. Although I am doing my virtual host on a laptop, I need to approach this from a stand point of doing this as if I were at the office with a quad Xeon quad core machine with 64G of RAM. My laptop has a 500G hard drive. I created a 50G lv / partition (along with swap). So what is the correct way of setting up the other volumes. Do I create a partition of say about 150G which would hold the images (iso, vdmk, etc) and the create another volume that it strictly for data or is there a better way to utilize lvm with kvm?

Given the size of your data drive, I would just allocate 250MB for a boot or UEFI partition, 35GB for a / partition, 2x your RAM for swap, and then I would allocate the rest for /home. I would store you VM's in /home. not /.

---

### Post by kcallis on 2016-05-29
> **T.J. said:**
> Given the size of your data drive, I would just allocate 250MB for a boot or UEFI partition, 35GB for a / partition, 2x your RAM for swap, and then I would allocate the rest for /home. I would store you VM's in /home. not /.

Currenly, I have the following in play:

```
± |master &#10003;| &#8594; lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
NAME                           FSTYPE        SIZE MOUNTPOINT LABEL
sda                                        465.8G            
&#9500;&#9472;sda1                         ext2          487M /boot      
&#9500;&#9472;sda2                                         1K            
&#9492;&#9472;sda5                         LVM2_member 465.3G            
  &#9500;&#9472;kobayashi--maru--vg-root   ext4         43.3G /          
  &#9492;&#9472;kobayashi--maru--vg-swap_1 swap          7.9G [SWAP]     
sr0                                         1024M         

```

I thought that I would create a logical volume of 50G to hold iso, etc. I was thing thinking about a lv of 150G for data, because I also want to use that space for containers (docker, vagrant and lxd). Does that sound correct or should I go another route?

---

### Post by T.J. on 2016-05-29
> **kcallis said:**
> Currenly, I have the following in play:


I thought that I would create a logical volume of 50G to hold iso, etc. I was thing thinking about a lv of 150G for data, because I also want to use that space for containers (docker, vagrant and lxd). Does that sound correct or should I go another route?

I do not administer servers any longer, and have never used containers.  I'm sorry, but I really can't (and shouldn't) advise you when containers are in the mix, such as docker or lxd. I don't want to give you bad advice.   One comment I can make with certainty is that if you are using LVM, you can leave as much slack space as you can allow. That should help with future situations, since you can reallocate it at any time.
 

(There is something I do not understand, and if someone reading this can enlighten me in an off-topic post, message or a new thread, I would be honestly grateful. A "container" is little more than a read-only chroot, enhanced with cgroups and namespaces, which makes them a Linux only consideration. I find it very strange that everyone can have such a "hissy fit" over systemd, which uses cgroups. The fact that cgroups renders code unportable was a huge complaint with systemd. Then the same people turn around and embrace Docker and lxd, which also uses cgroups. 

Systemd was accused of breaking software. Docker can break software in the container, yet Docker gets a "free pass".  

It's a strange double standard within the Linux developer community that I do not comprehend.)

---

### Post by kcallis on 2016-05-29
> **T.J. said:**
> I do not administer servers any longer, and have never used containers.  I'm sorry, but I really can't (and shouldn't) advise you when containers are in the mix, such as docker or lxd. I don't want to give you bad advice.   One comment I can make with certainty is that if you are using LVM, you can leave as much slack space as you can allow. That should help with future situations, since you can reallocate it at any time.
 

(There is something I do not understand, and if someone reading this can enlighten me in an off-topic post, message or a new thread, I would be honestly grateful. A "container" is little more than a read-only chroot, enhanced with cgroups and namespaces, which makes them a Linux only consideration. I find it very strange that everyone can have such a "hissy fit" over systemd, which uses cgroups. The fact that cgroups renders code unportable was a huge complaint with systemd. Then the same people turn around and embrace Docker and lxd, which also uses cgroups. 

Systemd was accused of breaking software. Docker can break software in the container, yet Docker gets a "free pass".  

It's a strange double standard within the Linux developer community that I do not comprehend.)

I am just trying to get my head around playing around with virtualization beyond using desktop virtualization (ie Virtual-box). For instance, I just created a 100G logical drive for data and I just did a logical for images. Now I am doing my due diligence to understand how to make a block device for both the images as well as the data. So it is all just a leaning curve for me. But I need to do something since is have been sitting here and have yet to have a single guest running! :(

---

### Post by T.J. on 2016-05-30
> **kcallis said:**
> I am just trying to get my head around playing around with virtualization beyond using desktop virtualization (ie Virtual-box). For instance, I just created a 100G logical drive for data and I just did a logical for images. Now I am doing my due diligence to understand how to make a block device for both the images as well as the data. So it is all just a leaning curve for me. But I need to do something since is have been sitting here and have yet to have a single guest running! :(

Hello again!

The easy way to allocate space for KVM is to just use an image file, just like you would with VirtualBox. 

*qemu-img create -f qcow2 image.qcow2 80G  *

That command will create a file that can be used as a drive image that can expand out to 80G before being full.


I think there might be some confusion.  You can give a KVM direct access to raw LVM partitions, but I don't recommend it unless you have a compelling reason.  It's messy and it defeats one of the purposes of a VM, which is to make things portable.  When I was referring to LVM or logical volumes that was strictly for your host OS, i.e. Linux.  In other words, if you use LVM rather than standard partitions in Linux, you have the ability to reallocate drive space as needed for new image files.  It's used on servers a lot, but it's good for workstations too. My disks are divided into LVM volumes - I do not use regular partitions, except for booting.  I store my KVM images in a folder in /usr/local which is an LVM on a separate physical hard drive from the OS, but you can set it up in whatever way you think best.  The actual layout doesn't matter as long as you have the space and the drive is accessible.

As for the rest of the adventure, using a KVM, it is far, far easier than you think. 

Please forgive me if this is too simplistic, but I do not know your skill-set. First bit of information that you should know is that the software that runs a VM is called a hypervisor.  It provides the virtual hardware that the guest runs on.  There are two kinds: Type 1 and Type 2.  Type 2 are ones that run on top of an OS, like VirtualBox.  Because they are controlled in the host operating system's userspace, just like any other user program, they are not very efficient.  Type 1 hypervisors run inside or underneath the host OS itself, and are far more efficient than a regular user program, because they have more direct access to the hardware.  KVM or Hyper-V are examples of a Type 1 hypervisor.

I personally prefer to work with the command line, but you can use the virt-manager GUI if you want.  I use a shell script to start my virtual machines rather than a GUI, but the choice is yours.  It's more a matter of personal taste than necessity. I'm posting the script so you can use it for inspiration if you want, but please look everything up before you attempt to actually use it for something.  It's not fault tolerant and it requires having bound a card to VFIO.


 ```

#!/bin/bash



zenity --question --text "Release Right Monitor"  --title "System"


if [ $? -eq 0 ] ; then
 xrandr --output DVI-0 --off
fi;




gksu -S -g --description "Windows 7" \
"/usr/bin/qemu-system-x86_64 -enable-kvm -m 8192 -cpu host,kvm=off \
-smp 3,sockets=1,cores=3,threads=1 \
-machine q35,accel=kvm \
-device qxl \
-usb \
-device usb-mouse \
-device usb-kbd \
-soundhw hda \
-bios /usr/share/seabios/bios.bin -vga none \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=04:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on \
-device vfio-pci,host=04:00.1,bus=root.1,addr=00.1 \
-device virtio-blk-pci,scsi=off,addr=0x7,drive=drive-virtio-disk0,id=virtio-disk0,bootindex=0 \
-drive file=/usr/local/VM/DevMach.img,if=none,id=drive-virtio-disk0,format=raw,media=disk \
-netdev tap,id=user.0 \
-device virtio-net-pci,netdev=user.0,mac=52:54:00:58:ba:9c \
-boot order=d \
-usbdevice host:9.2 \
-device virtio-blk-pci,scsi=off,addr=0x8,drive=drive-virtio-disk1,id=virtio-disk1 \
-drive file=/usr/local/VM/Games.img,if=none,id=drive-virtio-disk1,format=raw,media=disk \
-rtc base=localtime,driftfix=slew"


wait


xrandr  --auto --output DVI-0  --mode 1920x1080 --right-of DVI-1



```

It's a bit ugly, I grant you, but it gets the job done.  This one actually turns over my secondary GPU to the Windows virtual machine, along with my right monitor.  This gives Windows full DirectX capability as if it were running on a regular computer.  Everything works: including DirectX games, such as Fallout or Black Desert; watching videos on Vudu etc. 

 The only thing I haven't figured out yet is how to get HD such as BluRay working.  HD and HDMI requires secure pathing, and that is rather self-defeating for virtualization.  I'm thinking about getting a USB drive and experimenting to see if I can get around it that way, since you can pass an entire USB hub to the VM directly.  SD video works just fine.

---

### Post by MAFoElffen on 2016-06-01
I felt some clarifications were needed. 

First the Op was if to stored images in /root or /home... Specifically this would be a question to put into a user's home directory, in the "public" shared home directory or elsewhere in the Linux Filesystem.

For VirtualBox, which is s userspace type 2 hypervisor application, the program default is to configure that the VM guest images are to be found in the user's home directory, and to be accessed by that user without elevated (sudoer/wheel) permissions. You would have to manually changed that to be any different than that.

This gets more into a theme privileged or unprivileged access.
- - - -
This could be cleared up further by asking if a VM guest needs to be shared by anyone besides the main user? If so, then it needs to be somewhere else than in a user directory, or at least shared with that other user. That has to do with "privileges" and permissions.

Next question would be that if a user is not the only user in an environment that includes VM Guests, does each user need the rights and privileges to be able to start/stop, and/or makes changes to a VM Guest or just need acess to that VM Guest? If the user is the only user in that environment, then much of the where and how it is implemented does not matter. The lone user is the environment administrator.

Just thought I might throw those in to clarify a few things. Hope that helps. (Good info so far...)

---

