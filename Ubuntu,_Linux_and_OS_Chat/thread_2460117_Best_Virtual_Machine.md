---
title: "Best Virtual Machine"
date: 2021-04-02
forum: Ubuntu, Linux and OS Chat
---

### Post by thumper76 on 2021-04-02
I'm looking for the best Virtual Machine to run on top of Ubuntu 20.04. I've read that KVM is built into the Linux kernel. Would that be the best choice? Or are there advantages to other versions? Is it better to run two operating systems as dual boot or is it better to run one in a VM ? Advice appreciated!

---

### Post by DuckHook on 2021-04-03
> **thumper76 said:**
> I'm looking for the best Virtual Machine to run on top of Ubuntu 20.04. I've read that KVM is built into the Linux kernel. Would that be the best choice? 
The answer to a question such as yours can only be "it depends".

KVM is indeed built into the kernel, but then, so is Xen. They are both paravirtualized VMs which means that they operate with one toe touching the bare metal HW. This makes them very efficient since they can use some elements of actual hardware instead of having to do everything through strictly software translation. Maintaining security integrity in a paravirtualized environment is more challenging though, so from time to time, there have arisen security implications. These tend to be patched quickly, but it is important to understand the exposure.

Pretty much every VM these days make use of the hardware hooks that CPU manufacturers build into their chips. But the fact that KVM and Xen are also built into the kernel is bound to make both of these VM engines more efficient.
> Or are there advantages to other versions? 
Since I run both KVM and VirtualBox, I must say that VBox is easier to use and more "intuitive" for people coming from Windows or Apple. It conforms more to the conventions that general users have been steeped in, and it requires fewer steps to get running. My biggest beef with VBox is that if you want it to be properly useful, then installing those useful "extras" requires an add&#8209;on that is closed source and proprietary. We have to take Oracle's word on it that they aren't, for example, spying on us. Notwithstanding such concerns, I have it installed to run an old isolated instance of XP which I did not initially set up properly to be cross platform compatible so that it could run on KVM.
> Is it better to run two operating systems as dual boot or is it better to run one in a VM ?
Again, it depends. No VM will run as fast as an OS installed on bare metal. So if it is speed and computing efficiency that matter above all, you will want dual boot. OTOH, a bare metal install cannot provide the sandboxing that is a VM's strength. So if it is security that matters most, a VM is better. Dual boot is better for system redundancy (if you mess up one partition/install, you can log into the working one, then chroot into the borked one to attempt rescue). VMs are better for easy snapshots/restores.

To make things even more interesting, a third option exists these days by way of containers. If interested in those, see the link in my sig: *Sandboxing Apps with LXD*. I do not recommend containers for newbies or those who are allergic to technical challenges. They are not trivial to implement.

To give you a sense of the various possibilities, I have three OSes on my main box, so it is not only dual boot but triple boot. Within each of those OSes are both VBox and KVM virtual machines. However, I have found over the past few years that I am migrating the majority of my apps from VMs to containers, so each of those OSes also run LXD. This is meant to illustrate that it is not necessary to look at VMs as standing in opposition to dual boot. They can be mixed and matched. That's the power and flexibility of Linux.

---

### Post by TheFu on 2021-04-03
As DuckHook says above, "it depends."

What is "best" depends on a number of factors.  For most people, the least evil system to start out with on a Linux hostOS would be virtualbox. As you learn more, you might find that other hypervisors are more stable and faster than vbox.  Of course, there are also political and practical considerations for any choice of virtual machine system.  Each has different levels of GPL support - from ZERO to full and many levels in between.

