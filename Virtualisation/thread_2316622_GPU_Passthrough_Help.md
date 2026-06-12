---
title: "GPU Passthrough Help"
date: 2016-03-09
forum: Virtualisation
---

### Post by Lyxnx on 2016-03-09
I'm in the process of upgrading to an Ubuntu based distro (I'm thinking of Linux Mint or something like Xubuntu as I can't stand unity) but I was wondering how I can setup GPU passthrough using my CPU integrated graphics for the host and my discrete GPU for the VM. I'm not new-new to Linux but I'm not experienced either so you won't need to treat me like I'm a first-timer (used to run ubuntu, arch linux and linux mint then I transferred back to windows as it had better support for games.)
Currently I'm dual booting windows 7 and manjaro but I can't find many guides so I think I'll swap to Ubuntu because the community support seems much better and dual booting is a pain for me so it would be preferable to run windows in a VM on one monitor and have Linux on the other.

**My specs:**
Intel Core i5-6600K CPU
Gigabyte GA-Z170XP-SLI motherboard (**with** VT-d support **and** enabled)
NVIDIA GTX 960 Windforce 4GB GPU

---

### Post by MAFoElffen on 2016-03-09
Have you ran VM guests before and from what Hypervisor? (VMware player, Virtual box,  etc...) Some., like Vrtual Box, which the addition of there extra tools, will allow extended graphics from the host. VMware has a different strategy There free Player, does not allow passthrough to the host GPU... but their higher end (paid) products do. KVM will let you, but is an advanced configuration affair (manually editing files).

---

### Post by Lyxnx on 2016-03-10
No I haven't but I've seen it done using qemu or something.

---

### Post by MAFoElffen on 2016-03-10
No experience with a hypervisor or virtualization... Do you feel comfortable with your Linux commandline skills?

What are your goals and requirements? What is your system specifications of what you are running?

Because reading your first post > being dis-satisfied with the look and feel of the Graphical User Interface  of your desktop manager (unity)... you could just install another desktop manager of what you want onto your existing system, with having to run something in virtual... My server console here has unity, lxde, gnome, xfde, etc. installed concurrently. When I get bored, I just log into a different GUI desktop.

I don't want to dissuade someone from using and playing with virtualizations, but it seems like that is what fills the needs and requirements that you mentioned. Just throwing that out there for thought.

If you want to do more than that, then...

---

### Post by Lyxnx on 2016-03-10
1) I use virtualbox for testing systems before I actually put it on native hardware.

2) I feel like I can get jobs done via the CLI. 

3) I aim to remove the original windows installation and replace with Linux entirely and launch qemu or whatever whenever I want to play games so I don't have to deal with rebooting to play games and reboot again to Linux. 
Specifications are in first post. 

4) It's not the GUI I'm unhappy with, but I'm unsure of what I'm going with at this point which is why I'm testing different flavours and derivatives in virtualbox. 

Switching DE isn't what I'm after; playing high end games (gta v, witcher 3 etc) without having to reboot into windows is. 

I haven't seen many guides for KVM/qemu passthrough for ubuntu which is why I ask here - the ubuntu support is one of, if not the largest, supported distros.

---

### Post by MAFoElffen on 2016-03-10
Well then. Since you say you have experience with VirtualBox, then that is a start. That is more experience than than "none".

