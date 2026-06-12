---
title: "New fatal VirtualBox error in Ubuntu 20.10"
date: 2020-10-27
forum: Virtualisation
---

### Post by linuxreallyrocks on 2020-10-27
[INDENT]sudo /sbin/vboxconfig
vboxdrv.sh: Stopping VirtualBox services.
vboxdrv.sh: Starting VirtualBox services.
**vboxdrv.sh: failed: Running VirtualBox in a Xen environment is not supported.**

There were problems setting up VirtualBox.  To re-start the set-up process, run
  /sbin/vboxconfig
as root.  If your system is using EFI Secure Boot you may need to sign the
kernel modules (vboxdrv, vboxnetflt, vboxnetadp, vboxpci) before you can load
them. Please see your Linux system's documentation for more information.
[/INDENT]

I'm simply running Ubuntu 20.10 on real hardware, not a Xen virtual machine. VirtualBox was working fine, but just today it has decided that it's in a Xen environment and refuses to start up. I was using the 6.1.16 release from the VirtualBox site and have now tried the repo version and the latest test build, all to no avail.

I need this dumb thing working and can hardly believe that it is having this ridiculous problem. Why does it think I'm using Xen when I'm not? What can I do with Ubuntu or VirtualBox to get this working? :mad:

---

### Post by linuxreallyrocks on 2020-10-27
Wow. Well, so much for Ubuntu. It managed to hose VirtualBox and Thunderbird in one morning.

---

### Post by ActionParsnip on 2020-10-27
What is the output of
```

sudo dmidecode -t 1

```

Thanks

---

### Post by linuxreallyrocks on 2020-10-27
> **ActionParsnip said:**
> What is the output of
```

sudo dmidecode -t 1

```

Thanks

Getting SMBIOS data from sysfs.
SMBIOS 2.8 present.

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: Micro-Star International Co., Ltd.
    Product Name: MS-7C56
    Version: 1.0
    Serial Number: To be filled by O.E.M.
    UUID: 9d45836d-0618-6e1d-ab4f-2cf05d603cc3
    Wake-up Type: Power Switch
    SKU Number: To be filled by O.E.M.
    Family: To be filled by O.E.M.

---

### Post by dragonfly41 on 2020-10-27
Recently I started exploring KVM with the aim of emulating IBM Power on KVM (I read an article).
I have only installed KVM so far and cannot comment further . but could KVM work for you?

