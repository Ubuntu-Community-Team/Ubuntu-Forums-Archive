---
title: "Which VM and setup should i choose to run a demanding program like Gigapixil AI?"
date: 2021-06-17
forum: Virtualisation
---

### Post by tenner1 on 2021-06-17
To be more specific, I need a VM that'll be able to utilize my computers graphics card so I can run this program...



[LIST]
[*]Topazlabs Gigapixel AI 
[/LIST]

My computer exceeds the minimum requirements for this program by a safe  margin so I was hoping to be able to set up a VM that can at least give  Gigipixil AI the **minimum** requirements.  The key here is that the VM will  have to run Windows with the ability to utilize my graphics card with  "**OpenGL version 3.3 or later and DirectX12 compatibility**."   

I'm not expecting to be able to run this program as fast as it would on a windows host system.  For informational purposes, this program did work on my 7 year old dell computer even though it didn't quite meet the minimum requirements so I'm hopeful that my new computer can handle it though a VM.


[LIST]
[*]For more information, the full system requirements for this program are listed here... 
[/LIST]

[https://help.topazlabs.com/hc/en-us/articles/360012811791-Gigapixel-AI-System-Requirements-](https://help.topazlabs.com/hc/en-us/articles/360012811791-Gigapixel-AI-System-Requirements-)

> [COLOR=#4E4E52][FONT=Roboto]Windows 7, 8, 10 (_64-bit only_)
[/FONT][/COLOR][COLOR=#4E4E52][FONT=Roboto]*As of Jan 14, 2020, Microsoft has ended its support for Windows 7. [/FONT][/COLOR][COLOR=#4E4E52][FONT=Roboto]**Mac:** macOS version 10.13 (High Sierra) and above (use [Gigapixel v5.2.2]("https://downloads.topazlabs.com/deploy/TopazGigapixelAI/5.2.2/TopazGigapixelAI-5.2.2-osx-Full-Installer.dmg") for macOS 10.12)[/FONT][/COLOR][COLOR=#4E4E52][FONT=Roboto]We currently do not support Linux-based operating systems.[/FONT][/COLOR]**Graphics Drivers and OpenGL**

[COLOR=#4E4E52][FONT=Roboto]Your system's graphic drivers need to be **fully up to date**, which you can accomplish by following this guide:[/FONT][/COLOR][COLOR=#4E4E52][FONT=Roboto][Updating your GPU]("https://help.topazlabs.com/hc/en-us/articles/360043638851-How-to-update-your-computer-GPU-")[/FONT][/COLOR][COLOR=#4E4E52][FONT=Roboto]Our apps also require **OpenGL version 3.3 or later and DirectX12 compatibility**.
[/FONT][/COLOR]**Hardware Requirements**

**CPU**

[TABLE="width: 0"]
[TR]
[TD="align: center"][/TD]
[TD="align: center"]Intel[/TD]
[TD="align: center"]AMD[/TD]
[/TR]
[TR]
[TD="align: center"]Minimum[/TD]
[TD="align: center"]**Intel i5** or above[/TD]
[TD="align: center"]** Ryzen 3** or above[/TD]
[/TR]
[TR]
[TD="align: center"]Recommended[/TD]
[TD="align: center"]**Intel i5 or i7 6th Gen Core** and above (2015 or newer)[/TD]
[TD="align: center"]** Ryzen 5 **or above[/TD]
[/TR]
[TR]
[TD="align: center"]Optimal[/TD]
[TD="align: center"]**10th Gen or above Intel Core processors**[/TD]
[TD="align: center"]**Ryzen 7 **or above[/TD]
[/TR]
[/TABLE]
[COLOR=#4E4E52][FONT=Roboto]_A note on openVINO_**: **Topaz Labs apps support Intel's OpenVINO toolset for high-speed CPU-based rendering. If you are currently using an Intel CPU, you can enable OpenVINO in the Preferences menu of any of our apps.  **On first-run, Gigapixel AI will auto-optimize settings based on your current installed hardware.**[/FONT][/COLOR]**GPU/Graphics Card**

[TABLE="width: 0"]
[TR]
[TD="align: center"][/TD]
[TD="align: center"]Nvidia[/TD]
[TD="align: center"]AMD[/TD]
[TD="align: center"]Intel iGPU[/TD]
[/TR]
[TR]
[TD="align: center"]Minimum[/TD]
[TD="align: center"]**2GB of dedicated VRAM **(GT 740 or greater)
[/TD]
[TD="align: center"]**2GB of dedicated VRAM **(Radeon 5870 or greater)[/TD]
[TD="align: center"]**Intel iGPU HD5000 **and above[/TD]
[/TR]
[TR]
[TD="align: center"]Recommended[/TD]
[TD="align: center"]** 4GB of dedicated VRAM **(GTX 970 or greater)[/TD]
[TD="align: center"]** 4GB of dedicated VRAM **(Radeon RX 460 or greater)[/TD]
[TD="align: center"]**-**[/TD]
[/TR]
[TR]
[TD="align: center"]Optimal[/TD]
[TD="align: center"]** 8GB of dedicated VRAM **(GTX 1080 or greater)[/TD]
[TD="align: center"]** 8GB of dedicated VRAM **(Radeon RX 580 or greater)[/TD]
[TD="align: center"]**Intel® Iris® Xe Graphics Family**[/TD]
[/TR]
[/TABLE]

[LIST]
[*]*Minimum: Requirements for application to function, users should expect slow performance, large files may cause crashing* 
[*]*Recommended: Users should experience no performance issues, though slowness may occur with large files* 
[*]*Optimal: Users should not experience any performance issues* 
[/LIST]
[COLOR=#4E4E52][FONT=Roboto]*-We do not support Intel HD Graphics 4600 or lower.*[/FONT][/COLOR]**RAM**

[COLOR=#4E4E52][FONT=Roboto]Minimum: **8GB**
[/FONT][/COLOR][COLOR=#4E4E52][FONT=Roboto]Recommended: **16GB**[/FONT][/COLOR][COLOR=#4E4E52][FONT=Roboto]Optimal: **32GB**
[/FONT][/COLOR]


My new host computer has 16GB of ram, a 1tb SSD Drive, an Intel Core i7 processor, and a GeForce RTX 2060 graphics card.

The only other thing I can think to add from here is that I'd prefer that this VM works through Virtual Machine Manager.  I only like to use terminal commands to set things up when absolutely necessary.  

So basically all I need to know is which VM would work best for this situation and are there any drivers or additional features that I'll need to add to my VM to get this working properly.  I have the free unlicensed version of Windows ready to be installed but if that's not going to work well, just let me know.

---

### Post by scorp123 on 2021-06-17
KVM with GPU pass-through?

This guide for Ubuntu 18.04 should still be valid more or less:
[https://mathiashueber.com/windows-virtual-machine-gpu-passthrough-ubuntu/]("https://mathiashueber.com/windows-virtual-machine-gpu-passthrough-ubuntu/")

EDIT:  by chance also found a guide for Ubuntu 20.04 from the same guys...
[https://mathiashueber.com/pci-passthrough-ubuntu-2004-virtual-machine/]("https://mathiashueber.com/pci-passthrough-ubuntu-2004-virtual-machine/")

If it's good enough for gaming then it should also be good enough for your program there (never heard of it to be honest ... ) .

---

### Post by MAFoElffen on 2021-06-17
Just thinking out loud:

I agree with #2 if you have only 1 machine to do it all and you didn't mind that it was going to run much slower than on metal. And you understood how VGPU's and pass-through (IOMMU) works...

Y'all understand that when you assign a "pass-through" device on a Type 1 Hypervisor, such as a GPU, that device is not a "shared device" with the hypervisor's hosting system itself (in practice). The host OS no longer can use it, except through a VM. Once Assigned, then it is a dedicated device to either be shared/dedicated through the VM Guests. So In practice, the Hypervisor host still has to have "a video card" that it can use, other than that, to be able to display anything from the Host OS. Of course it could always be headless, but you are wanting to see/use the VM from the same machine. I admit that I didn't really understand that concept until I did it myself 7 years ago, and came to that reality. (There were embarrassing details to that.) Then it was... Oh, of course.

KVM works, and takes some setting up to do it. You can run it from the same host that you are viewing it from. (But not from the same Video card.) That would mean an Ubuntu Host, KVM running as a service, 2 GPU's installed, Windows Guest... In that scenario, it would be processing allot" on the same machine. Host OS, VM Host service, a very demanding VM Guest, on it's own internally shared resources... Shared memory and vcpu's that you assign as an asset to that VM... A few layers there. Just saying there is a perspective to see how that would ran and use resources.

I do both KVM and vSphere. In my opinion, vSphere does shared VGPU's easier, and what I would prefer to host that... But then you need a dedicated machine just to run vSphere as a Host System. On VGPUs, you install the card, install a module, and then is menu driven to set up the pass-through to that device (which, then, shows up in the menus as a resource). No typing involved to setup the pass-through.

(Or, if you had another machine, you could also do dedicated KVM Hosting, with VGPU... More typing and finding where and how to ID that resource involved.)

Then a user of the VM would see better performance. All they are doing from their machine is rendering the graphical session. How I see that, would be to have enough hosting hardware to dedicate a modern GPU, which is many times the minimum of the program... so that you see a cost savings with a shared VGPU between multiple users. Then the users who use it do not need workstation quality machines to access the Guest and use remotely shared resources. You could be "using" it (through the VM) from a notepad. Commercial application of that as a service, is racks of shared GPU's. To me, that is where that scenario makes the most sense. 

Certainly an interesting question.

Edit: If you "only" had one machine, with one GPU, wanted "on metal" performance, wanted to continue using Ubuntu, and run that (which doesn't run on Linux), on the hardware you have... What about a dual-boot? (Ubuntu-Windows) An option. For the average user, adding more storage, today, is much cheaper than adding more GPU. Not a hit on virtualization and hypervisors at all. Just notes on IOMMU and how it is applied. Who knows, that may change in the future.

---

### Post by tenner1 on 2021-06-19
It looks like this requires me to modify the BIOS and perform numerous terminal commands. I may try it but will have to think about it,  the thing about me is that if one step isn't quite clear, I get very lost because there are terms being used that I'm not familiar with.  I wonder if this could work with my existing VM in Virtual Machine Manager and I can just do the pass-through for that.  I have a windows guest though QEMU which was set up through virtual machine manager.  It just doesn't appear to support the latest OpenGL drivers.  I followed this guide to set it up...

[https://howtos.davidsebek.com/linux-kvm-windows/step-by-step.html](https://howtos.davidsebek.com/linux-kvm-windows/step-by-step.html)

Which had me install these drivers...

[https://www.linux-kvm.org/page/WindowsGuestDrivers/Download_Drivers](https://www.linux-kvm.org/page/WindowsGuestDrivers/Download_Drivers)

---

### Post by tenner1 on 2021-06-19
[**[COLOR=#DD4814][B]MAFoElffen**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1044547")  Does that imply that in a pass-through setup the Guest and Host Machine wouldn't work at the same time?  Or that this isn't a very functional solution?  I actually have a duel boot system already but prefer using my encrypted Linux OS for security reasons.  Windows is just there to basically goof around and watch Youtube but any work I'm doing, I prefer the added security layers of having Ubuntu with encryption.   My hopes was that a Windows VM on linux would be a little more secure than a Windows host OS but I could be wrong.

---

### Post by TheFu on 2021-06-19
VMM is just a GUI over KVM. It uses libvirt, but under the covers, it is all KVM/QEMU.

I don't know of any GUI method to setup IOMMU passthru to a guest with virt-manager. It just isn't a priority, I suppose.

You'll need 2 GPUs. If your Core i7 has an integrated GPU, then that will go to the Linux host and the nvidia card has to be setup for exclusive passthru to the Windows VM.  You can run multiple VMs and access all of them, based on the system resources. Only 1 can use the nvidia GPU. All the others, including the host will be using the core i7 iGPU.  If the i7 doesn't have an iGPU, then you'll need another one installed.

Security is a completely different question. In general, the virtual machine aspect makes little difference to OS security good or bad. If you use a bridge for networking of virtual machines, then network security is a little worse than if you use IOMMU to pass a dedicated NIC into a guest VM.

Many years ago, I looked into GPU passthru. Looked at the 20 pages of instructions only to realize my $40 GPU wasn't on the "known to work" list of GPUs.  Plus, I've never had 2 GPUs inside any computer.  Graphics just isn't that important to me.

I understand that ESXi plus vsphere has a point-n-click solution for GPU passthru, but ESXi completely takes over the system and is known to be very picky about hardware.  Last time I tried to load it (11 yrs ago), of 4 computers, only 1 could ESXi be loaded. The other 3 didn't have approved disk controllers or NICs - it refused.  Also, with ESXi, you'll need a different workstation to use any GUI and you'll want a commercial backup tool to make VM backups. At a client, we ended up buying a $1000 backup program.

I suspect VMware Workstation can do GPU passthru as well. That is a $200. May want to research to good and bad about this product.  For example, when are paid upgrades needed as new Linux releases happen?  How long after a linux version is released before Workstation supports it?  It isn't days. I think it is months.

---

### Post by CharlesA on 2021-06-19
> **TheFu said:**
> 
I understand that ESXi plus vsphere has a point-n-click solution for GPU passthru, but ESXi completely takes over the system and is known to be very picky about hardware.  Last time I tried to load it (11 yrs ago), of 4 computers, only 1 could ESXi be loaded. The other 3 didn't have approved disk controllers or NICs - it refused.  Also, with ESXi, you'll need a different workstation to use any GUI and you'll want a commercial backup tool to make VM backups. At a client, we ended up buying a $1000 backup program.


Proxmox has the same type of thing for setting up GPU passthrought (or any PCIe passthrough for that matter).
[https://pve.proxmox.com/wiki/Pci_passthrough](https://pve.proxmox.com/wiki/Pci_passthrough)
[https://pve.proxmox.com/wiki/PCI(e)_Passthrough](https://pve.proxmox.com/wiki/PCI(e)_Passthrough)

However, it also runs on top of Debian with it's own kernel and whatnot, so unless you plan on using this box as a dedicated NAS or VM host, that wouldn't work very well.

Please note: You need both CPU and motherboard to support VT-D.

Here's a guide for ubuntu 20.04, but I haven't tried it on vanilla KVM:
[https://mathiashueber.com/pci-passthrough-ubuntu-2004-virtual-machine/](https://mathiashueber.com/pci-passthrough-ubuntu-2004-virtual-machine/)

---

### Post by MAFoElffen on 2021-06-19
Trying to answer all... Just remember that I try to learn from my own past mistakes. LOL

To the OP, post #5- 
> **tenner1 said:**
> [**[COLOR=#DD4814]MAFoElffen[/COLOR]**]("https://ubuntuforums.org/member.php?u=1044547") Does that imply that in a pass-through setup the Guest and Host Machine wouldn't work at the same time? Or that this isn't a very functional solution? I actually have a duel boot system already but prefer using my encrypted Linux OS for security reasons. Windows is just there to basically goof around and watch Youtube but any work I'm doing, I prefer the added security layers of having Ubuntu with encryption. My hopes was that a Windows VM on linux would be a little more secure than a Windows host OS but I could be wrong.
Some of what you are saying is true, but not overall... And others are risky assumptions. Any VM guest on a hypervisor is in a container, usually by default, shielded from the hypervisor host. The hypervisor host has hooks into the host OS to enhances it's use of hardware virtualization. When you start doing hardware pass-through's, you peal back those layers of sheilding, and open doors into the hypervisor's host OS and the physical hardware. That could be, for example, if you exposed a physical hard disk or if your case, used a physical GPU for access to your VM Guests..

Some of those resources can still be "shared" between... But in the case of GPU pass-through, at least currently, it is NOT a share resource at the Host OS and Hypervisor level. That becomes a "dedicated" resource to the hypervisor in those layers. It Is taken over by the hypervisor for a dedicated resource to be used by it's guests. So yes, you need another GPU to do pass-through.

Just a comment on (cyber) security to the outside world, On things, and access to the outside world, that is another specific subject. Linux may be less risky, than Windows, because most OS risks involve attacks against what most people use. For me, I don't limit use and security to a specific OS. Personally, if I am surfing, I setup a limited account for that purpose. If I am doing bill-pay, online banking, etc, I use a very locked down account that I just use only for that purpose. Cyber Security is a train of thought and practice. It's true, that when I setup accounts and access to remote users into a system, I create a locked down virtual instance, that is disposable. Something that is shielded and less at risk to that system. It's a train of thought and a methodology. As TheFu said, and I fully agree, Security should be practiced, immaterial to the OS you are on.

> **TheFu said:**
> Many years ago, I looked into GPU passthru. Looked at the 20 pages of instructions only to realize my $40 GPU wasn't on the "known to work" list of GPUs. Plus, I've never had 2 GPUs inside any computer. Graphics just isn't that important to me.

I understand that ESXi plus vsphere has a point-n-click solution for GPU passthru, but ESXi completely takes over the system and is known to be very picky about hardware. Last time I tried to load it (11 yrs ago), of 4 computers, only 1 could ESXi be loaded. The other 3 didn't have approved disk controllers or NICs - it refused. Also, with ESXi, you'll need a different workstation to use any GUI and you'll want a commercial backup tool to make VM backups. At a client, we ended up buying a $1000 backup program.
Agreed with all. LOL

KVM is a lot of manual work to do Pass-through. You can't do it from Virt-Manager. Think virsh or manually editing the guest XML files to use the pass-through resources, after manually configuring KVM, and using start-up scripts to expose the pass-throughs to KVM's control, in order for KVM to be able to provide the physical hardware as a resource to any guests. Even when exposed, the pass-through resources will not show up in the Virt-Manager resource menu's. It's definitely not an out of the box solution. But it is possible, it is free (cost-wise), and it does it.

KVM sits on top of a Linux Kernel. Because it runs on top of Linux Kernel, it is more open to the hardware it runs on. KVM, running on top of Linux Kernel, there are so many other Linux plug and play kinds of Linux tools that you can do for customization, management, and use with it... Which makes administration easier. But, commercially, just using a graphics layer on a production  "server", opens potential vulnerability risks. Think of the reasoning why MS "finally" realized that and went to "core" instances of server... I feel KVM does many things better and easier than Hyper-V. 

Hyper-V as a hypervisor type, is sort of a hybrid hypervisor, and you have to do "extra things" to be able to do things that are just "done" in KVM and RHEV. Some of those things are extra work, I think because of their train of though on security, you have to tell each guest instance that it can do something. (Example: For doing nested virtualization). Then in the case of doing vGPU (pass-through) on Hyper-V, it is not a "free solution", it is commercialized. You have to add more services to do that, and those services will not run or work, without purchasing additional licensing to do it. And that licensing is metered. So for a normal Win 10 Pro user, it's not really an option. It's "possible", but not without cost. True, you could add SCCM and SCCM VM Management to do some "other" VM management tasks for you, but those also come at at additional costs in licensing. (commercialized).

Hyper-V also becomes a sort of monster about the Hyper-V service and how it relates to other things. It has an EGO. It believes that if you are using it as a hypervisor, that it should have exclusive control over it's resources. It doesn't share and does not play well with other's. For instance, if you turn it on as a service, if you had type 2 hypervisors installed, those software hypervisors will no longer be able to see that your CPU is hardware virtualization capable! In other words, any VMware Player or VirtualBox 64bit guests will then fail. If you have a nested virtualization hypervisor as a guest to Hyper-V, such as vSphere, or if vSphere is anywhere in the Domain, the VMware PowerCLI (VMware PowerShell CLI module for the VMware vSphere Management APIs) fights with the PowerShell Hyper-V VM management modules. Each of those have a power struggle on who they think should be in charge exclusively! Like I said, it doesn't play well outside of it's own branded friends. And some would say, that "it takes over your machine."

VMware is just another animal. When you think ESXi and vSphere, it is a dedicated machine solution and is meant to be headless, in normal, general practice. True it "looks" Linux-like when you drop down to a shell, but it is not Linux. It does not use a Linux Kernel. It uses it's own proprietary VMware kernels, which is deeply tied into the hardware, which does use Linux-like low level toolsets. vSphere (now) is no longer ESXi + vSphere. Now they have different proprietary kernels than each other... Just to make things more confusing. I'll leave that at that, without getting into details. vSphere is a highly proprietary hypervisor solution. But it does virtualization hosting, at scale, very well. Because it's specialized to virtualization as a job, and uses it's own proprietary kernel to do that, it is not as open to the hardware it can run on. Because it is specialized and proprietary, it has a very small and secure foot print, when compared to other hypervisors.

So that is the expanded, unabridged version of  my earlier post, the why's and what each means. I always try to give people multiple options, and an understanding of what they mean.
[HR][/HR]**To summarize (here) and rephrasing what I said in my earlier post:**
 As a general user, not understanding the inner workings of KVM, you could certainly follow the guides on how to make that work on your hardware,* _if you add another GPU_*... Yes. It will work. on your hardware (*plus another GPU*), but you have to understand that it will run slow, and you may not be happy with the performance of that. "Your" hardware resources *_will_* be challenged trying to run that resource intensive application in a VM.

Or, you already have a Dual-Boot of Ubuntu and Windows, where you already have the ability to install it on Windows natively and it will run as "at-metal" performance. This does not make it unsecure, as a practice, if you take "security" seriously in your methodology and practice of it.

If your goal is that you like challenges, to explore and see if you can do it... Then, it's well worth that as an adventure, and learning process. Heck, that is why Linux is so popular. You can change things, tweak it to how you want, and learn how things work, usually for free. That is the whole adventure, right?

---

### Post by tenner1 on 2021-06-20
[B]MAFoElffen

> 
[/B]> Some of what you are saying is true, but not overall... And others are  risky assumptions. Any VM guest on a hypervisor is in a container,  usually by default, shielded from the hypervisor host. The hypervisor  host has hooks into the host OS to enhances it's use of hardware  virtualization. When you start doing hardware pass-through's, you peal  back those layers of sheilding, and open doors into the hypervisor's  host OS and the physical hardware. That could be, for example, if you  exposed a physical hard disk or if your case, used a physical GPU for  access to your VM Guests..

Some of those resources can still be "shared" between... But in the case  of GPU pass-through, at least currently, it is NOT a share resource at  the Host OS and Hypervisor level. That becomes a "dedicated" resource to  the hypervisor in those layers. It Is taken over by the hypervisor for a  dedicated resource to be used by it's guests. So yes, you need another  GPU to do pass-through.

Just a comment on (cyber) security to the outside world, On things, and  access to the outside world, that is another specific subject. Linux may  be less risky, than Windows, because most OS risks involve attacks  against what most people use. For me, I don't limit use and security to a  specific OS. Personally, if I am surfing, I setup a limited account for  that purpose. If I am doing bill-pay, online banking, etc, I use a very  locked down account that I just use only for that purpose. Cyber  Security is a train of thought and practice. It's true, that when I  setup accounts and access to remote users into a system, I create a  locked down virtual instance, that is disposable. Something that is  shielded and less at risk to that system. It's a train of thought and a  methodology. As TheFu said, and I fully agree, Security should be  practiced, immaterial to the OS you are on.
To respond to this and what **TheFu** asked about my setup. I'm running quite a decent gaming laptop but given that it is a **laptop** I'm assuming that I wouldn't have the option for a second GPU.  It has 2 RAM slots and 2 hard drive slots so there's some flexibility for upgrading but laptops as you guys probably know, have a few limitations.  I could look into it but regardless, I wouldn't have the money for an upgrade right now even if I could.   No worries though, I've been researching and found out that a program called WINE could help.....

[https://community.topazlabs.com/t/linux-support/16340/5](https://community.topazlabs.com/t/linux-support/16340/5)

I'll have to do more research on this though because the member here who claims he got this program working with the help of WINE used it in combination with something else and I'm not sure all of the steps he took.  I'd have to look into it closer but it looks like WINE can make some Windows programs run on Linux without emulation.  If I'm reading it right, WINE takes the approach of converting programs into code that other OS's can understand, (for lack of a better way to describe it)

To comment on what you said about security...

> It's a train of thought and a  methodology. As TheFu said, and I fully agree, Security should be  practiced, immaterial to the OS you are on.

100% Agreed.  I try to be smart whichever platform I'm using.  As you were suggesting more people are on Windows and therefore most viruses and hackers are writing programs that are designed to attack Windows.  I consider Linux more secure primarily for that reason but it's certainly not bulletproof.  In my mind, not being on the connected to the internet is the best way to secure a computer so I was planning to use the Windows Guest VM without it being online for a little boost in security.  Still, my host Ubuntu OS would have likely remained connected.   I suppose the nail in the coffin for only using my native Windows OS for things like movies, gaming, and Youtube, is that it isn't encrypted.  I'm definitely not suggesting Windows can't be safe to use if you make smart choices, I just consider it less secure and more intrusive for a few reasons.  The annoying forced Windows updates actually started crashing my old computer each time they ran.  It was like a double edged sword, Windows updates often came with important security updates but they force other changes that are often unwanted or aren't needed.

> If your goal is that you like challenges, to explore and see if you can  do it... Then, it's well worth that as an adventure, and learning  process. Heck, that is why Linux is so popular. You can change things,  tweak it to how you want, and learn how things work, usually for free.  That is the whole adventure, right?         

You seem very bright but have a lot more patience than I do for OS tinkering.  I love Ubuntu for the fact that it's free, highly customizable, and can be a bit more secure than Windows but am in a funny position because time is hard to come by for me.  My creative hobbies mostly involve music, photography, and writing, and that's where I generally challenge myself.  A GUI based OS in my mind should make convenience a priority.   That's my only frustration with Ubuntu, I wouldn't go as far as to say they drop the ball on this but a part of me wishes that they'd do more to make the GUI take a more dominate role over the Terminal.  I'm not knowledgeable enough on Linux to know if they could do this without impacting the customization abilities of Ubuntu though.

It took me hours and hours to figure out how to do a number of things.  For example, there was no option in the installer for creating a duel boot system with an encrypted Ubuntu OS.  I had to type miles of Terminal commands and then out of the box Ubuntu still was missing a number of key features that makes using it as easy or straight forward as using Windows.  I suppose every OS has some strengths and weaknesses but that's just my opinion.

P.S.  Thank you guys for the help, you know more about Linux than I do, that's for sure.

---

### Post by TheFu on 2021-06-20
WINE is an API layer that emulates the Windows API for Windows programs.  It is incomplete and will always be incomplete. Certain subsystems of Windows will never work in WINE.  Every year it gets a little better and a few programs "just work" without any tinkering.  None of the programs I use work under WINE without detailed tinkering and efforts to make it happen. Further, each release of WINE can break a previously working configuration.  

The dual boot issue is 50% a Microsoft problem.  MSFT had overwritten non-MSFT boot tools for a long time, so calling it **duel** boot, while funny, was correct. I don't know if that's still the situation. It doesn't matter to me. I never plan to have Windows running directly on hardware for any reason, ever again.  Virtual machines mean I can pick up the VM storage file(s), and move those to a newer machine as needed.  I have an old Win7 install that started in a KVM VM on a Core2 Duo system ---> Core i5 system ---> Ryzen 5 system. All that happened inside Windows was things got faster. It doesn't know that it isn't running on a Core2 Duo today or that the storage is now an SSD.  The decoupling of the OS from the hardware make a compelling reason to use virtual machines.  It does know that a new virtual GPU has been provided.  I switched the virtual graphics hardware from a generic VGA to a QXL driver a few years ago.  QXL is used by SPICE, which can make the fastest non-passthru hardware solution for virtual machines.  OpenGL framerates are much better using QXL and SPICE than with any other virtual solution I've seen. It is faster, by far, than x2go/NX protocols which blows away rdp and vnc stuff.

---

### Post by CharlesA on 2021-06-20
> **TheFu said:**
> It does know that a new virtual GPU has been provided.  I switched the virtual graphics hardware from a generic VGA to a QXL driver a few years ago.  QXL is used by SPICE, which can make the fastest non-passthru hardware solution for virtual machines.  OpenGL framerates are much better using QXL and SPICE than with any other virtual solution I've seen. It is faster, by far, than x2go/NX protocols which blows away rdp and vnc stuff.

Not to completely derail the thread, but did you need to do anything special to get OXL working? I've been using either "default" or "vmware" for my Displays and I haven't really thought about it since I normally don't access the console.


@OP: I can't really recommend anything other than either dual booting with Windows (which can be a pain), or installing Windows onto an external SSD and then booting off of it if you want to use Ubuntu as your main OS.

---

### Post by TheFu on 2021-06-20
> **CharlesA said:**
> Not to completely derail the thread, but did you need to do anything special to get OXL working? I've been using either "default" or "vmware" for my Displays and I haven't really thought about it since I normally don't access the console.

It is QXL (qxl), not OXL. ;)  What needs to be done depends on the guest OS.  For Linux desktops, the qxl drivers are there and "just work". For Windows, you'll need to install the Redhat drivers.  I've never tested qxl graphics performance under Windows, but it is definitely snappy.  Windows still sees it as a fake hardware driver and Microsoft programs refuse to play media using it, but other vendors/programs work fine in my extremely limited testing. [https://www.spice-space.org/download.html](https://www.spice-space.org/download.html) seems to be the place to get Windows stuff.

Perhaps my memory is faded and installing the spice server and spice agent on the remote system is necessary too. I don't recall, but the qxl stuff is part of the qemu-kvm-spice and xserver-xorg-video-qxl programs. 

Also, using either virt-manager or virt-viewer is required, since other desktop viewers don't support SPICE.  I've posted my virt-viewer scripts here before:
$ more ~/bin/regulus 
```
#!/bin/bash
GO=regulus
if [[ $HOSTNAME == "hadar" ]] ; then
    # For local connection on hadar ; hadar is usually the VM host.
    /usr/bin/virt-viewer -a -d  $GO &
else
    # For remote connections on the LAN
    /usr/bin/virt-viewer --connect qemu+ssh://hadar/system $GO &
fi
```

The Redhat Windows drivers include virtio drivers for a NIC and for disk controllers.  For the NIC, it is a good idea too, but for the storage controller, if Windows ends up in safe mode, using the SATA or SCSI drivers will make life easier for a few % of extra overhead.  When Windows refuses to boot, trying to load the "extra drivers" is necessary for virtio disk controller to work.  Just another hassle.  It has been less important since that VM doesn't run 24/7/365 anymore like it did with 7MC to record OTA TV like it did for about a decade.

Between the SCSI and SATA controller emulation by qemu, there is little difference for home users. SATA does have a lower device limit than what the SCSI emulation supports. Performance, I don't recall any difference.  I think the SATA limit is at least 10 devices. SCSI is hundreds of devices. Just depends on what you need and how the back-end VM storage is actually setup.  For Windows, I use file-based back-end storage. for Linux VMs, an LV block device is presented to the VM.

We should probably not hijack this thread any more.  For the OP, the OpenGL version supported via spice appears to be v3.1, but I've never cared much about the GL support level.
On a physical machine with a 1030 GT nvidia GPU:
```
$ glxgears 
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
270 frames in 5.0 seconds = 53.930 FPS
271 frames in 5.0 seconds = 54.150 FPS
300 frames in 5.0 seconds = 59.948 FPS
300 frames in 5.0 seconds = 59.947 FPS
300 frames in 5.0 seconds = 59.949 FPS
```

On a VM with a virt-viewer full desktop:
```
$ glxgears 
6380 frames in 5.0 seconds = 1275.865 FPS
3834 frames in 5.0 seconds = 766.648 FPS
2701 frames in 5.0 seconds = 540.048 FPS
2575 frames in 5.0 seconds = 514.863 FPS
3209 frames in 5.0 seconds = 641.702 FPS
```

The VM isn't high end.
```
$ inxi -GxC
CPU:       Topology: 2x Single Core (4-Die) model: AMD EPYC (with IBPB) bits: 64 type: MCM SMP 
           arch: Zen rev: 2 L2 cache: 1024 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm bogomips: 13973
            Speed: 3493 MHz min/max: N/A Core speeds (MHz): 1: 3493 2: 3493 
Graphics:  Device-1: Red Hat QXL paravirtual graphic card driver: qxl v: kernel bus ID: 00:02.0 
           Display: x11 server: X.Org 1.20.9 driver: none unloaded: fbdev,modesetting,vesa 
           resolution: 1680x1050~60Hz 
           OpenGL: renderer: llvmpipe (LLVM 11.0.0 256 bits) v: 4.5 Mesa 20.2.6 direct render: Yes 

```
Not a super fast VM.

---

### Post by CharlesA on 2021-06-20
Thanks for the info. I've got a setting for SPICE on Proxmox, but I haven't played with it much. I might have to check it out.

---

### Post by MAFoElffen on 2021-06-20
[SIZE=3]**I learned something new today!**[/SIZE]

Hey, this will not work for the OP because he doesn't have the right hardware, but... I  found a KVM driver that does full VGPU, that will allow installation of native graphics drivers and does it's own internal passthrough to the hardware GPU on it's own, while sharing (without requiring a second GPU). 

There is a catch... (There always is.) It was written by Intel. Requires 5th through 7th(?) Gen Intel iCores that have integrated Intel GPU's. I looked at GitHub and it is active.
[URL="https://01.org/igvt-g/blogs/wangbo85/2018/2018-q3-release-kvmgt-intel-gvt-g-kvm"]
2018-Q3 RELEASE OF KVMGT (INTEL GVT-G FOR KVM)[/URL]
[KVMGT: a Full GPU Virtualization Solution]("https://www.linux-kvm.org/images/f/f3/01x08b-KVMGT-a.pdf")
[Intel® Graphics Virtualization Technology (Intel® GVT)]("https://01.org/igvt-g")

---

### Post by TheFu on 2021-06-20
I've been watching that project for a few years.  Every demo I've seen has lasted a few minutes, then crashed. It is impressive for 2 minutes at a time.
> There is currently insufficient test coverage, so please bear with some stability issues
Gotta love that.  Every release includes "stability improvements."

---

### Post by MAFoElffen on 2021-06-20
Oh Dang! Gotta hate when that happens... LMAO!!!

What I was thinking is that my Desktop is AMD Opteron 16core, 32GB RAM, NVidia GeForce  GTX 1660Ti... All that and I can't use "that" solution... LOL

---

