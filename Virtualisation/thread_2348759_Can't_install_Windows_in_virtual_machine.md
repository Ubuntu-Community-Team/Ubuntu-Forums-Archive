---
title: "Can't install Windows in virtual machine"
date: 2017-01-07
forum: Virtualisation
---

### Post by steve169 on 2017-01-07
I'm running Ubuntu 16.04.1 on my Dell Inspiron 660 desktop's solid state drive. 

I've installed the KVM virtual machine and Virtual Machine Manager on the same drive as Ubuntu.

On one of my hard drives I have Windows 7 Pro. I want to clone it and all its applications to the virtual machine. (My data files are on different drives.)

I tried  to make an ISO file of the entire Windows drive.  But all my attempts to create an ISO have failed. Is there another way to go?

I have offered Virtual Machine Manager the thumb drive Dell provided for reinstalling Windows 7. But the manager immediately rejects the thumb drive, saying it is not bootable. (It is. I've tested it. It does not, however, contain the usual setup.exe file.)

My goal is to transfer my entire Windows installation to the virtual machine, then always run it from there.

Any suggestions for this newbie?

---

### Post by wildmanne39 on 2017-01-07
*Thread moved to **Virtualisation**.*

---

### Post by TheFu on 2017-01-07
When Windows installs, it looks at all parts of the hardware it is running on. This gets tied to the installation.

When you run **any** VM under **any** virtual machine technology, the hypervisor provides virtual hardware that will never match what any real machine has inside it.  Therefore, the only way to move a Windows install into a VM is to put Windows into a mode where it expects to be moved to new hardware. Think this is called "sysprep."  Microsoft limits the number of times this method can be used for each license.  I've had to do it to switch between versions of KVM because there were so many changes that the HW presented to guests OSes completely changed.  After you put it into sysprep, then you can clone the storage however you want (within the supported KVM disk storage methods)  and import that into a KVM VM settings.

This only works with enterprise licenses or retail copies of Windows.  Pre-installed Windows won't work, as they are not only tied to the hardware, but they look for specific hardware as part of their OEM signature.  

If you don't have a retail version of Windows, forgetaboutit.

Also, don't confuse what the hostOS sees with what the guestOS sees. Those have NOTHING to do with each other.  That fast GPU?  Doesn't matter.  That wifi card or other NIC?  Doesn't matter.  All the hardware presented to every guest OS is virtual-hardware.  The same applies to USB devices.

A few people have setup passthru for different devices.  This requires something called VT-d to be supported by your hardware AND enabled in the BIOS AND enabled in the running kernel.  I've only done it for NICs and disks.  Other people here with multiple GPUs have assigned 1 to their Windows VM and the other to Linux.  However, getting that to work has even more specific details that need to be followed exactly.

So ... does that help?

---

### Post by steve169 on 2017-01-07
I do have an old version of Windows 7 Pro, both 32- and 64-bit, that has an activation code. Which one should I use?

I've used Virtual Machine Manager to create a virtual machine and start the installation disk. But the install consistently freezes once it reaches the opening Windows logo page.

I have done nothing to my BIOS. Do I need to adjust something there?

---

### Post by TheFu on 2017-01-07
Are they retail versions? That is the one you should use. If it isn't a retail version, then it is most probably an OEM version.  Having an activation code is a separate issue.

Inside a VM, you don't have any control over the BIOS, just the HW provided to the VM.  The physical BIOS means nothing, as stated above.  An OEM version of Windows will look for the BIOS for the machine it was sold to run on. The VM will not provide that BIOS, so it won't run.

Or am I missing something?

---

### Post by steve169 on 2017-01-12
Dear Fu,
'
'I found an old version of Windows 2000 Pro, and it installed. Joy of joys!

I can live with Windows 2000. But is there any way I can copy my Windows 7 installation, which is on a different hard drive, into the virtual machine?

---

### Post by TheFu on 2017-01-12
Sure, you can copy data from a HDD into a VM, but that isn't really your question, is it?
You haven't answered any questions that I've asked. Without relevant data, impossible to answer.

Your questions really have more to do with microsoft licensing than virtualization. Hopefully, you are asking microsoft.

---

### Post by SeijiSensei on 2017-01-13
I've never used KVM, but in VirtualBox you can create "shared folders" that let you access filesystems on the host machine.  I have Linux mount the Windows partition on my multi-boot machine to /windows, then share that directory with my Win 7 guest running in a VM.  That will give you access to files like those in your C:\Users directory.  But I don't think there's any way you can, say, run a copy of Microsoft Word on the host machine inside the guest.  You need to install everything you want to use in the VM from scratch.

---

### Post by ODTech on 2017-01-19
> **steve169 said:**
> I do have an old version of Windows 7 Pro, both 32- and 64-bit, that has an activation code. Which one should I use?

I've used Virtual Machine Manager to create a virtual machine and start the installation disk. But the install consistently freezes once it reaches the opening Windows logo page.

I have done nothing to my BIOS. Do I need to adjust something there?

You need to enable to Vt-d and or Virtualization in your bios before you can install a 64bit OS. The reason Win 2000 loaded is because it is 32 bit.
Open your bios and turn on Vt-d and Virtualization. Vt-d is the important one so don't worry if you don't see/have the other.

As for your hard drive issue, i suggest using virtualbox or vmware to make things easier.

VMWare
If you can boot the old windows 7 then it's very easy to convert to a VM.
[http://www.softpedia.com/get/System/System-Miscellaneous/VMware-Converter.shtml](http://www.softpedia.com/get/System/System-Miscellaneous/VMware-Converter.shtml)
Install it on the live running windows installation and tell it to convert it to a VM. You need external storage for the data to copy to. 
VMWare has a Linux client so simply install it and open the VM. From past experience this process is very reliable.


Virtualbox/KVM
Connect the drive to a linux box or laptop and do the following.

Identify the win7 drive
```
sudo fdisk -l
```
Create a raw image of the entire drive. It doesn't give you progress bar so just leave it until it's finished. The x in /dev/sdx is replaced with the letter you identified with the fdisk command.
```
sudo dd if=/dev/sdx of=/home/youruser/newfile.bin bs=1m conv=noerror,sync
```
At this stage you can try to attach the raw image to a KVM VM and see if it will boot. KVM does work with raw files. Or you can move on to the next step and try with Virtualbox.
```
VBoxManage convertdd /home/youruser/newfile.bin /home/youruser/newfile.vdi --format VDI
```
Now just create a VM around the VDI file and hope for the best. If it won't boot right away remember to tweak the settings, there's not many but in past experience they sometimes help to get a converted OS to start up.

Licensing might be an issue as stated in above post but with newer Microsoft OS's they give you an option to go online and buy a new license or type a different product key. Maybe not so much the case with windows 7 but if you can get it to boot maybe it's a good time to upgrade to windows 10.

Hope above helps, post back if you have questions. 

A little bit off topic but just to set the record straight.
TheFu claimed a VM can never see your computers true physical hardware which is false. KVM can do pci passthrough and so can VMWare Esxi. I actualy just finished setting up my Ubuntu 14.04 host with a kvm vm running windows 10 today. My GTX670, wireless kb/mouse dongle and a pci-e sata controller is passed through directly to the windows 10 VM. Gaming performance is exactly as it would be on a physical machine.

---

### Post by ODTech on 2017-01-20
> **ODTech said:**
> You need to enable to Vt-d and or Virtualization in your bios before you can install a 64bit OS. The reason Win 2000 loaded is because it is 32 bit.
Open your bios and turn on Vt-d and Virtualization. Vt-d is the important one so don't worry if you don't see/have the other.

Just correcting myself. VT-d is for device passthrough so not important in your case. Virtualization or otherwise called Vt-x is what you need to enable to run a 64 bit VM.

---

### Post by TheFu on 2017-01-28
> **ODTech said:**
>  ....

A little bit off topic but just to set the record straight.
TheFu claimed a VM can never see your computers true physical hardware which is false. KVM can do pci passthrough and so can VMWare Esxi. I actualy just finished setting up my Ubuntu 14.04 host with a kvm vm running windows 10 today. My GTX670, wireless kb/mouse dongle and a pci-e sata controller is passed through directly to the windows 10 VM. Gaming performance is exactly as it would be on a physical machine.

Getting specific addon-HW to passthru is NOT what this was about. He needs the motherboard model and specific vendor BIOS to be passed thru if he has pre-installed Windows versions.  That will not happen - I've never seen any method to that. 

Getting a NIC or SATA control to pass thru isn't THAT hard, if vt-d is enabled by the BIOS and in the kernel.  Video card passthru has become easier the last few years, but it has been tied to specific cards that only gamers would own. Plus only systems with 2 GPUs need apply.
[B]
None of that will help the OP if he doesn't have a source disk that isn't tied to a specific vendor's hardware.[/B] The OP has never answered that question.  Running an unsupported OS isn't the smartest thing, unless the networking is disabled or extremely locked down.

---

