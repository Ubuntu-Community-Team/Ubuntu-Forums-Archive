---
title: "Virtualizing Windows7, what would be the best option?"
date: 2012-09-06
forum: Virtualisation
---

### Post by Bob Morane on 2012-09-06
Hi. Long time since i posted here. I'm still using Ubuntu (now kubuntu 12.04) and i'm still dual-booting (now Win7). A couple days ago i rebooted 5 times just to switch OSs ](*,) so i figured i would have to find a better option. I started looking at virtualization again. Years ago i decided it was a no-option because of poor performances. Now, things have changed with new virtualization options and better hardware.
[LIST]
[*]I need as close to native speed as possible for Windows7 as well as it being able to use much ram. My most ressource heavy applications run in windows.
[*]I'd like to re-use my existing windows install, or at least copy it entirely to the VM in a way that won't mess up with proprietary applications activation limits.
[*]I would prefer to have Ubuntu be the host OS and win7 the guest. I don't like the idea of having Ubuntu depend on Windows to run.
[/LIST]
My hardware
[LIST]
[*]Intell Core i5-2400 (quad core with VTx support)
[*]8 GB ram
[*]1 TB hard disk with several partitions
[*][[COLOR="Blue"]_Asus P8P67-M PRO motherboard_[/COLOR]]("http://www.asus.com/Motherboards/Intel_Socket_1155/P8P67M_PRO/#specifications") (i don't think it supports special virtualization features such as IOMMU but i'm not sure how to check it.
[/LIST]
I'd like to get the best possible configuration for running both OSs. I've already looked at several options. Probably i missed some :
[LIST]
[*]Oracle VM Box running under Ubuntu : i fear Win7 will suffer from severe performance drops and i need power for Win7.
[*]VirtualBox under Win7 (ubuntu as guest) : don't like it much.
[*]coLinux based solution (andUbuntu & portable ubuntu). Ubuntu would depend on Win and those seem to be abandonware.
[*]Cygwin : i would have to recompile Ubuntu. Ubuntu would run under Win7.
[*]Hypervisor based install (xen, kvm, vmware vSphere). This is the option i'm most interested in. Xen claims for up to 95% native speed. However i have no experience with this sort of virtualization. Xen is currently my favorite as it's open source (unlike vSphere) and kvm looks like a strange beast running inside the linux kernell (i would guess it has lower speed but i may be wrong).
[/LIST]
Now, can someone tell me
[LIST=1]
[*]Is it possible to re-use an existing install of Win7 under Xen. If so, do i need it on a separate physical disc, or is a partitionned disc OK?
[*]If Win7 has it's own physical disc, is possible to use PCI passthrough to give direct access to this disc or is PCI passthrough limited to PCI cards?
[*]Is it possible to use GPU acceleration on Win without using VGA passthough? If i use VGA passthough i'll need a different graphic card for Ubuntu IIUC.
[*]Is it possible to share disc partition between virtual machines like i do for dual-boot?
[*]Is there a way to share the clipboard? Well, for this one i doubt it but i guess it would be theorically possible with some shared memory.
[*]Also, did i miss some better options?
[/LIST]

---

### Post by jgaa on 2012-09-06
I have good experiences wih VirtualBox. I used W7 or XP to browse lame sites that required IE, Java or Flash, and re-set the VM after each use. As far as I remember, it can take disk partitions. If you want to share partitions between OS'es, you should mount them read only. Else, let one machne handle the partition, and then share it to the other(s). Clipboard works fine with VirtualBox and VmWare. (VmWare workstation 6 worked fine on Debian, but performance was so-so).

Today I have mostely abadoned VirtualBox. I don't like the way Oracle run things, so now I use VmWare workstation 7 for full deskop virtualization. Under Debian, I was unable to run W7 smooth and flawless as a guest under VmWare. Curretly I use W7 as the host system (on my main laptop, a Thinkpad w520 / i7 quad core CPU / 16 GB RAM, SSD) and run Debian and Ubuntu as guests. They run at almost full speed - so I can easily develop relatively large projects in kdevelop, without noticing any overhead.

---

### Post by HermanAB on 2012-09-09
Howdy,

You can boot the present Windows partition using either Virtualbox or VMware.  You don't actually need to re-install it.

However, there are a few gotchas.  For example, if you reboot into Windows, then the system activation may require you to register again.  If you boot into Windows and suspend, then run it under Virtualbox, the file system will be corrupted, because the VM doesn't know that it was suspended (and vice versa), so you may lose some files.  Therefore, in general, it is better to make a new VM.

---

### Post by Welly Wu on 2012-09-10
The best practice would be to make a backup of your existing Microsoft Windows 7 partition as a safety precaution before you decide to do anything.

The other best practice would be to install Microsoft Windows 7 in a guest virtual machine on the same PC. This will avoid many problems especially with suspend or hibernation or encryption.

For your purposes, I would recommend that you purchase and install the latest version of VM Ware Workstation 9 64 bit. VM Ware Workstation 9 is compatible with Microsoft Windows XP, Vista, and 7 and GNU/Linux including Ubuntu 12.04.1 64 bit Long Term Service. I have VM Ware Workstation 8.0.4 64 bit installed on my Ubuntu 12.04.1 64 bit Long Term Service. VM Ware Workstation 9 will offer you near native performance on your PC for Microsoft Windows 7 32 or 64 bit in a guest virtual machine and it fully supports Aero features with 3D graphics hardware acceleration. It also supports USB, Firewire, eSATA, and PCI pass through. Finally, you can make backup snapshots of your guest virtual machines and you can encrypt them using AES CBC mode 256 bits 14 rounds for additional security.

Oracle VM Virtualbox 4.1.22 64 bit is a good free and open source alternative and I use it for my Microsoft Windows 7 64 bit Ultimate Edition Service Pack 1 even though I have VM Ware Workstation 8.0.4 64 bit. One thing that you need to know is that VM Ware Workstation 9 supports Ubuntu 12.04 32 and 64 bit as both the host and guest operating system. You won't need to download a third party patch to compile the Linux kernel in order to get the VMNet driver to compile properly which you have to do so with VM Ware Workstation 8.x 64 bit with Ubuntu 12.04.1 32 or 64 bit Long Term Service.

In the end, VM Ware Workstation 9 will offer you the most amount of hardware and software compatibility and it will offer you long term support if you purchase a support contract. It is suitable for enterprise production environments so it is super stable. I have found that Oracle VM Virtualbox and the free and open source Virtualbox OSE within the standard Ubuntu Software Center to be slower and support for the Microsoft Windows 7 Aero is experimental.

If you plan to work with 3D hardware accelerated graphics such as PC games and you do graphics intensive computations such as video editing, photo editing, gaming, or 3D graphics modeling or if you use your AMD or Nvidia GPU as a second processor for say mathematically intensive computations such as trying to crack encrypted, salted, and hashed data, then you must use VM Ware Workstation 9 64 bit for the most speed and performance for your guest virtual machines. Oracle VM Virtualbox does not offer these features or capabilities or performance.

---

### Post by bra|10n on 2012-09-11
> **Bob Morane said:**
> 
I need as close to native speed as possible for Windows7 as well as it being able to use much ram. 

The ram won't be too difficult, but how to slow VirtualBox or VmWare down to native speeds?
:lolflag:

---

### Post by Bob Morane on 2012-09-12
> **Welly Wu said:**
> The best practice would be ... 

Thanks **Welly Wu**, that's a detailed post. I didn't think "traditional" VMs could run near full speed but last time i tried one was several years ago.

> **bra|10n said:**
> The ram won't be too difficult, but how to slow VirtualBox or VmWare down to native speeds?
:lolflag:
Should i laugh or cry?:-k

---

### Post by HostIndia on 2012-09-13
> **Welly Wu said:**
> The best practice would be to make a backup of your existing Microsoft Windows 7 partition as a safety precaution before you decide to do anything.

The other best practice would be to install Microsoft Windows 7 in a guest virtual machine on the same PC. This will avoid many problems especially with suspend or hibernation or encryption.


+ 1 to this especially when you are doing it seriously. And trying it on Windows 8 would have been better idea.

---

### Post by MasterJimmy on 2012-09-18
im kind of in a similar situation. im running ubuntu 12.04 as host and trying to install win7 home premium as a guest OS. i have the .iso i downloaded after i lost the original disc and have the valid cd key that came with my laptop originally so verification etc isnt a problem. the issue im having is how to even get it going as i cannot seem to figure out how to get the .iso usable. please help!

---

### Post by Bob Morane on 2012-09-20
You can burn the .iso to a CD/DVD-rom disc or mount it as a disc image. Probably burning it is the best way to go.
As for myself, i never got a disc as Win7 was pre-installed on my PC. I have the sticker with the license number so it's a legal install but i'm not sure i can reinstall from an iso :(

---

### Post by consolation on 2012-09-21
Is there an option that works correctly with windows suspend/hibernate?

---

### Post by ricak on 2012-09-21
> **Welly Wu said:**
> The best practice would be to make a backup of your existing Microsoft Windows 7 partition as a safety precaution before you decide to do anything.

The other best practice would be to install Microsoft Windows 7 in a guest virtual machine on the same PC. This will avoid many problems especially with suspend or hibernation or encryption.

For your purposes, I would recommend that you purchase and install the latest version of VM Ware Workstation 9 64 bit. VM Ware Workstation 9 is compatible with Microsoft Windows XP, Vista, and 7 and GNU/Linux including Ubuntu 12.04.1 64 bit Long Term Service. I have VM Ware Workstation 8.0.4 64 bit installed on my Ubuntu 12.04.1 64 bit Long Term Service. VM Ware Workstation 9 will offer you near native performance on your PC for Microsoft Windows 7 32 or 64 bit in a guest virtual machine and it fully supports Aero features with 3D graphics hardware acceleration. It also supports USB, Firewire, eSATA, and PCI pass through. Finally, you can make backup snapshots of your guest virtual machines and you can encrypt them using AES CBC mode 256 bits 14 rounds for additional security.

Oracle VM Virtualbox 4.1.22 64 bit is a good free and open source alternative and I use it for my Microsoft Windows 7 64 bit Ultimate Edition Service Pack 1 even though I have VM Ware Workstation 8.0.4 64 bit. One thing that you need to know is that VM Ware Workstation 9 supports Ubuntu 12.04 32 and 64 bit as both the host and guest operating system. You won't need to download a third party patch to compile the Linux kernel in order to get the VMNet driver to compile properly which you have to do so with VM Ware Workstation 8.x 64 bit with Ubuntu 12.04.1 32 or 64 bit Long Term Service.

In the end, VM Ware Workstation 9 will offer you the most amount of hardware and software compatibility and it will offer you long term support if you purchase a support contract. It is suitable for enterprise production environments so it is super stable. I have found that Oracle VM Virtualbox and the free and open source Virtualbox OSE within the standard Ubuntu Software Center to be slower and support for the Microsoft Windows 7 Aero is experimental.

If you plan to work with 3D hardware accelerated graphics such as PC games and you do graphics intensive computations such as video editing, photo editing, gaming, or 3D graphics modeling or if you use your AMD or Nvidia GPU as a second processor for say mathematically intensive computations such as trying to crack encrypted, salted, and hashed data, then you must use VM Ware Workstation 9 64 bit for the most speed and performance for your guest virtual machines. Oracle VM Virtualbox does not offer these features or capabilities or performance.

So, after reading your post let me ask you this:

imagine the scenario -  i have windows 7 running the games League of Legend, Football manager 12 and PES 12 smoothly in it.

if i delete everything and fresh install ubuntu 12.04 - then install windows 7 on the VM Ware Workstation 9 that you suggest, would i be able to run those games in it without any issue of performance? or could they be laggy or not running at all?

Best regards and tks in advance!

---

### Post by Welly Wu on 2012-09-21
In theory, this should work. Just make sure that you make a backup copy of your vmware folder to another storage device and medium. Anything that you install and run inside a guest virtual machine is self-contained. This means that it is portable. However, with Microsoft Windows, you will run into issues of product key verification and activation issues if you convert a guest virtual machine from one format into another format such as from an Oracle VM Virtualbox .VDI to a VM Ware .VMDK file or if you decide to use your guest virtual machine on a new PC with different PC hardware. You will need to call the special toll-free 800 number at Microsoft to go through the product activation process and they will ask you questions if you have a System Builders or OEM copy of Microsoft Windows Vista or 7. If you have Microsoft Windows 8, you are further limited to vendor lock in. This means that you can not port your VM Ware .VMDK file to an Oracle VM Virtualbox .VDI file or vice versa because Microsoft's new licensing treats virtual machines as separate installations that require you to purchase a new product key and activate the new product key with Windows 8. This is true for the Microsoft Windows 8 Pro 64 bit Upgrade version. If you purchase Microsoft Windows 8 Pro 64 bit System Builders version, then you are limited to only one PC installation per product key and activation. In other words, Microsoft Windows 8 will further lock you down to a per computer license structure and the Microsoft Activation system will close the previous loophole with previous Microsoft Windows XP, Vista, and 7 versions that allow for migrating these versions of Windows to new PCs by decommissioning the old PC and transferring the license to a new PC.

So, it behooves you to pick your virtual machine software application and hypervisor carefully with Microsoft Windows 8. This is especially true for the Pro, Ultimate, and Enterprise Upgrade and System Builders OEM versions.

The industry leader is VM Ware. It is expensive, but it allows for the greatest amount of native PC performance and compatibility with a broad range of operating systems and software applications. It is well supported and you can purchase a support contract with Fusion or Workstation products. It scales very well with legacy, older, and current generation PC hardware and it is mostly compatible with most PCs including Apple Macintosh and System76.

Finally, Microsoft Windows 8 is a re-imagining of Microsoft Windows brand. It will be the fastest high performance version of Microsoft Windows in the company's history. It will also be the most secure version especially if you purchase a new desktop or notebook PC with UEFI and secure boot technologies. Microsoft is tamping down on software piracy with Windows 8 and you should purchase a genuine copy. The same is true for Microsoft Office 2013 especially if you choose to obtain the subscription version of Home Premium, Professional, or Enterprise.

If you want to use Microsoft Windows 8 Pro 64 bit in a guest virtual machine, then you almost must use VM Ware Workstation 9 64 bit. Both are guaranteed to be hardware and software compatible with Ubuntu 12.04.x 64 bit LTS. You will enjoy near native PC hardware performance and maximum stability and compatibility, but it will be an expensive solution.

I can tell you that VM Ware Workstation 9.0.0 64 bit outperforms Oracle VM Virtualbox 4.2.0 64 bit by a significant lead with regard to Microsoft Windows 7 64 bit Ultimate Edition Service Pack 1. The same should hold true with Microsoft Windows 8 Pro 64 bit or Ultimate and Enterprise Editions.

---

