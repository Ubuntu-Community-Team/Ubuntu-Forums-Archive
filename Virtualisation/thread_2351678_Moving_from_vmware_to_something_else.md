---
title: "Moving from vmware to something else?"
date: 2017-02-05
forum: Virtualisation
---

### Post by ian78 on 2017-02-05
I currently have a custom NAS box which is running Ubuntu 16.04.1 LTS  and its the only linux machine i've ever had so my knowledge in this  area is limited so i'm turning to the forums for some advice and  guidance.

As well as being a big set of disks on the network, this NAS box also has 96GB of RAM so im using it to provide a virtual server currently running VMware workstation 11. I would like to be able to run newer Windows Server 2016 VMs in the future which apparently Workstation 11 doesnt support. I have two options which are pay another £115 for yet another upgrade or move away from VMware Workstation 11 to something else. The key requirement is to do this without having to destroy and rebuild the NAS box in the process.

I have so far looked at Xen, KVM, Proxmox VE. I think Proxmox VE is out because their website says the bare-metal installer wipes all existing data. So that sort of leaves Xen, KVM and whatever else might be suggested.

I'm not especially bothered about the solution being open source although I would be happy if it was. I just object to having to shell out cash to VMware every time Microsoft release a new operating system.

Thanks
Ian

---

### Post by TheFu on 2017-02-05
I use kvm. Switched away from Xen on 1 server and VMware ESXi on another after running both for 3 yrs due to boot issues with Xen's kernels and "management pricing issues" from VMware corporate. That was around 2011 and I've never looked back or regretted the decision. 

KVM is a kernel module, not a replacement kernel, like Xen. KVM is tested by the same techniques that make Linux so very stable.  It is rock solid and VERY fast. Faster than ESX or ESXi in my configuration, plus it was much more flexible on the allowed/supported hardware. On a server, I would never use a desktop tool like VMware Player/Workstation/Server or VirtualBox.  On my main KVM server, virtualbox has locked up the entire system, not just a problem VM.

I don't run much Windows, but do have a Win7 media center running inside a KVM VM. Had to trick Windows media center into letting me use "non-local" storage. That is a limitation of Media Center, for some stupid reason, IMHO.  My network storage is faster than local storage, but MSFT thinks they know better than I do which storage should and should not be allowed.  If I ask a computer to do something stupid, that should be my choice.  This is one of the key reasons I prefer any Unix over Windows.  I run the computers, not the other way around.

Before swapping in any virtualization, it is smart to make a backup of anything you cannot loose. I doubt anything bad will happen, but you never know.

---

### Post by ian78 on 2017-02-08
Thanks for the info. I will take a look at KVM and maybe create a test VM on my windows desktop machien to have a play around with it. I tried creating a Win 2016 VM on VMware 11 the other day just out of interest and to see what happens and even though VMware says its not supported the VM does seem to be working. Whether i would want to run anything critical on it is a different story.

The one thing that iritates me about VMware workstation is when ubuntu is rebooting, say after an updated kernel is installed i have to manually go and suspend the running VMs before it reboots because even though they are configured to suspend when the system is shutting down they never do. VMware just powers them off if they are still running!  ](*,)

Time for me to go and RTFM on KVM

---

### Post by TheFu on 2017-02-08
KVM is Linux only. VMs can be any x86 OS, but the host must run Linux (to my knowledge). Also, it only works on VT-x enabled systems.  You are posting in the Ubuntu forums, so assuming you are running Ubuntu somewhere makes sense.

On Windows as the hostOS, people tend to run VirtualBox or VMware-something. 

BTW, if you are using a commercial product, seems the first place to ask for help with it would be through the vendor. Am I crazy?

---

### Post by ian78 on 2017-02-10
Yes, i do have a high(ish) powered unbuntu machine that serves as both a custom NAS and virtual server and that is currently running VMware workstation. When i said i would create a test VM on my windows desktop, i meant i would create new VM within the Windows 10 Hyper-V client, configure the VM for nested virtualisation, install ubuntu & KVM in that new VM and have a play. I am actually doing this at the moment whilst i type this message and crikey its slow. :sad:

