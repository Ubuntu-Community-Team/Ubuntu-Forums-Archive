---
title: "New project - Need Help with Picking Hypervisor"
date: 2009-09-29
forum: Virtualisation
---

### Post by smc18 on 2009-09-29
Hey guys,

I am halfway in my planning for my virtualization project at home. I've bought my hardware and now I'm looking for the most efficient hypervisor/software solution.

Hardware Setup
-------------------------
Asus RS100-X5/P12 1U server

Intel C2D E7500 - 2.93 GHz
4GB DDR2-800 MHz
2xWestern Digital 1TB HDD (RAID 1)

I've only thought about using ESXi, Hyper-V or an installation of Ubuntu Server with VMware Server 2 installed.

ESXi is already out of the picture because of hardware limitations.  My onboard Marvell Yukon NICs are not supported.

This now leaves me with Windows 2008 Enterprise with the Hyper-V roles installed or Ubuntu Server 8.04 with VMware Server 2 installed.

Many of you may automatically disagree with the Hyper-V solution because Hyper-V is not as developed or because it is Microsoft, but really I am only looking for the most efficient solution.

My only experience with virtualization is running VMs under VMware Server installed on Ubuntu and VMs under VMware Workstation installed on XP, so I'm looking to expand my knowledge with some dedicated hypervisors.

Any comments on Hyper-V vs Ubuntu Server running VMware Server 2?

---

### Post by rjking on 2009-09-29
I'll kick this off, by asserting that if you chose VMware, consider *not* using Ubuntu as the host, and instead running a supported os, such as CentOS (I'm impressed with myself that I beat Bodhi to this one...! Have to tip my hat to the real guru here...) :)

I will follow this by stating that I personally have been very happy with VMware server (even as the tide seems to be rising against it on this forum), and I also prefer Ubuntu as my primary server platform. However, when it comes to hosting VMware, I would suggest using a supported os (save yourself some headaches), then knock yourself out with Ubuntu guests!

Cheers!

---