All Linux-based virtual machine managers leverage Paravirtualization extensions. 
[https://en.wikipedia.org/wiki/Paravirtualization#Linux_paravirtualization_support](https://en.wikipedia.org/wiki/Paravirtualization#Linux_paravirtualization_support)

I haven't dual-booted in about a decade.  Once you know how to tune a virtual machine, there is little need for that 5% greater performance that running an OS directly on physical hardware can provide.  The big gotcha is with high-end graphical programs and very fast games.  Those are almost always best run directly on hardware to provide direct access to the GPU.  Inside a virtual machine, all the real hardware isn't usually available, just access to virtual hardware.  So - your Gee-Wize 2060 GPU never gets seen inside any VM.  Rather a simulated generic 2D GPU is presented to the VM guest.  The same applies for network cards, storage, even the CPU is virtual inside a VM.  In fact, most virtual machines perform faster and with fewer resources when vm-specific drivers called "virtio" are selected for the network cards and storage controllers presented to each guest VM.  I routinely see 25 Gbps transfers between the host and guest VM over the network when virtio is used.  But if I use a virtual PRO/1000 NIC, then the performance drops to about 940 Mbps - similar to what a real GigE NIC would provide.  How much does that matter? Usually it doesn't, but we could accidentally pick a virtual NE2000 NIC which provides 10 base-tx performance.  We would certainly feel that.

You may see marketing materials claiming that a "type 1" hypervisor is better/faster than a "type 2" hypervisor.  Again, the answer is "it depends."  A type-2 hypervisor on an OS that is setup to run specifically as a VM host isn't slower, at least not in my tests on identical hardware.  Then there are all the GUI-based hypervisors which seem to be slower than the enterprise hypervisors.

I can only suggest that you read up a little on the most popular hypervisors
[LIST]
[*]xen
[*]kvm
[*]VMware ESXi
[*]Proxmox
[*]Gnome Boxes [https://arstechnica.com/gadgets/2020/04/virtualization-on-the-linux-desktop-gnome-boxes-vs-virt-manager/](https://arstechnica.com/gadgets/2020/04/virtualization-on-the-linux-desktop-gnome-boxes-vs-virt-manager/)
[*]Virtualbox [https://askubuntu.com/questions/101449/gnome-boxes-vs-virtualbox](https://askubuntu.com/questions/101449/gnome-boxes-vs-virtualbox)
[*]VMware Workstation
[*]VMware Player
[*]Qemu
[/LIST]
I grouped them in order/together based on Enterprise use for servers.  If you plan to run only desktops with GUIs inside VMs, then look at Gnome Boxes and VirtualBox.

---

### Post by thumper76 on 2021-04-04
Thanks for the replies.Lot of info to evaluate.

---

### Post by kevdog on 2021-04-05
@DuckHook

Thanks for mentioning of containers.  Great post BTW - really informative and thorough.  I'm aware it took awhile to type all the information.  I'd only like to add that if/when you google containers -- a lot of information is going to come up about a product called Docker.  I kind of think of Docker as the posterchild for containers, although there are a lot of container platforms.  Docker is super easy to implement.  I'd say it's easier than working with KVM initially, however maybe that's perhaps since a lot of concepts relevant to VMs can be used on Docker so it's possible I went through the learning curve with VMs.  Docker is really good if you want to run a singe server -- for example nextcloud, bitwarden, let's encrypt stack, etc.  If you are using containers, treat them a machine that does one and only one thing -- not multiple like you're installed Ubuntu installation.  

I'd lastly just like to throw my hat in the ring and address the concept of hypervisors from a noob point of view since I only started working with them about a year and a half ago -- well I had used VirtualBox for many years, but for some reason I don't actually perceive this as a hypervisor --- it is technically however the performance isn't great.  When exploring hypervisors at first the landscape is really confusing, and there are a lot of command line arguments you'll need.  I'm not much of a GUI type of guy, however it's really useful as a beginner to use some GUI tools to get your VMs up and running and to be able to monitor them, and be able to spawn a CLI within the VM.  I'm aware there are tools such as VirtManager you can use within Ubuntu, however I really needed a lot more hand holding at the beginning. I actually watched a lot of videos on youtube and such looking for options with add on tools that would help with the initial setup. I also gravitated toward more Type I solutions however I'm not sure that's totally relevant.  After a ton of reading, it basically boiled down to me to three options -- Proxmox (which runs on top of Debian), ESXi (Oracle product which I believe is free if running less than 50 VMs), and Xen.  I didn't want any future problems with perhaps Oracle doing what they have done in the past, so I kind of crossed ESXi off the table -- however this option is really really popular with businesses.  With Xen I didn't really want anything to do with Citrix, however there is a open-source version of the xen hypervisor known as xcp-ng which runs on top of CentOS.  I tried both ProxMox and xcp-ng, but to make a long story short, for my first project I ended up with xcp-ng -- mostly due to a series of videos from Tom Lawrence who basically walks you through how to install the hypervisor from scratch, how to initially configure the hypervisor, and how to install Xen Orchestra (GUI frontend for xcp-ng which is http based) and Xen Center (another GUI frontend for xcp-ng but only works on Windows).  After installing the hypervisor I went on to virtualize many Ubuntu and Arch Linux installs and overall the setup works great.  I don't have any connection to Tom Lawrence or make money in any way from him, however for a really easy easy first step with simple instructions and video demonstrations, he does a super nice job showing how to get the setup up and running.  xcp-ng forums are pretty active when you have a question and even Tom Lawrence has his own forums which people answer questions regularly.  For my next Type I Hypervisor installation, I'll probably go with ProxMox now that I know a lot more about hypervisors at this point, and for the reason I'd like to learn and know more with working with this system, since Proxmox is a very widely used project.

With any Type I hypervisor solution however, you'll have to basically blow away your Ubuntu install and install the hypervisor, and then virtualize Ubuntu within the hypervisor.  This may or may not be want you want to do so just do your research to see if these two solutions meet your needs.

---

### Post by scorp123 on 2021-04-05
As others have already said: "It depends."

Me personally I need to test new distribution releases (e.g. Oracle Linux, Alma Linux, etc.) against software that was written by our own in-house developers and I need to make sure there are no broken dependencies or other "surprises", before I can deploy those distributions for real. And because I have many computers (both at work and at home) that are running many different OS (e.g. Ubuntu, Mac OS, Windows 10 ...) I prefer a solution that lets me copy one VM from one OS to another without having to change anything: **Virtualbox**.

Virtualbox exists for Linux, Mac, Windows ... so whatever I do to a VM at work (e.g. on a Linux desktop) I can copy it over to my MacBook, continue my experiment, and then copy the result to a colleague who's running Windows to get his input too ...

As was said before: "It depends."

For me being able to transport my VMs between various OS such as Mac, Windows, and Linux without running into too many hassles means I probably want Virtualbox. But that's just me and the scenario that fits me best.

---

### Post by TheFu on 2021-04-05
> **kevdog said:**
> ....
After a ton of reading, it basically boiled down to me to three options -- Proxmox (which runs on top of Debian), ESXi (Oracle product which I believe is free if running less than 50 VMs), and Xen.  I didn't want any future problems with perhaps Oracle doing what they have done in the past, so I kind of crossed ESXi off the table -- however this option is really really popular with businesses.  With Xen I didn't really want anything to do with Citrix, however there is a open-source version of the xen hypervisor known as xcp-ng which runs on top of CentOS.

ESXi is from VMware.  VMware makes 6 hypervisors the last time I checked. Think 2 are End-of-life.
[LIST=1]
[*]* VMware Player
[*]* VMware Workstation
[*]* VMware Server (dead?)
[*]* VMware Fusion
[*]* VMware ESX (EoL?)
[*]* VMware ESXi   + vSphere
[/LIST]
My take on each.
[LIST]
[*]Player is like Virtualbox. Free and mostly easy to use. Enterprise capabilities not included.
[*]Workstation is for commercial use in development and testing places. Very stable.  In forums, the main complaint is about not supporting unsupported versions of OSes. 
[*]Last time I used "Server" was around 2005. That was long before Player existed.
[*]Fusion is for OSX desktops - perhaps limited to only Intel Macs.
[*]ESXi is a stripped down version of RHEL that VMware has called their own for a long time. [https://en.wikipedia.org/wiki/VMware_ESXi](https://en.wikipedia.org/wiki/VMware_ESXi) Initially, it was a free, "lite" version of ESX, but VMware management decided to just rename ESX to ESXi ... and change the license model, pricing, etc.  Those changes had my company drop using ESXi and suggesting it to our clients. Some were being hit by bills that were 2x higher.  We moved them to KVM + libvirt + virt-manager and never looked back. ESXi takes over an entire system. No desktop. Extremely limited local logins.  Backup tools generally run $1000 to start.  ESXi is **very** picky about hardware.  Of 4 systems here, it refused to load on 3 of them. It didn't like the SATA controllers or the NICs.  To be fair, they were cheap, so ESXi HW requirements are a type of problem prevention. As I get older, I appreciate that.
[/LIST]

Oracle makes VirtualBox. Others have covered that above already.

Proxmox takes over an entire system. Access is through a web interface. Multiple Proxmox systems can be placed into a cluster with failover.  Underneath, it is KVM and Docker containers.  Almost like a web interface to a VPS is my impression.

I ran Xen for about 3 yrs in production at the same time we were running ESXi. It can be loaded onto most of the popular distros and integrates with the Linux Kernel, though not as cleanly as KVM does.  That kept Xen out of the linux kernel for a number of years.  Xen-ng provides a pretty interface and overview of the different systems.  Functionally, I don't see much difference between Xen and KVM, though in my production experience Xen had more problems.

I've never regretted changing to KVM from any other tool - virtualbox, Xen, ESXi, Workstation.  KVM can do some amazing things. The local and remove graphics through the Spice protocol are pretty amazing without going through PCI GPU passthru.  Gnome Boxes should work about the same, since it is based on both KVM and Spice. [https://help.gnome.org/users/gnome-boxes/stable/supported-protocols.html.en](https://help.gnome.org/users/gnome-boxes/stable/supported-protocols.html.en)  Spice can be used with KVM remote access. For almost all uses, it feels like native performance.

For someone new to virtualization and linux, the choices really come down to Virtualbox or Gnome Boxes, IMHO.  If work or college provided VMware Workstation licenses, I'd probably use those.  Think they are a little over US$100 typically.  

Using virtualbox inside a company requires paying for a license, with just a few exceptions for limited trials. It definitely is not free software.  Virtualbox appears to phone home based on Oracle tracking down some large corporate deployments and demanding payment.  [https://www.theregister.com/2019/10/04/oracle_virtualbox_merula/](https://www.theregister.com/2019/10/04/oracle_virtualbox_merula/)  The amount of money they wanted didn't seem too bad, except they were demanding it from a company that claimed they don't use it at all. The IP address space was shared with home DSL users, which are sorta the definition of allow users for VirtualBox free use.

Moving VMs between systems is something I think all of them can do.  I've converted ESXi, Xen and VirtualBox VMs to be used by KVM.  There's a tool - qemu-img that does this.  The trick is to have the hypervisor setup to present the same hardware in the new system as the old.  Most of them all use very standardized virtual hardware or virtio drivers, so this isn't hard at all for non-Windows systems.

---