I currently have a Win 10 VM within KVM installing at the moment and it has been installing for well over an hour now. Generally a Windows 10 VM will install in my Hyper-V client in about 10-15 minutes. I will leave it overnight and see what state it is in tomorrow morning.

I know VMware is a commercial product, but i doubt im going to get an unbiased response if i ask them what other virtualisation platform I might use to replace their software.

---

### Post by TheFu on 2017-02-10
I know my Ubuntu Server installs take 15 minutes.  Haven't installed Windows in 4-7 yrs, so can't help with that.

For any virtualization, the performance is based on providing only the needed system resources required for the VM.
* Always use VirtIO for disks and networking - for Windows, these are add-on drivers that can't be installed until after the initial install is completed
* Always leave 1G for the hostOS (512MB for Linux servers).
* Never overcommit disk, RAM, CPU
* if the guest has a GUI, provide the correct GUI interface drivers and video-RAM. Usually QXL for Spice is what you want, but that doesn't work for Windows without add-on drivers that can't be installed until after the initial install is completed.
* if a GUI is used on the guest, use a minimal GUI - avoid any that require 3D video accel.

All my Windows knowledge stopped with Win7.  Touched my first win10 system 2 days ago at a store.  Could feel the privacy being sucked away. ;)

---

### Post by heiko_s on 2017-02-13
Running a Windows 10 VM on Linux/KVM running as a Windows 10 Hyper-V client, that is running a nested virtualization, is not going to break any speed records. It may work for a demo, but I wouldn't try it for anything productive.

I'm currently running a Windows 10 VM on Linux using KVM and it performs very well. Have a look at this video to get some idea: [How fast is KVM? Host vs virtual machine performance!]("https://www.youtube.com/watch?v=Ww2xpxkhitk&t=5s")

A year ago I switched from Xen to KVM. Both are great, but Xen has more limitations regarding hardware.

You can run an Ubuntu server with no GUI and one or more KVM VMs, which can be Linux or Windows, whatever you like. I run a Linux desktop for everyday stuff and start a Windows VM for photo editing under LR, PS, etc.

KVM (like Xen) allows you to pass through PCI devices to the guest, for example a graphics card. I have one GPU for the Linux host and another one for the Windows VM, which uses it's Windows-native drivers. This way I get about 95% of a Windows bare metal installation, good enough to do about anything you can think of in the VM, including 3D gaming or photo / video editing on large files. The downside of this way of virtualization is that you need a CPU and motherboard that supports IOMMU or VT-d (Intel terminology) in addition to VT-x that was mentioned before. And you need 2 GPUs (one could be the IGD of the CPU). The setup can also be a little challenging.

