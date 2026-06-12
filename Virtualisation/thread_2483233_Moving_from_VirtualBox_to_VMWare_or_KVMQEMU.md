---
title: "Moving from VirtualBox to VMWare or KVM/QEMU"
date: 2023-01-23
forum: Virtualisation
---

### Post by oygle on 2023-01-23
I've been using VirtualBox Version 7.0.4 r154605 (Qt5.15.3) for a few months , with Win 10 pro as the guest. Performance is terrible, and the laptop, albeit a few years old, is quite powerful. It does seem to have become worse re resources/performance when I went from Win 8.1 to win 10 pro though. Anyway I want to try VMWare

Rather than install/setup Qemu/VMWare and then jump through all the hoops with installing and updating Windows 10 Pro again, the guide at [https://www.howtogeek.com/125640/how-to-convert-virtual-machines-between-virtualbox-and-vmware/](https://www.howtogeek.com/125640/how-to-convert-virtual-machines-between-virtualbox-and-vmware/) seems to suggest I can basically export in VirtualBox and then import in VMWare.

Is the article correct ? Any gotchas at all or other surprises and things to be aware of ?  The VM file now is about 40 Gb. I looked at and started a test 'export' for a few minutes; no issues. The export appliance dialogue has  

> 
The Open Virtualization Format supports only ovf or ova extensions. If you use the ovf extension, several files will be written separately. If you use the ova extension, all the files will be combined into one Open Virtualization Format archive.

The Oracle Cloud Infrastructure format supports exporting to remote cloud servers only. Main virtual disk of each selected machine will be uploaded to remote server.


Should I use OVF or OVA ? The format is set to "Open Virtualization Format 1.0" ; is that the correct format for importing in VMWare ?  There are settings there for :

MAC Address policy
Include ISO image files

should the MAC be as per the default setting and do I include ISO image files ?  Hopefully the file/s expoted can easily be imported into VMWare.

---

### Post by TheFu on 2023-01-23
VMware makes 6 virtualization products.  You'll need to be more specific.

BTW, if your host is Linux, why not use the hypervisor that Amazon, Linode, and about 1000 other cloud server providers around the world use?  It's built into the kernel, F/LOSS, and extremely stable.  We switched off both VMware enterprise tools AND all the typical desktop hypervisors from 2010-2012 to use KVM/QEMU on Linux.  Even today, we are happy with that choice, which is not what we experienced with any of the others.  When you are done playing with toys, come over to KVM/QEMU.  There's a nice GUI for it that is very similar to what vbox provides, just with much more flexibility. For example, I manage my VM hosts from my workstation over an ssh control channel while running VMM on my workstation.  Completely secure.  I can here the gasps with me admitting to using any GUI tool, since I'm almost 100% shell Linux user.  VMM - aka virt-manager. [https://virt-manager.org/](https://virt-manager.org/)

I'm fairly certain that moving a Windows VM between different hypervisors will require doing a fresh install, if MSFT thinks the motherboard has changed.  OTOH, I've moved my KVM hosted WinXP and Win7 VMs across no less than 3 different physical machines and perhaps 5 Ubuntu OSes without needing to tell Windows anything.  The same motherboard is emulated, so MSFT thinks those OS installs are on the same hardware - though  instead of being on a 2008 Core2 Duo, they are running on Ryzen 5xxx CPUs today ... er ... just a wee bit faster.

KVM basically never crashes. It run stable, fast and with 100% F/LOSS.  Using QXL and SPICE, remote GUI connections are fast and secure too.

BTW, if you want to make your VM fast, there are a few tricks based on the current hardware.  An article about this: [https://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](https://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox)  The main things are storage allocations (if not on an SSD) and properly sharing the physical hardware between the hostOS and any running guests.  Often, people give the guest OSes too many CPUs and too much RAM, starving the hostOS of those resources.  If tuned correctly, every guest VM should run around 90% native install performance.

---

### Post by oygle on 2023-01-23
> **TheFu said:**
> VMware makes 6 virtualization products.  You'll need to be more specific.

Thanks for your very detailed reply. Seems my 'bad'. I assumed KVM/QEMU is the same as VMWare, but reading your reply, ... seems not. If I installed "virt-manager"  (I can see it in Synaptic), do I then install KVM/QEMU ?   Thanks  :)

---

### Post by monkeybrain20122 on 2023-01-24
If you have a vbox Windows image (vdi) you can convert it to a qcow2 (format of kvm/qemu) with a one line command and then you can just use virt-manager to create a new vm by importing the qcow2, you don't need to go through the troubles of reinstalling Windows. I have tested this with an old Windows 7 vdi and it worked like a charm.

[https://markontech.com/linux/convert-virtualbox-vms-to-qemu-kvm/](https://markontech.com/linux/convert-virtualbox-vms-to-qemu-kvm/)
[https://www.vinchin.com/en/blog/kvm-create-vm-from-qcow2.html](https://www.vinchin.com/en/blog/kvm-create-vm-from-qcow2.html)

However, kvm/qemu is optimized for Linux guests (and Linux hosts) I have an arch qvm running and it is matches native performance on a weaker machine. Cool features available for Linux guests are not available for Windows guests.For example, with vgl running games in Linux guests is actually quite smooth but this doesn't work on Windows. Sharing things between host and guest for kvm/qemu is a bit of a pita comparing to VB.

---

### Post by ajgreeny on 2023-01-24
> **monkeybrain20122 said:**
> If you have a vbox Windows image (vdi) you can convert it to a qcow2 (format of kvm/qemu) with a one line command and then you can just use virt-manager to create a new vm by importing the qcow2, you don't need to go through the troubles of reinstalling Windows. 

[https://markontech.com/linux/convert-virtualbox-vms-to-qemu-kvm/](https://markontech.com/linux/convert-virtualbox-vms-to-qemu-kvm/)
[https://www.vinchin.com/en/blog/kvm-create-vm-from-qcow2.html](https://www.vinchin.com/en/blog/kvm-create-vm-from-qcow2.html)

However, I am not sure about the performance because kvm/qemu is optimized for Linux guests (and Linux hosts) Cool features available for Linux guests are not available for Windows guests. Also to set up shared folders between host and guests for kvm/qemu is a bit of a pita comparing to VB.
The performance of Windows 10 in KVM/QEMU is very much better than it is in Vbox in my experience so I recommend the conversion mentioned by monkeybrain above which I tried simply as a test using the free enterprise version of Windows which could be downloaded in the Vbox format, though I'm not sure if it still available. 

EDIT: I've just checked and it is no longer possible to download that test version VM. As you already have a Vbox VM you would not need that step anyway,

I tried that Vbox version which did run but was so slow and unusable that I tried the conversion to qcow2; the difference was astounding and would have been very usable.

However, I no longer have that VM as I have no need for it and I'm not even sure about the license situation if you moved a licensed VM from Vbox to KVM/QEMU; I'll leave you to search that yourself as Microsoft licenses baffle me.

---

### Post by Irihapeti on 2023-01-24
You will probably have to re-activate Windows if you move it from Virtualbox to QEMU/KVM. (At least, that was my experience using Windows 10 Pro retail.) But after that, you should be set. I recently moved my VM to a completely new PC without any licence issues.

---

### Post by MAFoElffen on 2023-01-24
I beta test VMware vSphere, and I have a license... But my own daily drivers for VM Hosts, by choice is KVM/Qemu. There is just so much you can do, and for free. I can replicate various machine platforms, and run so much tp test code, app's, OS'es, etc.

I have converted VBox VM's to KVM. Is easier than exporting from VirtualBox and Importing into any VMware product.

---

### Post by TheFu on 2023-01-24
> **Irihapeti said:**
> You will probably have to re-activate Windows if you move it from Virtualbox to QEMU/KVM. (At least, that was my experience using Windows 10 Pro retail.) But after that, you should be set. I recently moved my VM to a completely new PC without any licence issues.

MSFT used to have a tool called sysprep.  I've used it.  It removes all the drivers in a Windows install, in preparation for moving to new hardware.  At the first boot, it specifically looks for new hardware and loads the drivers needed.  I don't recall any license issues moving a Windows  install using that tool, but it has been over a decade and I have trouble remembering what happened yesterday .... or anything before my afternoon nap. ;)

For my old Win7 install, I'm using a raw image file, not a compressed VDI/VDMK/qcow2 file.  That's because it was created before I had any SSDs.  If you put the VM storage onto an SSD (SATA or NVMe), then the file format used doesn't really matter.  qemu-img can convert between different file-based VM storage formats.  For all my other VMs, I use LVM2 LVs, which provide direct block devices to the VM and provide lots of enterprise storage capabilities.  Alas, lvm2 is probably too complex for people not already comfortable using it with their normal Linux installs to manage storage.  I will say that performance with LVM is noticeably faster than all the others for moving data, but for typical desktop uses, that probably doesn't matter.

As others have said, MS-Windows is a special situation. Since I don't have Win10/11 anywhere, I can't say any specifics, but with Win7, to get the best performance, I loaded the Redhat QXL GPU drivers and the virtio drivers for both networking and storage.  With Linux guest VMs, the virtio networking and disk drivers are built-in.  For network transfers between the host and any VMs on the same physical computer, I'm seeing 25-35 Gbps transfers according to iperf3.  This is even with the physical NICs being only 1 Gbps and not bonded.  Of course, transferring that much data make VM graphics awesome, but isn't really useful for anything stored on disk, since disks can only read-write so quickly.  High end NVMe x4 storage might get to 32 Gbps, but my real world consumer testing puts them closer to 3 or 4 Gbps.  My SATA SSD is more like 550 Mbps.

---

### Post by MAFoElffen on 2023-01-24
Do not do a sysprep on Windows to move...
> Fedora infrastructure hosts virtIO drivers and additional software  agents for Windows virtual machines running on kernel-based virtual  machines (KVM). [virtIO]("https://www.linux-kvm.org/page/Virtio") is a virtualization standard for network and disk device drivers.

[https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/stable-virtio/virtio-win.iso](https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/stable-virtio/virtio-win.iso)

---

### Post by TheFu on 2023-01-24
> **MAFoElffen said:**
> Do not do a sysprep on Windows to move...


[https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/stable-virtio/virtio-win.iso](https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/stable-virtio/virtio-win.iso)

I don't see how sysprep and virtio drivers are directly connected. What am I  missing?

---

### Post by oygle on 2023-01-24
Wow, lots of great replies, thank you [TheFu]("https://ubuntuforums.org/member.php?u=1037685"), [monkeybrain20122]("https://ubuntuforums.org/member.php?u=1843403"), [ajgreeny]("https://ubuntuforums.org/member.php?u=27747"), [Irihapeti]("https://ubuntuforums.org/member.php?u=346442") and [MAFoElffen]("https://ubuntuforums.org/member.php?u=1044547") , very much appreciated, thanks.

The move from VirtualBox to KVM/Qemu (was VMWare) , in regards to Windows 10, is on the same computer, so I don't think Microsoft will spit the dummy. AFAIK, the MS OS can't even 'see' outside a VM, and all it will be checking is hardware. So, hardware the same, shouldn't be any licensing or activation issues.

It seems exporting from VirtualBox and then importing may be problematic, as the few articles I have read say to 'keep trying' if the import doesn't work. Hmm..

So converting the VDI to QCOW2 seem the best way to go forward, plus install Virt-Manager. The help guides for that are as supplied, plus one other:

[https://markontech.com/linux/convert-virtualbox-vms-to-qemu-kvm/](https://markontech.com/linux/convert-virtualbox-vms-to-qemu-kvm/)

[https://www.vinchin.com/en/blog/kvm-create-vm-from-qcow2.html](https://www.vinchin.com/en/blog/kvm-create-vm-from-qcow2.html)

[https://www.tecmint.com/migrate-virtualbox-vms-into-kvm-vms/](https://www.tecmint.com/migrate-virtualbox-vms-into-kvm-vms/)

either the first one or the third one I think. Thanks again for your help.  :)

---

### Post by TheFu on 2023-01-24
Remember with virtual machines, the real hardware doesn't matter. It is the virtual hardware that the VM sees, so the virtual motherboard will be different.  You can check what chipset virtualbox emulates and see if KVM/QEMU can emulate a motherboard/chipset that is similar, but they won't be the same.  Sorta like how Asus and Gigabyte both make motherboards using the X570 chipset, but they are still slightly different.  But we are working with virtual motherboards being emulated.  

Here are the list of motherboards emulated on 1 of my VM hosts:
pc-1.0
pc-i440fx-trusty
pc-i440fx-xenial
pc-q35-2.11
pc-i440fx-focal

So, if virtualbox is emulating an i440fx, then I'd pick that for KVM.

---

### Post by oygle on 2023-01-24
> **TheFu said:**
> Remember with virtual machines, the real hardware doesn't matter. It is the virtual hardware that the VM sees, so the virtual motherboard will be different.  You can check what chipset virtualbox emulates and see if KVM/QEMU can emulate a motherboard/chipset that is similar, but they won't be the same.  Sorta like how Asus and Gigabyte both make motherboards using the X570 chipset, but they are still slightly different

Oh, I see, thanks. I'd be best to dump/list all the emulations that VirtualBox is currently seeing then. The **VBoxManage list** at [https://docs.oracle.com/en/virtualization/virtualbox/6.0/user/vboxmanage-list.html](https://docs.oracle.com/en/virtualization/virtualbox/6.0/user/vboxmanage-list.html) should be able to tell me all the info.

---

### Post by TheFu on 2023-01-24
[https://www.virtualbox.org/manual/UserManual.html#settings-system](https://www.virtualbox.org/manual/UserManual.html#settings-system)
PIIX3
ICH9 
look like the chipset options.

---

### Post by oygle on 2023-01-24
> **TheFu said:**
> [https://www.virtualbox.org/manual/UserManual.html#settings-system](https://www.virtualbox.org/manual/UserManual.html#settings-system)
PIIX3
ICH9 
look like the chipset options.

Thanks, it is PIIX3

Well, I went through the steps as per [https://markontech.com/linux/convert-virtualbox-vms-to-qemu-kvm/](https://markontech.com/linux/convert-virtualbox-vms-to-qemu-kvm/) , no hiccups at all. The conversion to .qcow2 file format only took about 20 mins to process the 40 Gb .VDI ; the resultant .qcow2 file was 34.5 Gb

The import took no time at all, no errors or problems. Started up the guest/win10 , and _unfortunately_ it was **VERY** slow, in fact worse than VirtualBox   :(

No doubt I need to tweak some settings in Virt-Manager. Ran system monitor whilst the guest was running, the process libvirt-qemu was using all the RAM at 4 Gb (8 Gb of RAM in laptop), and the CPU usage was 20% to 25%, with occassional jumps to 49% . Using any apps on the host resulted in resource issues, mouse not moving, video issues, even the email client (Claws) was taking longer than usual to fetch email. Firefox was not worth the waiting on host.

There is plenty of disk space available; swap is only 4.7 Gb, maybe that needs increasing.

---

### Post by TheFu on 2023-01-24
Is the qcow2 on an SSD?
Did you load QXL and virtio drivers, as suggested?
RAM and swap are fine.  How many vCPUs?  I typically use 1 for Linux VMs and 2 for Windows.  With Linux, if I need more CPU, adding 1 is easy.  MS-Windows installs a different kernel for single core systems than for multi-core systems.

[https://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](https://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox) has some ideas for performance, but they aren't just for vbox. They apply to all VMs, just the exact details change, but not the big ideas.

QXL+spice is excellent. Use it.  This will help graphics performance. [https://www.spice-space.org/download.html](https://www.spice-space.org/download.html) has the Windows binaries.
VirtIO may or may not matter. Depends on how you use the VM.  The NIC and storage virtio drivers are a bit of a hassle if your VM won't boot at some time in the future due to storage corruption (failing disk).  So, it might be better to emulate e1000e Intel PRO/1000 NIC and SATA/SCSI HDDs for many people.  I had a drive that was failing which happened to be where the Windows VM was stored. It was a hassle to use the Windows CDROM/DVD for recovery mode because the virtio drivers weren't provided.  If win10/11 brings those, use them. If they don't, it probably isn't worth the hassles for 95% of users.

---

### Post by MAFoElffen on 2023-01-24
See the attached... That is a Windows 11 VM Guest running RSAT to manage another Windows Server 2022 VM Guest running as a Domain Controller, that also has Ubuntu 23.04 Linux VM Guests joined to the domain... They are all living together, and working together.

Pushing things? Yes, I have a little experience running Windows Guests on KVM.

Sysprep Generalize would have sterilized the VM image of systems and administrative specifics, such as drivers, licensing info, computer system ID (SID), Activation, User info, etc. When the image does a first boot after that, it starts out, as if it was a fresh, new, install, asking for user info and such... It is meant for distributing a single image for multiple image distribution thorughout a Domain or so forth... As a new/fresh image. Not meant to move an image to be "restored" to new hardware and "continuing on" with the configuration it had, with the users it had.
> The sysprep /generalize command removes unique information from your Windows installation, which enables you to reuse that image on different computers. The next time you boot the Windows image, the specialize configuration pass runs. During this configuration pass, many components have actions that must be processed when you boot a Windows image on a new computer. Any method of moving a Windows image to a new computer, either through imaging, hard disk duplication, VM copying or other method, must be prepared with the sysprep /generalize command. Moving or copying a Windows image to a different computer without running sysprep /generalize is not supported. 
So yes, as a fresh install, needing configuration as new.

You can see that now right? That way, with sysprep generalize, you get different / unique machines, not a "copy" of the original. There is a place for that, but when trying to keep his activation... You could do it. It is possible, but more work and not the test case. (a migration of the users, data and configs.

The other link I gave was the kvm virtio drivers for Windows. That would allow enhanced graphics and cut-and-paste... Per se, Guest additions kinds of things for a Windows Guests in KVM. That would have to be mounted as a CD (ISO) and installed to each Windows Guest.

I run Win11 guests and that 2022 Server VM's, both at 4GB RAM each (depending on their jobs)... but just like Windows installed natively, it runs better and more snappy with twice that amaount of RAM. Given it a bigger swap file may help. 

I run the KVM Windows virtio drivers maintained by the Fedora Project. I do a bit of tuning for testing. 

Remember that I beta test for Ubuntu Desktop and Server Development Editions, Windows Insider Program for Desktop and Server, and VMware vSphere and vCenter. Just something I do. So I have a bit of hands-on User and Admin experience on them. It keeps me entertained and current in my skills.

---

### Post by oygle on 2023-01-25
> **TheFu said:**
> Is the qcow2 on an SSD?

No, a SATA HDD

> **TheFu said:**
> Did you load QXL and virtio drivers, as suggested?

To do that, one needs to get sharing going on the guest system. It's kind of a PITA that there seems to be no definitive articles/guides for Virt Manager, to do this and that. At least VirtualBox has loads of documentation for help. One has to resort to spending hours searching, some things don't work though. Anyway, I used [https://www.debugpoint.com/share-folder-virt-manager/](https://www.debugpoint.com/share-folder-virt-manager/) and got up to > In the guest machine, create a folder where you want to mount the host folder. as beyond that is a *nix guest.

Then used [https://dausruddin.com/how-to-enable-clipboard-and-folder-sharing-in-qemu-kvm-on-windows-guest/](https://dausruddin.com/how-to-enable-clipboard-and-folder-sharing-in-qemu-kvm-on-windows-guest/) , but win10 froze.  started up again and able to install it okay.  Now can at least use clipboard bewteen host and guest. However, the win10 freezing concerns me, as when it did boot again, the Win10 wanted me to login as it didn't seem to recognise me. So, something may have becoming corrupted in the freeze.

> **TheFu said:**
> How many vCPUs?

Processors: 4 × Intel® Core&#8482; i7-4510U CPU @ 2.00GHz

> **TheFu said:**
> [https://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](https://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox) has some ideas for performance, but they aren't just for vbox. They apply to all VMs, just the exact details change, but not the big ideas.

I did look at that document, but noted it was 10 years old, plus I didn't want to have to wade through all that info and try and glean out what I need. Some sort of 'how to' is easier for me.

> **TheFu said:**
> QXL+spice is excellent. Use it.  This will help graphics performance. [https://www.spice-space.org/download.html](https://www.spice-space.org/download.html) has the Windows binaries.

I got as far in the Win10 guest as to install the windows binaries. There was no performance difference, however being 'Windows" it would require a reboot. Some things never change.

Because of the 'freeze' in Win10, I need to start again. That is, from converting the .VDI to .QCOW2 . This time I will grab a backup of the resultant .QCOW2 file. Thanks for your help.

---

### Post by oygle on 2023-01-25
> **MAFoElffen said:**
> See the attached... That is a Windows 11 VM Guest running RSAT to manage another Windows Server 2022 VM Guest running as a Domain Controller, that also has Ubuntu 23.04 Linux VM Guests joined to the domain... They are all living together, and working together.

Pushing things? Yes, I have a little experience running Windows Guests on KVM.

That's quite a setup and a lot more involved than I need to do.

> **MAFoElffen said:**
> Sysprep Generalize would have sterilized the VM image of systems and administrative specifics, such as drivers, licensing info, computer system ID (SID), Activation, User info, etc. .................

I don't think I need to use Sysprep; possibly the mention of it is for another poster ?

> **MAFoElffen said:**
> The other link I gave was the kvm virtio drivers for Windows. That would allow enhanced graphics and cut-and-paste... Per se, Guest additions kinds of things for a Windows Guests in KVM. That would have to be mounted as a CD (ISO) and installed to each Windows Guest.

Yes, thanks. I did download those Virtio drivers, but then a catch-22. I couldn't mount it in a win10 guest and even if the guest could access it, I would need to get sharing going on the win10 guest. Using an ISO on *nix I'm fine with, but how does one do that on Win10 ?  There seems to be many ways to do specifics with KVM/QEMU. Virtio, Spice, other methods. Just one guide that I can easily follow to get a Win10 guest going. 

> **MAFoElffen said:**
> Given it a bigger swap file may help.

There seems to be a general resource issue with this laptop, so my perception of KVM/QEMU/Virt Manager and all the 'extras' may not be clear. Meaning, if the host was more powerful, other resource issues may not be as they are. The laptop is 8 years old now. I may try making the SWAP larger.

Thanks for your help. As you can see, I need to (somewhat) start again.

---

### Post by TheFu on 2023-01-25
> **oygle said:**
> No, a SATA HDD

Well, then you shouldn't use file-based VMs.  You need a preallocated img file for massive performance differences if it isn't on an SSD.  That's covered in the jdpfu link.

> **oygle said:**
> 
To do that, one needs to get sharing going on the guest system. It's kind of a PITA that there seems to be no definitive articles/guides for Virt Manager, to do this and that. At least VirtualBox has loads of documentation for help. One has to resort to spending hours searching, some things don't work though. Anyway, I used [https://www.debugpoint.com/share-folder-virt-manager/](https://www.debugpoint.com/share-folder-virt-manager/) and got up to  as beyond that is a *nix guest.

Why?  I'd just download it to Windows from inside the VM.  Then right-click on the driver file and choose "install" if it is an .inf.  If it has a setup.exe, run that. Done and done.

> **oygle said:**
> 
Then used [https://dausruddin.com/how-to-enable-clipboard-and-folder-sharing-in-qemu-kvm-on-windows-guest/](https://dausruddin.com/how-to-enable-clipboard-and-folder-sharing-in-qemu-kvm-on-windows-guest/) , but win10 froze.  started up again and able to install it okay.  Now can at least use clipboard bewteen host and guest. However, the win10 freezing concerns me, as when it did boot again, the Win10 wanted me to login as it didn't seem to recognise me. So, something may have becoming corrupted in the freeze.

Was the source VDI corrupted?  I don't use Windows enough to recognize what this means.  Maybe someone else will.

> **oygle said:**
> 
Processors: 4 × Intel® Core™ i7-4510U CPU @ 2.00GHz

Well, the real processor count doesn't matter. How many did you tell virt-manager to provide to the VM?  I hope not 4.  Go with 2 vCPUs to start. Always leave 1 CPU for the hostOS to have fully.  If you don't, the systems that manage the VM won't have sufficient CPU to do that job.  Same applies for RAM.  The jdpfu link says that too.

> **oygle said:**
> 
I did look at that document, but noted it was 10 years old, plus I didn't want to have to wade through all that info and try and glean out what I need. Some sort of 'how to' is easier for me.
 Sorry. That's all I got.  When I write articles, I want to say "why", not what to type. The what to type changes too often, with each GUI, but the "WHY" doesn't change.  1000s of how-to guides say what to type.  Only a very few explain WHY.

> **oygle said:**
> 
I got as far in the Win10 guest as to install the windows binaries. There was no performance difference, however being 'Windows" it would require a reboot. Some things never change. 

Because of the 'freeze' in Win10, I need to start again. That is, from converting the .VDI to .QCOW2 . This time I will grab a backup of the resultant .QCOW2 file. Thanks for your help.
Well, if you don't reboot the VM (full shutdown and restart), then the QXL drivers won't be used.  Also, inside the VM controls, you'll need to enable spice, not VNC.  Inside the details for the virtual machine, look for 
* Display Spice --> "spice server"
* Channel Spice --> it probably says spicevmc + virtio
* Video QXL ---> Choose QXL for the model.

---

### Post by oygle on 2023-01-25
> **TheFu said:**
> Well, then you shouldn't use file-based VMs.  You need a preallocated img file for massive performance differences if it isn't on an SSD.  That's covered in the jdpfu link.

It'a already preallocated. The storage size is shown in Virt Manager as 45 Gb, whereas the actual size is 36 Gb. I searched through the jdpfu document for "preallocated", "img", "image" and "file", yet there are no specifics , or 'how to's".

> **TheFu said:**
> Was the source VDI corrupted?  I don't use Windows enough to recognize what this means.  Maybe someone else will.

In typical Windows fashion, it totally froze, no mouse, nothing, no response. From the VM manager, I tried shutdown, stop, pause, force this, force that, so after 20 mins of that The VM Manager succeeded in a shutdown. So from a Win perspective, a process outside of Windows shut it down. Next 'start' to win10 guest and it wanted logins, etc, so I have to assume that win10 guest file is cactus.

> **TheFu said:**
> Well, the real processor count doesn't matter. How many did you tell virt-manager to provide to the VM?  I hope not 4.  Go with 2 vCPUs to start. Always leave 1 CPU for the hostOS to have fully.  If you don't, the systems that manage the VM won't have sufficient CPU to do that job.  Same applies for RAM.  The jdpfu link says that too.

I only gave it two. One thing that did seem to make a slight difference in performance was the 'enable shared memory' setting. The doc at [https://www.debugpoint.com/share-folder-virt-manager/](https://www.debugpoint.com/share-folder-virt-manager/) suggested that. By default it is set off/disabled.

> **TheFu said:**
> Well, if you don't reboot the VM (full shutdown and restart), then the QXL drivers won't be used.  Also, inside the VM controls, you'll need to enable spice, not VNC.  Inside the details for the virtual machine, look for 
* Display Spice --> "spice server"
* Channel Spice --> it probably says spicevmc + virtio
* Video QXL ---> Choose QXL for the model.

Rebooting the VM was not initially possible, as the guest had frozen. Meaning any action from the VM Manager has no effect. The inside details are the same as here. Thanks.

---

### Post by TheFu on 2023-01-25
Thinking about this again, I'm back to thinking the wrong drivers are still installed.  Inside the VM, can you check in the driver manager for the GPU, network and disk drivers being used?

I'm assuming KVM/QEMU as the hypervisor with virt-manager and libvirt as the supporting tools/libraries.

The image file isn't fully allocated if the VM and the file system holding it don't show the same sizes inside and outside the VM.

For example, at the host level:
```
-rw-rw---- 1 root         root 36507222016 Jan 18 16:42 Win7Ult-Data2.img
-rw-rw---- 1 root         root 63166218240 Jan 18 16:42 Win7Ult-os.img
```
 That's 35G and 59G sized files for Windows.
When I boot that VM, from inside it, I see 2 drives, they are 58.7G and 33.6G.  That's the overhead of NTFS formatting.  That's "fully pre-allocated".  VDI and qcow2 are dynamic resizing file containers.  That slows down the VM, since the size increases cause performance hits when they are needed.  They are also known as "sparse files", which you can look up later if you are interested.

---

### Post by oygle on 2023-01-25
> **TheFu said:**
> Thinking about this again, I'm back to thinking the wrong drivers are still installed.  Inside the VM, can you check in the driver manager for the GPU, network and disk drivers being used?

In the win10 guest, there were a few 'attention' type icons when viewing device drivers. For example - "Other devices /  mas storage controller". I did try fixing that and load drivers, but win10 could neither find the driver on the computer or as part of the updates. I also noticed, when applying "show hidden devices" there were a number of VBOX drivers. They weren't being used, but as it is superfluos, deleted those.

---

### Post by TheFu on 2023-01-25
Video = Redhat QXL driver
Network = Redhat Virtio driver OR  Intel PRO/1000 driver. You're choice.
Disk Controller = Redhat Virtio driver OR standard SATA/SCSI driver.  If you might have more than 15 storage devices connected, go with the SCSI driver.

You don't want any other drivers for those things loaded.  The fake hardware presented by the VM settings in virt-manager needs to match the driver loaded inside the VM.

BTW, you need to remove any virtualbox stuff, like their guest additions.  sysprep would have done this, but if MAFoElffen says not to use sysprep, **definitely listen.**  He knows this stuff when it comes to Windows much, much, much better than me.  And my MSFT knowledge is way out of date.  Some of our knowledge overlaps, but some doesn't.  When I used sysprep, all the applications and data for those applications remained.  At the time, I didn't want my 7MC already seen/recorded TV shows to be lost and I didn't want to setup season passes for shows.  I don't remember if a new userid was necessary.  But I definitely remember that I didn't lose ANY TV recording history or season pass information due to sysprep or the migration.  I've moved from C2D --> Core i5 --> Ryzen computers all with different physical motherboards, but since it was a VM, I just retained the same virtual motherboard and it moved cleanly.  In the Ryzen, I did have to change the CPU architecture, since Intel and AMD CPUs are different settings.  This Windows system was a media center PC, running inside a VM, so it needed to be fast enough.  Only the Ryzen has an SSD. The prior 2 computers didn't.

According to this: [https://leduccc.medium.com/improving-the-performance-of-a-windows-10-guest-on-qemu-a5b3f54d9cf5](https://leduccc.medium.com/improving-the-performance-of-a-windows-10-guest-on-qemu-a5b3f54d9cf5)  There are known issues moving Windows guests due to incorrect disk controller settings.  They also say that using a host kernel of 5.15+ is a huge performance gain. Anyway, he gets into the weeds for optimization of Windows guests under KVM.  About half of what is in that article will get you 90% of the gains and the other half another 5%.  Stick with the drivers for now.  I've definitely never pinned a CPU to a VM.  Turning off disk caching in the VM setup is easy and might help a little. I've always done that.  Most of the suggested tuning values are libvirt defaults now.

Oh, and make certain you aren't using btrfs on the Linux host.  THAT is important.

---

### Post by oygle on 2023-01-25
> **MAFoElffen said:**
> Do not do a sysprep on Windows to move...

[https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/stable-virtio/virtio-win.iso](https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/stable-virtio/virtio-win.iso)

I mounted the ISO in the win10 guest and installed virtio-win-guest-tools . There is a virtio-win-gt-X64 windows installer file there as well. Do I also install that ?

---

### Post by oygle on 2023-01-25
> **TheFu said:**
> Video = Redhat QXL driver
Network = Redhat Virtio driver OR  Intel PRO/1000 driver. You're choice.
Disk Controller = Redhat Virtio driver OR standard SATA/SCSI driver.  If you might have more than 15 storage devices connected, go with the SCSI driver.

The Video is Redhat, the other two are Microsoft.

> **TheFu said:**
> According to this: [https://leduccc.medium.com/improving-the-performance-of-a-windows-10-guest-on-qemu-a5b3f54d9cf5](https://leduccc.medium.com/improving-the-performance-of-a-windows-10-guest-on-qemu-a5b3f54d9cf5)  There are known issues moving Windows guests due to incorrect disk controller settings.  They also say that using a host kernel of 5.15+ is a huge performance gain.....

The Kernel Version: 5.15.0-58-generic (64-bit). I'll have another rad of that article; I had seen it a few days ago but didn't read all the specific details.

> **TheFu said:**
> Oh, and make certain you aren't using btrfs on the Linux host.  THAT is important.

It's got a vfat/FAT32 partition for /boot/efi , and all other partitions are EXT4

---

### Post by TheFu on 2023-01-25
virtio-win-gt-X64 is a new-fangled graphics method.  I've never tried it. My VM hosts don't have the support.  I know that QXL works well, but I've heard good things about virt-gt.   [https://pve.proxmox.com/wiki/Windows_VirtIO_Drivers](https://pve.proxmox.com/wiki/Windows_VirtIO_Drivers)  says that it provides a passthru, so do you have 2 GPUs in the system?  Passthru GPUs to a guest require exclusive use and only specific $300+ GPUs are supported.  At least that's my understanding.  I've never had a GPU like that.

According to that proxmox link, the QXL drivers for Windows are in the ISO.  For now, I'd say to install that. You can change it later.  QXL is a virtual GPU driver and doesn't require GPU/PCIe passthru, so it works on any system, even those without any GPU physically in the computer.

BTW, proxmox is KVM too, just with a fancy webapp interface and that it takes over the entire system so it is a VM host only.

---

### Post by MAFoElffen on 2023-01-26
What I meant was the Windows swap file, which they refer to as a page file... From within your Windows Guest...

[LIST=1]
[*]Click Start > Run ( <Win><R> )and then type sysdm.cpl, and press Enter. 
[*]Click the Advanced tab. 
[*]In the Performance Section, click Select 
[*]Click the Advanced Tab 
[*]In the Virtual Memory section, click Change. 
[*]Clear the Automatically manage page file size for all drives check box. 
[*]Find the list of drives and select the drive that contains your paging file. 
[*]Select Custom Size. 
[*]Reset both the Initial Size (4096) and Maximum Size (8192) values to higher values. 
[*]Click Set. 
[*]Click OK. 
[/LIST]
Restart VM. It will be snappier... Like I said, Windows runs better with more memory.

I do differently, as I have 128G's on my Virt Hosts. I can just add more memory to the Guest. But In VirtManager, I usually have my sys monitors open to see just how much resources a guest is using and needs, so I can manage those resources.

---

### Post by oygle on 2023-01-26
> **TheFu said:**
> virtio-win-gt-X64 is a new-fangled graphics method.  I've never tried it. My VM hosts don't have the support.  I know that QXL works well, but I've heard good things about virt-gt.   [https://pve.proxmox.com/wiki/Windows_VirtIO_Drivers](https://pve.proxmox.com/wiki/Windows_VirtIO_Drivers)  says that it provides a passthru, so do you have 2 GPUs in the system?  Passthru GPUs to a guest require exclusive use and only specific $300+ GPUs are supported.  At least that's my understanding.  I've never had a GPU like that.

No I don't have 2 GPU's. With the virtio-win-gt-X64.msi , I found out it is a cut down version of the fuller install virtio-win-guest-tools.exe , so I only really had to install the EXE

> **MAFoElffen said:**
> What I meant was the Windows swap file, which they refer to as a page file... From within your Windows Guest...

[LIST=1]
[*]Click Start > Run ( <Win><R> )and then type sysdm.cpl, and press Enter. 
[*]Click the Advanced tab. 
[*]In the Performance Section, click Select 
[*]Click the Advanced Tab 
[*]In the Virtual Memory section, click Change. 
[*]Clear the Automatically manage page file size for all drives check box. 
[*]Find the list of drives and select the drive that contains your paging file. 
[*]Select Custom Size. 
[*]Reset both the Initial Size (4096) and Maximum Size (8192) values to higher values. 
[*]Click Set. 
[*]Click OK. 
[/LIST]
Restart VM. It will be snappier... Like I said, Windows runs better with more memory.

Thanks, that has made a **HUGE** difference to the Host actually. I can now do tasks on the Host whilst the VM/guest are running. Even a screendump on the guest works now; I think that is spice though. See the attached screen dump; maybe I could increase, but the guest only has 4Gb ram, so surely an 8Gb page/swap file is plenty. Maybe the 'shared memory' in the Virtual Manager settings should be disabled ?

Definitely the guest is more responsive also. Now, one thing I don't understand. I have TOP running and the guest is doing nothing at all, but top says

libvirt+
    cpu  41  to 59 (sometimes jumps to 70, 80 and even 103% , 130%)
    mem   53 %

why would it be using so much when the guest is doing nothing ? I guess it is simply the whole resources of running an emulation.  Thanks for your help.  :)
[ATTACH=CONFIG]291637[/ATTACH]

---

### Post by TheFu on 2023-01-26
My win7 under KVM has these settings:
2 vCPUs
1.5G RAM
Storage
  2 fully Preallocated img files for storage (C: and D: inside Windows)
  virtio
  raw access with no cache.
Networking
  e1000 NIC  - that's an Intel PRO/1000 emulated NIC.
SpiceVMC with virtio and virtio-serial
Graphics: GPU is listed as spice, listening on all host NICs.  I'll connect over spice from other systems almost always, if I use a GUI
Video model qxl with 64KB vRAM.
Audio is an emulated ac97 soundcard.
2 USB3 passthru devices, but I can't remember those ever working.

It runs fast on the Ryzens and was a Windows7 Media Center on an older, slower, Core i5-750 (1st-gen) and on a Core2 Duo E6600 (which was a 1st-gen Core2 Duo).

Let me boot it to see the swap ... btw, 12 seconds to boot to the login window.
The pagefile is 1511 MB and fixed size. I don't allow it to grow and shrink as needed.

As for the CPU use as seen by the hostOS.  Windows has always used much more CPU and shared resources poorly, even when doing nothing.  That article above seems to say they added some controls to make Windows better behaved in virtual machines in Win11, if the settings are tweaked.  That's outside my experience, so I don't know.

My Win7 machine is for financial programs and versions of those programs that were installed in 2013 or earlier.  Every year, I install a new tax program and hope it works. So far, that has been working. One year, it won't, I just hope it isn't this year.

---

### Post by MAFoElffen on 2023-01-27
Getting back to the virtio drivers... I mount it in the cdrom device, open the drive in the guest, as if it where a dvd and run setup. It installs the virtio drivers to the guest.

For a Windows 11 guest
2 vCPU's
Display Spice, Listen
Video QXL
Memory 4GB
Internal page file min 4096, max 8192
Sound AC97 or ICH9 (either works)
TPM 2.0

For TPM, on one host I have sptpm installed and use for the guest, type 'emulated', on another tHost hat has a TPM, on the guest I use TPM type 'pass-through'.

---

### Post by oygle on 2023-01-29
Thanks for your help.

---

