---
title: "enable IOMMU support for KVM"
date: 2011-08-04
forum: Server Platforms
---

### Post by C0dR on 2011-08-04
Hi,
first, sorry for my bad english, I am german :D
I have a problem enabling IOMMU on my MSI 970A-G45 mainboard. I need the IOMMU support for PCI passthrough in KVM ( I need my DVB pci cards in the virtual machine).
I have installed Ubuntu server 11.04 and enabled IOMMU in bios.
The first strange thing is, that when iommu is enabled in the bios i cant access network or USB devices in ubuntu. Only when its disabled in bios.

Well, i tried the tutorial from here: [http://www.linux-kvm.org/page/How_to_assign_devices_with_VT-d_in_KVM](http://www.linux-kvm.org/page/How_to_assign_devices_with_VT-d_in_KVM) and compiled a new kernel with *"Support for DMA Remapping Devices", "Enable DMA Remapping Devices" and "PCI Stub driver"* enabled and installed it (based on description in wiki)

But the command 
```

dmesg | grep AMD-Vi

```
does not pop out anything. So I tied to add the command "iommu=pt iommu=1" to grub and now i have a kernel panic while booting :evil:
```

Kernel Panic - not syncing: Cannot allocate iommu bitmap

```

i dont know what to do....I cant even boot my ubuntu server anymore :(
can anyone tell me how to enable IOMMU support on ubuntu?

greets
C0dR

---

### Post by k3v1n on 2011-08-06
I'm working on the same issue. I have an ASUS M5A97 and Ubuntu Server 11.04. Libvirtd (Virtual Machine Manager) worked beautifully, but I have ran into issues with enabling IOMMU and passing a physical device through (have tried NICs, USB hubs, Video Cards, and a TV Tuner). Like your system, mine does not let me use USB or NIC devices when IOMMU is enabled in the BIOS; however, a PS2 keyboard still functions. I have looked for tutorials, but cannot find one (other than what you linked to) to explain how to do this. I reinstalled US 11.04, without the GUI this time, but the same issue arises. 
I looked into Xen, but cannot find a good tutorial for that either. 
Maybe my google skills are infected?!

Please post anything that you find. I'll do the same.

---

### Post by C0dR on 2011-08-06
i havent found something yet :(
to boot i had to reinstall my ubuntu, but i still cant use iommu :evil:
I have the feeling that no one is using iommu. there is nothing on the internet about using it with ubuntu....only this only tutorial from kvm.
I'll report you as soon as I find something.

---

### Post by k3v1n on 2011-08-06
I was asking in the kvm IRC channel; the people there said they had set it up before but would only point to the link you had posted as a tutorial (which, IMHO is a weak guide). I'm working on following that guide, but it confuses me. I have not yet been able to figure out how to run the first line 'make menuconfig'. We'll figure this out; it'll just be a slow (I've already spent a month) process. However, I'm sure it's possible.

---

### Post by C0dR on 2011-08-06
Well, the description is very simplified...
u first have to get the source code from the linux kernel:

```
sudo apt-get build-dep --no-install-recommends linux-image-$(uname -r) 
```

and then some tools for compiling:

```
sudo apt-get install fakeroot build-essential kernel-package libncurses5-dev
```

now go to a directory you want (for example your home):
```

cd ~

```

now get the linux source code files:
```

apt-get source linux-image-$(uname -r) 

```

and now we have to get into the source directory (version could be other than mine, just lookup the folder with 'ls'):
```

cd linux-2.6.32

```

now you are ready to follow the guide. (make menuconfig etc)


But its useless for me because I cant even get IOMMU working....

---

### Post by k3v1n on 2011-08-07
I followed your instructions. (thank you for those). Now I'm getting the Kernel panic error as well. I'm reading through googles to see what I can find. A lot of people have had this issue, although for other reasons. Will post my findings.

---

### Post by C0dR on 2011-08-08
no problem.
I ordered a real server mainboard today (asus p7F-x with Intel X3430). when it arrives I will try it with vt-d (its the same as AMDs IOMMU).
Maybe its a desktop chipset problem, because some people mentioned problems with desktop mainboards, although they have iommu.
I will report you as soon as possible.

---

### Post by C0dR on 2011-08-10
WoW!
It works. No problems, no usb/network disabling when iommu is enabled!
Just f*** the desktop mainboards.
Buy a Asus P7F-X, its not really expensive (165€) and it worked for me. None of the desktop mainboards i tried worked...

It seems that the desktop chipsets does not really support iommu or something. I hope this statement will help you.


My Settings now are:

Intel Xeon X3430
Asus P7F-X
G.Skill DDR3-1333 Ram
3x Western Digital 2TB (two of them RAID1)

---

### Post by srt4play on 2011-08-10
I use a GIGABYTE GA-890FXA-UD5 desktop board in my virtualization server and IOMMU works good, using a distribution called Proxmox. I use IOMMU to pass several NICs to different VMs.

Could you keep us updated as to the performance you get from the VM using the tuner cards?  Are you running a client/server media program like mythtv or mediaportal?  I attempted to run mediaportal in a Win7 VM with tuner cards passed via IOMMU, it worked but performance was not good. I think disk I/O performance was the problem.

---

### Post by C0dR on 2011-08-10
Well, the 890FX chipset might be a better one than the 970. I heard that the FX are supporting IOMMU better (but was a bit too expencive for me :D )

I am using a windows server 2008 on the VM with DVBServer and 3 TV Cards.
Since now it works well, I tried HD with 3 clients at the same time and it only penetrates my DLink adapters :biggrin:

I will report when problems appear or the speed breaks.
But until now, time for :popcorn: :D

---

### Post by Plecebo on 2011-10-05
I had the same kernel panic on a brand new 11.04 server install on my ASRock 890FX Deluxe4 board. 

I installed with iommu enabled in the bios and after updating etc I  executed:
```
dmesg | grep AMD-Vi
```
and got: 
```

AMD-Vi: Enabling IOMMU at 0000:00:00.2 cap 0x40
AMD-Vi: Lazy IO/TLB flushing enabled

```
in the guide it also indicates that you should get this output from the dmesg: 
```
AMD-Vi: Initialized for Passthrough Mode
```
which I did not get. 

I figured I needed to compile my kernel to fully enable/initialize passthrough, but following the instructions in this thread (to download the source) and on the linux-vim.com guide page to compile/install I also get the kernel panic on reboot. 

Anyone have any ideas how to enable AMD-Vi?

---

### Post by Robstarusa on 2012-10-17
> **Plecebo said:**
> I had the same kernel panic on a brand new 11.04 server install on my ASRock 890FX Deluxe4 board. 

I installed with iommu enabled in the bios and after updating etc I  executed:
```
dmesg | grep AMD-Vi
```
and got: 
```

AMD-Vi: Enabling IOMMU at 0000:00:00.2 cap 0x40
AMD-Vi: Lazy IO/TLB flushing enabled

```
in the guide it also indicates that you should get this output from the dmesg: 
```
AMD-Vi: Initialized for Passthrough Mode
```
which I did not get. 

I figured I needed to compile my kernel to fully enable/initialize passthrough, but following the instructions in this thread (to download the source) and on the linux-vim.com guide page to compile/install I also get the kernel panic on reboot. 

Anyone have any ideas how to enable AMD-Vi?

I have the same board & same issue.

This is how I solved it (in 12.10 beta...perhaps 11.10 is the same?)

open /etc/default/grub with your favorite editor
edit GRUB_CMDLINE_LINUX="" and replace "" with:
GRUB_CMDLINE_LINUX="iommu=pt iommu=1" 

if GRUB_CMDLINE_LINUX has something in it, just tag this on the end.

Save the file

run "update-grub" 

reboot.

Now as far as getting IOMMU working (I'm trying with KVM), I haven't gotten that working yet, but when I do I'll post an update.

---