If you have a CPU with VT-x or AMD-v support, then you can run 64 bit operating systems and use virtual hardware sharing from your host. If you have a high end GPU, then you might be able to use some of the advanced features from it (in different ways with different hypervisors.

VirtualBox, VMware player and Qemu are type 2 hypervisors, meaning that they simulate hardware virtualization through software. If you had used the old Virtual PC, that was in this category.

With Virtualbox, if you use thier tools extension packs, you can use extended features of your high end video card and sound card. VMware Player does not. VMware's philosophy varies, in that they have paid products higher up their chain that allows you to use host graphics. (VSphere and Workstation Pro, which are both type 2 hypervisors.) Both those are GUI driven and easy to use. Qemu is mostly commandline... although it is possible to use Virt-Manager with Qemu.  In fact, you can passthrough hardware manaully with QEMU.

The plus side of a type 2 hypervisor, is that you can run a 32 bit VM on a 32bit CPU or a 64 bit CPU without VT-x capabilities. Slow, but possible. The extended hardware features will be limited.

Enter in type 1 hypervisors. The hypervsiors include VSphere, VMware Workstation Pro, KVM, Xen, Hyper-V, etc. These are virtualizations on metal, which means they use the virtualization features of CPU (VT-x or AMD-v) to virtualize the shared resources for a VM guest. The Workstation Pro does this with GUI menu's. Other Linux based hypervisors, well, mostly manual configs using commandline such as utilities like Virsh.

virt-manager is a gui driven user interface that is a visual shell over the virsh tool-set. That means it allows you to pick, choose, select and not have to remember the cli commands. It also has a good interface to see you VM visually through it's internal VNC or Spice interfaces. You could always use other RDP managers...

I followed these 4 guides as reference:
[http://ubuntuforums.org/showthread.php?t=2266916](http://ubuntuforums.org/showthread.php?t=2266916)
[https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/](https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/)
[http://www.se7ensins.com/forums/threads/how-to-setup-a-gaming-virtual-machine-with-gpu-passthrough-qemu-kvm-libvirt-and-vfio.1371980/](http://www.se7ensins.com/forums/threads/how-to-setup-a-gaming-virtual-machine-with-gpu-passthrough-qemu-kvm-libvirt-and-vfio.1371980/)
[https://wiki.archlinux.org/index.php/PCI_passthrough_via_OVMF](https://wiki.archlinux.org/index.php/PCI_passthrough_via_OVMF)

It worked. I did it and went on.

Although I use Hyper-V, VSphere (ESXi), KVM, Xen, Docker (Linux and Win Server 2016), and LXC. I don't do GPU passthrough for gaming. I've done it, but couldn't accept the lag. I have Opteron 16-core CPU's with SLI NVidia GT980 ti's and three 30 inch monitors.... not a hardware issue of running virt's. Just faster running games native.

On another PC... I am happier doing a dual-boot on for gaming (performance-wise), than doing pass-through.

For FYI, there is another type of virtualization on the cusp. I'm doing it now, running containers straight from the Linux Kernel (systemd, machinectl), without any hypervisor... That kind of technology should change how and what we can do with VM's... Next is to test Win Containers from Linux...
[http://thenewstack.io/the-windows-and-linux-container-era-is-here/](http://thenewstack.io/the-windows-and-linux-container-era-is-here/)
[http://blogs.msdn.com/b/stevelasker/archive/2015/08/24/deploying-to-linux-amp-windows-docker-containers.aspx](http://blogs.msdn.com/b/stevelasker/archive/2015/08/24/deploying-to-linux-amp-windows-docker-containers.aspx)

---

### Post by Lyxnx on 2016-03-11
Thank you for taking the time to explain everything. 
I will try those links of guides you posted and see if I have any success. 

Another thing - if I use 2 monitors, 1 for Linux and one for Windows, where do I plug them in? Gpu or regular output ports? I want to use both monitors with Linux and as soon as I start windows, linux goes to the right monitor and I have windows on my main one.

---

### Post by MAFoElffen on 2016-03-11
When I did it, Those guides I linked to, that I followed, had one to the internal and other another, or others to your high end gpu. The end end GPU was blacklisted by linux, so it would not be used. It was used soley by the Virtaual, in a past through.

I talked  (through posts) with someone here, who did it with ESXi 6, who had his high end, with one montitior, and did not use another gpu. He said his moitor would turn on and off when it staring the VM, durng the transition... but that he would not be able to jump between his virtual guest and his host sessions without problems... So I guest at the present, there still might be concessions(?) I here Workstation has that worked out but costs...

---

### Post by Lyxnx on 2016-03-11
So you're saying I won't be able to use 2 monitors at once? 
If I were to plug my main monitor into the integrated output slots and run a VM and play a game, would it output still?

---

### Post by MAFoElffen on 2016-03-12
That is what I said... While doing the passthrough, what I figured out was happening, was that the devices you pass through are 'blacklisted' to the host system, which tells it, when you boot into your host Linux operating system, do not use those devices. Then your guest VM, when it boots, uses those devices. (otherwise, those are still dark, off, unsused until then...)

My type 1 hypervisors are on servers... so they cannot even run those guests. With one of my gaming pc's. that I did it with.. it was one of the 3 monitors was running the host OS and the other 2 where running the guest.

Like I said, someone here was running ESXi and told me he is running a pass-through differently, where it is only using one gpu and monitor. He said it he starts his vm up, the monitor goes black for a few moments while it hands off form the host to the witch between the guest and host... except via shutting down the guest, where the GPU transitions back to the host. That is 'all' he described to me. I tired to get more out of him, on how he did it... but to no end beyond that.

There must be a way, because VMware VSphere + NVidia Grid does it... and so does VMware Workstation Pro, right? Someone else please juump in and tell me about how Workstation Pro does it(?) I registered for a trial of NVidia Gird... but never heard back from VMware. Their registration for that requires a business name, so I'm thinking that one is pricey). I dl'ed a trial of Worksation, but I have to wait to free up a machine to test it on before I install that...

Seriously, If the paid VMware products can do it without wasting my hardware (periods of unuse) and performance was good... I would buy them. I went back to native on-iron gaming because of those 2 issues.

---

### Post by ubuserone on 2016-03-23
May I know , how much possible for a user rookies without much knowledge on linux coding to successfully doing the passthrough ?
The requirement for basic hardware , compile kernal and sort of stuff really looks hard to read and understand it.

I have a dual boot windows 7 and ubuntu 14.04 but I would like to have a passthrough for some programs or light games to test out.

What's the best freeware application for easy gui less technical way ? QEMU + KVM ?

---

