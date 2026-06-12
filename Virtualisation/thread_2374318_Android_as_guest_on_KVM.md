---
title: "Android as guest on KVM"
date: 2017-10-14
forum: Virtualisation
---

### Post by satimis on 2017-10-14
Hi all,

Does KVM support Android running as guest ?

On following URL
[https://www.linux-kvm.org/page/Guest_Support_Status#Android](https://www.linux-kvm.org/page/Guest_Support_Status#Android)
guest Android 2.2

The latest Android version is Android 8.0 Oreo (API 26)

I'm now running Android-x86-6.0-r2-02 on VM of VirtualBox.  It works but certain features are missing, such as the basic feature copy-n-paste.  The mouse pointer freezes frequently.  I have been informed by Oracle VirtualBox Forum that they won't support Android.

I'm prepared to test Android as guest on KVM with Ubuntu 16.04 as host.  Please shed me some light.  Thanks

Regards
satimis

---

### Post by KillerKelvUK on 2017-10-14
Hey, have you been here yet? 

[http://www.android-x86.org/](http://www.android-x86.org/)

They have a section on running as a qemu guest although they only track upto Android 7.1 at present but you may be able to locate a nightly build or similar if you poke around.

---

### Post by satimis on 2017-10-14
> **KillerKelvUK said:**
> Hey, have you been here yet? 

[http://www.android-x86.org/](http://www.android-x86.org/)

They have a section on running as a qemu guest although they only track upto Android 7.1 at present but you may be able to locate a nightly build or similar if you poke around.
Hi,

Thanks for your advice and link.

I read;
Android-x86 Open Source Project Announcement
Android-x86 Project - Run Android on Your PC

I have no idea whether the packages there are for physical PC or for running on VM of VirtualBox or for running as guest of KVM

I have download 64-bit ISO:  android-x86_64-7.1-rc2.iso
and tried installing it on VM.  But failed unable to install.

-> Settings -> Storage
the image android-x86-7.1-rc2.vdi
is automatically created under;
Attributes
Name: IDE (controller)
Type: PIIX4

NOT
Attributes
Name: SATA (controller)
Type: AHCI

---

### Post by KillerKelvUK on 2017-10-15
> [COLOR=#000000]I have no idea whether the packages there are for physical PC or for running on VM of VirtualBox or for running as guest of KVM[/COLOR]

So the answer is both as it they should work if you want to install it as the main OS on your PC or if you want to run it as a virtual machine.  If you want to run as a VM then you have a choice of hypervisors e.g. VirtualBox, KVM/Qemu, Xen, VMware blah blah, as long as the hypervisor emulates x86 architecture you should be good.  The complicating bit might be getting the correct VM configuration for compatible emulated hard.

> [COLOR=#000000]and tried installing it on VM. But failed unable to install.[/COLOR]

When you started the VM in VirtualBox did it boot from the Android .iso?  You should have seen a boot menu etc, did you get that far?

I'm downloading the same image now to test but my setup is with KVM/Qemu but there should be enough similarities to help you with Virtualbox.

---

### Post by satimis on 2017-10-15
> **KillerKelvUK said:**
> So the answer is both as it they should work if you want to install it as the main OS on your PC or if you want to run it as a virtual machine.  If you want to run as a VM then you have a choice of hypervisors e.g. VirtualBox, KVM/Qemu, Xen, VMware blah blah, as long as the hypervisor emulates x86 architecture you should be good.  The complicating bit might be getting the correct VM configuration for compatible emulated hard.



When you started the VM in VirtualBox did it boot from the Android .iso?  You should have seen a boot menu etc, did you get that far?

I'm downloading the same image now to test but my setup is with KVM/Qemu but there should be enough similarities to help you with Virtualbox.

Hi,

I have tried several hours without a breakthrough.  It is very strange to me.  On creating a new VM for installing android-x86_64-7.1-rc2 it always automatically connect the .vdi image to IDE controller NOT SATA


Please forget this test installing android-x86_64-7.1-rc2 on VM of VirtualBox

Tomorrow I'll purchase;
a 256G SSD for running the OS and installing qemu-kvm and libvirt
a 2TB WD Gold label 7,200 rpm HD for installing the guests of KVM

This is a 8-core AMD PC with 32G RAM onboard

The document to follow will be;
Ubuntu 16.04: Install KVM and run virtual machine
[https://www.hiroom2.com/2016/07/11/ubuntu-16-04-install-kvm-and-run-virtual-machine/#sec-1](https://www.hiroom2.com/2016/07/11/ubuntu-16-04-install-kvm-and-run-virtual-machine/#sec-1)

After KVM is running I'll install android-x86_64-7.1-rc2 on its guest

Regards
satimis

---

### Post by KillerKelvUK on 2017-10-15
Okay, well I've just tested this in KVM/Qemu and booting from the .iso with the default guest configurations (using virt-manager) worked first time i.e. boot menu off the .iso and was able to load the live android OS.

NOTE:  I didn't create a hard disk for the VM as I just used the LIVE CD feature of the android distro.

---

### Post by satimis on 2017-10-17
> **KillerKelvUK said:**
> Okay, well I've just tested this in KVM/Qemu and booting from the .iso with the default guest configurations (using virt-manager) worked first time i.e. boot menu off the .iso and was able to load the live android OS.

NOTE:  I didn't create a hard disk for the VM as I just used the LIVE CD feature of the android distro.

Hi,

Yes, Android works on Live CD but I can't install it on VM.  If connecting .vdi to IDE controller the installation took long time without ending.  If connecting .vdi to SATA controller, it offered lot of options to select, finally saying the device not mounted.

Now I have purchased```

A SanDisk Ultra 3D 2.5" 250GB SATA III 3D NAND Internal Solid State Drive (SSD)   SDSSDH3-250G-G25    SATA3 6Gb/s
Sequential read speeds of up to 560 MB/s;
sequential write speeds of up to 530 MB/s 

A WD Gold WD2005VBYZ
2TB SATA3 6Gb/s /128MB Datacenter  7,200rpm
7x24 HDD

```

My daily working PC has been running >5 years.

Existing Configuration
=================
CPU - AMD 8-cores
RAM - 32G
Mobo
&#10219; sudo dmidecode -t 2```

# dmidecode 3.0
Getting SMBIOS data from sysfs.
SMBIOS 2.7 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
        Manufacturer: ASUSTeK COMPUTER INC.
        Product Name: M5A97 LE R2.0
        Version: Rev 1.xx
        Serial Number: 141235722500456
        Asset Tag: To be filled by O.E.M.
        Features:
                Board is a hosting board
                Board is replaceable
        Location In Chassis: To be filled by O.E.M.
        Chassis Handle: 0x0003
        Type: Motherboard
        Contained Object Handles: 0

```

1TB SSD for running Ubuntu 16.04 desktop, VirtualBox and VMs
1.5TB WD Black label spinning HD for data storage

New configuration
=============
I'm prepared running Ubuntu 16.04 desktop and KVM on the new SanDisk 250G SSD.  The new 2TB WD Gold WD2005VBYZ HD will be for storage of KVM guests and data storage.

Just checked the spec of the mobo.  It has 6 SATA3 6Gb/s ports.  I suppose it would be sufficient to install:-
1TB SSD
250G Sandisk SSD
1.5TB WD Black label HD
2TH WD Gold label HD
DVD burner

I'll use the last SATA3 port to connect my old 120G ADATA SSD for testing Android on phyical PC.  Booting will be selected on BIOS

Comment and suggestion would be welcome.  Thanks

Edit
===
Just received a reply on KVM mailing list in response to my posting about running Android on KVM.  It said "Android works on KVM but there is a problem on copy-n-paste function", similar to running Android on Virtualbox on my testing.

Regards
satimis

---

### Post by KillerKelvUK on 2017-10-18
Hey satimis, can't really comment on your storage as it is what it is.  Are you looking to apply any redundancy i.e. raid (mdadm) or use any logical volumes (lvm)...how you store your vm's is pretty important?

Regards installing Android x86 to a virtual hard disk...well i've done three attempts now using KVM/Qemu all with the .iso mounted on a Qemu SATA bus and the virtual disk image connected to a virtio or sata bus.  All installations seemingly worked however when the guest reboots at the end of the process I get stuck on a "Booting from Hard Disk..." message from SeaBIOS.  Not sure what's causing this, thinking a mix of disk bus type, partition label and/or file system selected.  I don't have the time now to debug further but you might find a winning combination and let me know :-)  Keep us posted in this thread and I'll get back to it over the coming weekend.

Cheers,

K

---

### Post by satimis on 2017-10-19
> **KillerKelvUK said:**
> Hey satimis, can't really comment on your storage as it is what it is.  Are you looking to apply any redundancy i.e. raid (mdadm) or use any logical volumes (lvm)...how you store your vm's is pretty important?
- snip -

Hi K,

I have finished installing the new SanDisk SSD and the new 2TB WD Gold 7,200 rpm HD on the box.  Also I have installed Ubuntu 16.04 desktop on SandDisk SSD.  Ubuntu 16.04 desktop is now running w/o problem, update and upgrade also without problem.

My planning for SanDisk SSD and HDs setup on the box is as follows;
1TB SSD for running VirtualBox with Ubuntu 16.04 desktop as host.  All VMs are stored on it.

250G SanDisk SSD, paired with 2TB WD Gold HD, for running KVM and host, with guests installed on WD Gold HD.  The data of 1TB SSD is also stored on the latter.

1.5TB WD Black label HD is solely for data storage, working data backup for the 1TB SSD and 250G SanDisk SSD as well.

On moving approx 140 G data from 1TB SSD to 2TB WD Gold HD it took lengthy time to finish.  The transferring speed dropped form approx. 350MB/s to 25MB/s.  I don't know why?  I could do nothing on it, only sitting and waiting.  Have you got any advice?

Thanks.

I'll start installing KVM later when having time.

Regards
satimis

---

### Post by KillerKelvUK on 2017-10-19
Just remembered something...KVM and Virtualbox on the same host don't play well together, you may want to investigate this before you try to deploy.

---

### Post by satimis on 2017-10-19
> **KillerKelvUK said:**
> Just remembered something...KVM and Virtualbox on the same host don't play well together, you may want to investigate this before you try to deploy.
No.  They are NOT on the same host.

KVM is on 250G SanDisk SSD

VituralBox is on 1TB SSD

They are NOT running at the same time

satimis

---