Xen, while an excellent virtualization environment, has a number of limitations:
1. No proprietary Nvidia graphics driver on the host (if you run it as a server with no GUI, that's a non-issue).
2. No support for Nvidia graphics pass-through, except for the expensive Quadro-2000 and above pro models.
3. The Xen architecture is a little more restrictive, as it's a real hypervisor and the Linux dom0 (administrative domain) is nothing but a privileged VM. For example, you wouldn't be able to install VirtualBox (at the time it didn't support nested virtualization).
On the plus side it has better documentation, in addition to great performance.

KVM is more flexible with regard to hardware. It's main plus is that it runs just like another task on the Linux machine. Unfortunately there isn't any good, up-to-date documentation. The development of KVM is so fast that things change all the time, and I guess the developers don't find the time to sit down and write some decent manuals (Alex Williamson is perhaps the exception, he provides very good info in his blog: [http://vfio.blogspot.com/]("http://vfio.blogspot.com/")). The [http://www.linux-kvm.org]("http://www.linux-kvm.org/page/Main_Page") website seems quite outdated.
Anyway, there is a hype around kvm and performance is good.

---

### Post by TheFu on 2017-02-13
Just to clarify, for non-GUI workloads, 90-95% of native performance is easily possible without much effort. Getting video passthru working used to be extremely hard. NIC and storage passthru isn't nearly as difficult. For most workloads, none of that is necessary, just use the virtio drivers. 

Most people don't interface directly with KVM, they use some libvirt client.  Libvirt is a hypervisor-independent layer to make end-user tools easier to create.  All of this is under very active development.  In 2010, kvm was extremely stable and ready for production.  Since then, it has only gotten better, libvirt has improved tremendously and the main 3 end-user tools are much more capable too - virsh, **virt-manager** and virt-install.  The defaults for libvirt and virt-manager are pretty reasonable these days too.  libvirt supports containers now, if that is of interest, in addition to kvm, xen, virtualbox and some VMware products.  

There are a few caveats with kvm last time I looked - brtfs had issues with it. There was some manual setting to help, but it is just easier to use **any** other Linux file system.

---

### Post by DuckHook on 2017-02-13
@OP

Though it has been mentioned in passing, for the sake of completeness, you may also wish to give VirtualBox some attention. For the general user, and especially one not too familiar with Linux, the biggest feature that VBox has going for it is user friendliness.

**Full Disclosure**

I am attempting to move away from VBox. Have been running 5 flavours of 'buntu on KVM for a few weeks now and am *very* impressed. Speed is better, it runs natively in the kernel, and I just feel better using it because it is FOSS. But, to be frank, it is undeniably more geeky. Anyone who is serious about it will have to delve into CLI wizardry with stuff like:```
virsh edit name_of_vm
```…and then monkey around in XML files. With VBox, it's very user-friendly with the most important stuff accessible from a well-designed GUI app.

Keep in mind that gurus like TheFu and heiko_s are unfazed by arcane commands and complexity. Though I consider myself a power-user, the learning curve to KVM was (and is) not trivial. I can well imagine that it would appear daunting to the general user. But as in all things Linux, the flip side of complexity is greater power, finesse and control.

---

### Post by TheFu on 2017-02-13
Dude - load up **virt-manager** - the GUI is almost the same as virtualbox, just with more power.
[https://help.ubuntu.com/community/KVM/VirtManager](https://help.ubuntu.com/community/KVM/VirtManager)
or 
[http://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/](http://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/)
explain.

---

### Post by DuckHook on 2017-02-13
> **TheFu said:**
> Dude - load up **virt-manager** - the GUI is almost the same as virtualbox, just with more power.
[https://help.ubuntu.com/community/KVM/VirtManager](https://help.ubuntu.com/community/KVM/VirtManager)
or 
[http://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/](http://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/)
explain.):P

I do use Virt-Manager. But you can't, for example, move/rename the qcow2 image unless you dicker with the XML file. I've also run into display issues on which I've just now had to turn to the forums for help. Even creating a shared directory between guest and host is more involved than it is in VBox, necessitating a fstab entry. Having said all of that, I'll be the first to admit that I've only begun my explorations. I may simply be doing things stupidly (it wouldn't be the first time).

---

### Post by TheFu on 2017-02-14
> **DuckHook said:**
> ):P

I do use Virt-Manager. But you can't, for example, move/rename the qcow2 image unless you dicker with the XML file. I've also run into display issues on which I've just now had to turn to the forums for help. Even creating a shared directory between guest and host is more involved than it is in VBox, necessitating a fstab entry. Having said all of that, I'll be the first to admit that I've only begun my explorations. I may simply be doing things stupidly (it wouldn't be the first time).

Well, you can do it without touching XML, but modifying the XML is 50x easier. ;)  Just change 1 line with the path. Moving an image file around is one of the few (only?) times I've needed to touch the XML in 5+ yrs for KVM. Everything else that isn't networking has been done through the GUI. I manage the bridges outside virt-manager, but most people running a desktop inside the VM wouldn't do that.

My KVM servers are headless (that means without a keyboard, mouse, monitor).  Treat every VM like it is a separate physical machine across the country. Do everything through the network. Use a remote desktop if you need a desktop. Use network-based file sharing if you need that. Works perfectly. I only use virt-manager as a GUI when console access is needed - that happens if networking fails. Other than that, virt-manager is used at install time and never again. Spice started "just working" for me on 16.04. I don't use it, however. Spice is fine on the LAN, but securing it for use around the world takes more. The same would apply to virtualbox.
My primary desktop (which I'm on using x2go writing this) runs inside a KVM VM in my private cloud. It is available from anywhere in the world with a minimal internet connection.  It also works when sitting 2 ft away. ;)  I mostly run servers, so ssh is really the only desired interface. 

It is possible to share files without touching the fstab - use autofs - but the fstab is easier for most people. I prefer autofs for a number of reasons and use it for all NFS, CIFS, and temporary USB storage. It does take a little setup using multiple files. I avoid using CIFS/Samba - it is too limiting and slower than NFS. Storage on the network should behave like local storage. NFS does that. CIFS does not.

However, if you want cheap, redundant, storage, qemu/KVM has **sheepdog** support. That doesn't work with any other hypervisor. Basically, it is replicated, block, storage for virtual machines (sorta).  

Need to do anything non-standard with the host networking?  KVM won't freak out. Anything that Linux networking can do (which is anything), can be done and kvm will work with it. Need 5 10G bonded links? No problem.  Want to use wifi on the host? That can be done, but it isn't a good idea.  Still, you can do it.

---

### Post by heiko_s on 2017-02-14
> **DuckHook said:**
> ...Keep in mind that gurus like TheFu and heiko_s are unfazed by arcane commands and complexity. Though I consider myself a power-user, the learning curve to KVM was (and is) not trivial. I can well imagine that it would appear daunting to the general user. But as in all things Linux, the flip side of complexity is greater power, finesse and control.

1. I'm totally flattered being called a "guru". I'd rather call myself an ordinary user with a purpose who doesn't give up easily. About 5 years I started on my quest to get Windows running in a VM with near-native performance. The first 3+ years it was Xen, now it's KVM. Else than doing that I know very little. So if the OP is willing to take the (bumpy) ride to KVM heaven (or whatever), why not? As long as he's aware of the benefit versus effort.

2. For a little Windows Office or basic 2D applications, VB is an excellent tool that is easy to use, far easier than kvm and virt-manager / virsh / qemu (command line). Not only is VB very easy on the user, it has excellent and in-depth documentation!

3. With the right hardware (VT-d / AMD-v support), kvm is more powerful, for example doing things like VGA passthrough. Unfortunately, the documentation sucks and you have to search for answers all over the net.

---

### Post by TheFu on 2017-02-14
> **heiko_s said:**
>  
3. With the right hardware (VT-d / AMD-v support), kvm is more powerful, for example doing things like VGA passthrough. Unfortunately, the documentation sucks and you have to search for answers all over the net.

Different needs for different people. I love the flexibility available.

If you remove the VGA passthru, virt-manager is pretty simple for Linux VMs.

---

### Post by DuckHook on 2017-02-14
> **heiko_s said:**
> …Not only is VB very easy on the user, it has excellent and in-depth documentation!…

…kvm is more powerful…Unfortunately, the documentation sucks and you have to search for answers all over the net.This was/is my experience too. KVM documentation is very Spartan whereas the VirtualBox users manual and wiki are very complete and helpful. Linux power users will tend to find their way around KVM, but it is not easy going for the general user.

I don't know which category the OP considers him/her/self in. I do know that, as one's KVM skills improve, that TheFu's observations are correct and KVM is just more powerful and versatile.

I don't use passthrough or any other highly technical setup, but having just migrated a simple Xubuntu VDI image into qcow2 and running the exact same VM under KVM, I can attest that everything from videos to surfing to app execution is faster than it was under VBox.

---