### Post by brian mcgee on 2009-09-29
Using Xen + Debian Lenny on 4 servers at work. It's been nothing but phenomenally efficient. Extremely powerful too. Here's something to get you started: [http://www.howtoforge.com/virtualization-with-xen-on-debian-lenny-amd64](http://www.howtoforge.com/virtualization-with-xen-on-debian-lenny-amd64)

However, to get deeper into the principles and advanced configuration of Xen, I recommend a book called "Running Xen: A Hands-on Guide to the Art of Virtualization". It's a great intro and reference.

If you want simpler virtualization, have a look at KVM. I have used it on my Debian workstation for ~6 months with no problems. Another link:
[http://www.howtoforge.com/virtualization-with-kvm-on-a-debian-lenny-server](http://www.howtoforge.com/virtualization-with-kvm-on-a-debian-lenny-server)

As far as guests are concerned, LVM-based are more efficient than image-based.

---

### Post by __p1n__ on 2009-09-30
> **brian mcgee said:**
> Using Xen + Debian Lenny on 4 servers at work. It's been nothing but phenomenally efficient. Extremely powerful too. Here's something to get you started: [http://www.howtoforge.com/virtualization-with-xen-on-debian-lenny-amd64](http://www.howtoforge.com/virtualization-with-xen-on-debian-lenny-amd64)

However, to get deeper into the principles and advanced configuration of Xen, I recommend a book called "Running Xen: A Hands-on Guide to the Art of Virtualization". It's a great intro and reference.

If you want simpler virtualization, have a look at KVM. I have used it on my Debian workstation for ~6 months with no problems. Another link:
[http://www.howtoforge.com/virtualization-with-kvm-on-a-debian-lenny-server](http://www.howtoforge.com/virtualization-with-kvm-on-a-debian-lenny-server)

As far as guests are concerned, LVM-based are more efficient than image-based.

My vote is for Xen as well.  My main workstation is built with xen 3.4.1 and netbsd 5.0.1.  The guest os images are similarly logical volume based and not raw partitions and run in HVM's.

---

### Post by openfly on 2009-09-30
If you aren't going ESX the only other real option is Xen.

---

### Post by dpj23 on 2009-09-30
How many virtual machines are you planning on running on this piece of equipment is how I would start to answer your question.  I would follow up with the reason I ask is for this reason.

If you are only going to run a few machines then I would suggest using VM workstation 6.5 it has which enables a list of things you can do that VM server won't allow you to do.  Now this works well if your only going to run 2 or 3 machines that you would manage manually.  

If you want the web based console so you can manage them remotely from a web browser then VM server.  But that is the best it will do these days compared to other products.  The install of vmserver 2.0 can be a little tricking so I would read up on it as well.  I know that not all the packages are installed by this program so it might be good for you to know the dependencies as well....

Ideally you would wait for 10.4LTS and then start the project, install vm workstation 6.5 (next version will be compatible with ESX4) and run a great host operating system followed by VMware which would provide the virtualization software.

---

### Post by brian mcgee on 2009-10-01
Also, I'd add that Xen is regarded as the most efficient of the best hypervisors... also, it's super-easy to script (e.g. if you want a VM to boot at the end of the month, you just add an entry to your crontab). I've heard bad things about MS Hyper-V, but I've never used it.

---

### Post by PilotJLR on 2009-10-01
VMware Server 2 is a bad choice. Hyper-V is better, but that doesn't mean it's the BEST choice. Consider these:
1. VMware ESXi
2. Citrix XenServer
3. And then Hyper-V...

---

### Post by smc18 on 2009-10-03
Thanks for all the replies so far. :)

My hardware is not compatible with ESXi; so I will be learning how to use Xen.

Here's a stupid question, what is the difference between Xen and XenServer?

From what I've read Xen seems to be an indepent Open Source project and XenServer is funded by Citrix, but what else?

---

### Post by freakalad on 2009-10-04
I'm understanding Xen to be a generic reference to Citrox's solutions. Xen & XenServer being the proprietary enterprise hypervisor, whereas XenSource is the proper Open Source solution.

I've tried using Xen before, but didn't really like it much (for various reasons).

I'm currently using KVM (along with libvirt), & I like it a LOT. 
The only drawback is that I'm not able to get extremely hi-graphics (3D) on it, but that's something I'm working on. 
KVM is also not the accepted hypervisor for both RedHat (RHEL) & Ubuntu, so expect great things from that space.

If the desktop-experience is something that's extremely important to you, then look at Sun's VirtualBox (preferred platform for games & windows-users that have migrated to Ubutnu), but then you loose out on other bit, like live-migrations & libvirt

---

### Post by brian mcgee on 2009-10-04
Sorry, to clarify, when I recommended Xen, I did *not* mean Citrix's XenServer. I meant XenSource ([http://www.xen.org](http://www.xen.org)). AFAIK, Citrix just includes proprietary tools on top of XenSource and calls it XenServer. There are FOSS tools available for XenSource that have never let me down. Anyway, we've had a lot of success with Xen in production. 

KVM is great too, but not as mature. That said, I have not run into any trouble with KVM, and I understand it's being very actively developed.

---

### Post by freakalad on 2009-10-04
True on all points.

Xen is very mature, but it's a custom kernel, which causes all sorts of other issues. But that's fine in production environments.
KVM, on the other hand, is "little more" than a kernel module, which makes it a snap to implement

In both cases, they can be administered with libvirt, so it opens up to all sorts of goodies, like Eucaliptus, OpenNebula, SolidICE, virt-manager, Enomaly, EC2 & etc.

Xen(Source) is pretty hard-core & not very forgiving; and I expect much of the growth & development will now shift away from Xen to KVM (since it now the official hypervisor for both RHEL & Ubuntu)

---

### Post by brian mcgee on 2009-10-04
> **freakalad said:**
> Xen(Source) is pretty hard-core & not very forgiving; and I expect much of the growth & development will now shift away from Xen to KVM (since it now the official hypervisor for both RHEL & Ubuntu)

Agreed. KVM is certainly easier, and I suspect it might be the best option in this case. smc18, it might help to know a bit more about what your specific goals are, but since you said it's a home env, I'm leaning towards KVM. Also, consider that Xen will probably take more time to get going.

---

### Post by __p1n__ on 2009-10-04
> **freakalad said:**
> I'm understanding Xen to be a generic reference to Citrox's solutions. Xen & XenServer being the proprietary enterprise hypervisor, whereas XenSource is the proper Open Source solution.

I've tried using Xen before, but didn't really like it much (for various reasons).

I'm currently using KVM (along with libvirt), & I like it a LOT. 
The only drawback is that I'm not able to get extremely hi-graphics (3D) on it, but that's something I'm working on. 
KVM is also not the accepted hypervisor for both RedHat (RHEL) & Ubuntu, so expect great things from that space.

If the desktop-experience is something that's extremely important to you, then look at Sun's VirtualBox (preferred platform for games & windows-users that have migrated to Ubutnu), but then you loose out on other bit, like live-migrations & libvirt

Xen 3.4 supports a variety of ways to do VTd-based pci passthrough to HVM guest os'es.  There are some restrictions with respect to cpu though.

[http://wiki.xensource.com/xenwiki/VTdHowTo](http://wiki.xensource.com/xenwiki/VTdHowTo)

---

### Post by freakalad on 2009-10-04
Device pass-through is one of the more serious drawbacks for me on KVM.

In VMWare, VirtualBox (& even Xen/Source, if I'm not mistaken), you can dynamically add & remove USB & PCI devices, but in KVM it has to be explicitly set between reboots (have I got this right?)

What's especially an issue at the moment is the video. 
I'm trying to VM/abstract my desktops & media centers in a VM, & then make use of something like NX (FreeNX, QtNX, NeatX; FOSS RPD/super-compressed remote-X) to pull the UI out.

I'll keep working at this, bit by bit, until I've got a satisfactory solution

---

### Post by smc18 on 2009-10-06
Sounds good :) :)

It's ashame I've already setup Citrix's XenServer on the machine and setup a few VMs already.

Sometime in the future, I would like to try out KVM and also XenSource.

---

### Post by freakalad on 2009-10-06
I'm having NO luck with OpenGL in a VM.

Are you able to get something going in Xen?

---

### Post by smc18 on 2009-10-07
> **freakalad said:**
> I'm having NO luck with OpenGL in a VM.

Are you able to get something going in Xen?

So far, I've only setup two Windows 2008 Servers for Terminal Services and Active Directory.

The VMs seems to be doing their job;  I set them up for learning purposes so at the moment they aren't really doing anything to demanding.

---