[https://www.linuxtechi.com/install-kvm-on-ubuntu-20-04-lts-server/](https://www.linuxtechi.com/install-kvm-on-ubuntu-20-04-lts-server/)

---

### Post by linuxreallyrocks on 2020-10-27
> **dragonfly41 said:**
> Recently I started exploring KVM with the aim of emulating IBM Power on KVM (I read an article).
I have only installed KVM so far and cannot comment further . but could KVM work for you?

[https://www.linuxtechi.com/install-kvm-on-ubuntu-20-04-lts-server/](https://www.linuxtechi.com/install-kvm-on-ubuntu-20-04-lts-server/)

It would depend on how well I could transition my Windows 10 and Windows 7 VMs from VBox, and also on how well sharing files between host and guest works. I did not have a good experience with the latter when I looked into it some months back.

Anyway, I think an update to Ubuntu today caused the breakage. Since Fedora 33 is out now and I have had generally good experiences with Fedora, I've installed that on this system while I've been doing my work on my laptop instead. I suppose if no major issues crop up, I'll be sticking with Fedora. Otherwise, I don't know. Might have to look at Pop!_OS again whenever it finally gets updated to the Ubuntu 20.10 code base. I want a more recent kernel than 5.4.x since I use AMD hardware.

---

### Post by wildmanne39 on 2020-10-27
*Thread moved to **Virtualisation for a more appropriate fit**.*

I know this is not going to solve your issue but there is not a release of Virtualbox yet for 20.10 since it has only been out a few days, there is always a lag when a new version of Ubuntu comes out and that may very well be why you are having this issue, also the releases that end in .10 like 20.10 does is not meant to be installed on a production machine they are still technically being tested even though they have been released, it is always best for a production machine to use an LTS version of Ubuntu preferably one that has has the first point release.

Have you checked to see if the following is the issue,  every time I install virtualbox I have to disable secure boot because it is a hassle for me to sign the key, I have done it a couple of times though but I was having issues with my old laptop and I had to keep resigning the key so I just started disabling secure boot instead.
> There were problems setting up VirtualBox. To re-start the set-up process, run
/sbin/vboxconfig
as root. If your system is using EFI Secure Boot you may need to sign the
kernel modules (vboxdrv, vboxnetflt, vboxnetadp, vboxpci) before you can load
them. Please see your Linux system's documentation for more information.

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by linuxreallyrocks on 2020-10-27
> **wildmanne39 said:**
> *Thread moved to **Virtualisation for a more appropriate fit**.*

I know this is not going to solve your issue but there is not a release of Virtualbox yet for 20.10 since it has only been out a few days, there is always a lag when a new version of Ubuntu comes out and that may very well be why you are having this issue, also the releases that end in .10 like 20.10 does is not meant to be installed on a production machine they are still technically being tested even though they have been released, it is always best for a production machine to use an LTS version of Ubuntu preferably one that has has the first point release.

Have you checked to see if the following is the issue,  every time I install virtualbox I have to disable secure boot because it is a hassle for me to sign the key, I have done it a couple of times though but I was having issues with my old laptop and I had to keep resigning the key so I just started disabling secure boot instead.


[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

It was fine before I applied system updates this morning and in the days, months and years previous, so of course it has nothing to do with secure boot, which I also know I am not using. It's still working on the laptop, where I have not applied those updates.

Now, while there is not technically a VirtualBox release for Ubuntu 20.10 as of yet, the one I was using was working until those system updates were applied. Something odd happened that now has VirtualBox thinking that a regular system is a Xen environment. Even a test build of VirtualBox had this issue, which tells me it is due to that update I installed.

Also, again, I upgraded to get the new kernel. LTS releases sit on very old versions for a very long time, but kernel 5.8 has some significant improvements that I wanted to take advantage of.

---

### Post by ajgreeny on 2020-10-27
You should be able to convert your VBox vdi VMs to the KVM qcow2 format quite easily with a couple of commands.

First you need to export the vdi from VBox as an ova, then extract the ova to the two files it contains, with ```
tar -xvf filename.ova
```
You then need to convert the vmdk from the extracted ova with ```
qemu-img convert name.vmdk name.qcow2 -O qcow2]
```
and finally use that qcow2 file as the file to import when you start a new VM in KVM using virt-manager.

I moved a couple of months ago from VBox to KVM and I am amazed at the performance of KVM; it is so much faster, smoother, and needs no guest-additions, you simply use ssh to share any files between host and guest.  All my KVM VMs were converted from VBox in this way and all have performed faultlessly so it must be worth you trying this way if you are really wanting to use KVM

See these for info that might help more.
[https://access.redhat.com/discussions/4340061](https://access.redhat.com/discussions/4340061)
[https://www.linux.com/audience/devops/creating-virtual-machines-kvm-part-1/](https://www.linux.com/audience/devops/creating-virtual-machines-kvm-part-1/)
[https://dev.to/guinuxbr/convert-ova-to-qcow2-48f2](https://dev.to/guinuxbr/convert-ova-to-qcow2-48f2) (as you have VMs of Windows already this one may not be appropriate as it uses the ova files available from Microsoft which are only usable for 90 days.

---

### Post by linuxreallyrocks on 2020-10-30
> **ajgreeny said:**
> You should be able to convert your VBox vdi VMs to the KVM qcow2 format quite easily with a couple of commands.

First you need to export the vdi from VBox as an ova, then extract the ova to the two files it contains, with ```
tar -xvf filename.ova
```
You then need to convert the vmdk from the extracted ova with ```
qemu-img convert name.vmdk name.qcow2 -O qcow2]
```
and finally use that qcow2 file as the file to import when you start a new VM in KVM using virt-manager.

I moved a couple of months ago from VBox to KVM and I am amazed at the performance of KVM; it is so much faster, smoother, and needs no guest-additions, you simply use ssh to share any files between host and guest.  All my KVM VMs were converted from VBox in this way and all have performed faultlessly so it must be worth you trying this way if you are really wanting to use KVM

See these for info that might help more.
[https://access.redhat.com/discussions/4340061](https://access.redhat.com/discussions/4340061)
[https://www.linux.com/audience/devops/creating-virtual-machines-kvm-part-1/](https://www.linux.com/audience/devops/creating-virtual-machines-kvm-part-1/)
[https://dev.to/guinuxbr/convert-ova-to-qcow2-48f2](https://dev.to/guinuxbr/convert-ova-to-qcow2-48f2) (as you have VMs of Windows already this one may not be appropriate as it uses the ova files available from Microsoft which are only usable for 90 days.

When I tried it before, I think I skipped converting the image format. I tend to use VMDK images for my VBox VMs, and that format also seems to work fine with QEMU.

Having SSH work is the big thing. Now that you've posted this helpful info, I'll have another look at making the switch. Thanks.

---

