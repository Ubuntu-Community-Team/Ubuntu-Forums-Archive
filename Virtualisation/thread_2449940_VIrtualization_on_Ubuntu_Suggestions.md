---
title: "VIrtualization on Ubuntu Suggestions"
date: 2020-09-04
forum: Virtualisation
---

### Post by rsteinmetz70112 on 2020-09-04
I have not used Virtualization before. I have always install things directly on the hardware. I wish to try it out and do some testin, preferable when I upgrade my test machine to 20.04 LTS.

I'd appreciate some recommendations on minimum hardware and which software to use. I would like to have virtual Linux and Virtual Windows.  I will almost certainly need to upgrade my RAM and SSD, I may even need to upgrade my processor/motherboard.  The machine I'd probably use has 8GB of RAM and an AMD FX 8350

---

### Post by deadflowr on 2020-09-04
*Thread moved to **Virtualization***

What is the intentions as far as running virtual machines?

Some users run VMs for OS testing.
And some run VMs as an isolation method, to keep various tasks/programs restricted from one another. (more or less)
And I'm sure others use it for other reasons.

If you want to try testing out different OSes, then you might try using Virtualbox.
It's nice and easy to use.
Good for both beginners and old hats.

---

### Post by rsteinmetz70112 on 2020-09-04
For right now its for learning and testing. I have some vague ideas for how I might eventually use it.

---

### Post by SeijiSensei on 2020-09-04
VirtualBox is probably the easiest solution. I recommend installing it by following the instructions here: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions).

On 20.04, replace "<mydist>" with "focal" like this:
```
deb [arch=amd64] https://download.virtualbox.org/virtualbox/debian focal contrib
```

Rather than editing /etc/apt/sources.list, I create a separate file in /etc/apt/sources.list.d/ called "virtualbox.list".  It contains just the line above. You'll need to do this with sudo.

---

### Post by TheFu on 2020-09-04
4gb of RAM is enough and any dual core CPU with vt-x capabilities will be fine for almost any needs, just don't expect heavy graphics to work well, but all non-GUI stuff runs fine.  Properly tuned, about 95% of native performance is pretty common. Just be certain to share the available hardware nicely between all the running processes in all running VMs.

The choice of hypervisor is a personal thing. Most people would start with virtualbox in the beginning, then switch to more powerful, more stable, solutions later.  For desktop-on-desktop VMs, virtualbox isn't a bad choice. If you want servers -  no GUI and plan to access the VMs by ssh 99.99999%, then kvm is stable and fast.  KVM is what morst cloud providers use.

I'd suggest starting with vbox. Carefully read the license for the "guest additions" - there are some unexpected things inside it.

---

### Post by SeijiSensei on 2020-09-04
Yes, I forgot to mention to install the Extension Pack. It includes things that cannot be distributed under an open-source license. One surprising item is USB support. The USB technology is [encumbered]("https://www.usb.org/").

---

### Post by lammert-nijhof on 2020-09-07
For years I just load the deb file and the extension pack and install both by double clicking it. I don't worry about automatic updates. Once in a month I check for a new point release, read the changes and afterwards I decide, whether the update is useful. Sometimes on a new install of Ubuntu you might have to install gcc, make and another deb file first. But using e.g. gdebi for the installation Linux will tell you what other deb files it needs. 

I strongly recommend Virtualbox for desktops, because advantages of Virtualbox are:
 
[LIST]
[*]it is significantly more user-friendly than any other option; 
[*]It always has been reliable, all options work and that is not true for  QEMU/KVM; I still run a Windows XP VM, that I installed in Virtualbox in  Jan 2011 on a 32-bits Pentium 4. 
[*]it uses the CPU type of your host, while my Ryzen 3 2200G has been mismanaged by QEMU/KVM as an old Opteron server CPU. 
[*]you can activate Windows In a VM using the activation code glued to the PC. 
[*]I boot my Ubuntu VMs in 7-13 seconds from a nvme SSD. 
[*]The 3D Graphical user interface is good, but you loose significant  performance compared to real hardware. However I can play Super Tux Kart  and Extreme Tux Racer in a VM at 1080p and 60Hz. Modern commercial  games will not play in this way. BUT I play Wolfenstein in a VM (in DOSBOX in Ubuntu VM on an Ubuntu VBox Host) [IMG]https://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG] [IMG]https://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG] 
[/LIST]
 I think for servers, you should use KVM, but I have no experience in that area.

---

### Post by TheFu on 2020-09-07
The **apt** program (not apt-get) can traverse dependencies and install those required by .deb files too, but that doesn't remove the risks inherent with using .deb files directly.

The only thing I miss from apt-get that apt doesn't provide is package-name globbing.  With apt-get, we can remove lots of packages using wildcards. Apt doesn't support that ... yet.

KVM + virt-manager has similar vGPU performance now to what virtualbox had thanks to the "SPICE" protocol and QXL guest drivers.  I know people who use KVM for autoCAD work.  And if you have 2 GPUs, KVM on the right hardware supports GPU passthru to a guest with exclusive access to one of the GPUs.  

KVM supports many more storage backends, but home users aren't likely to use most of those. For enterprise or professional setups, that's a powerful aspect in virtualization and management.

KVM supports any sort of networking the Linux host can provide.  This is different from Virtualbox and requires understanding how to setup the networking in a way you'd want.  It is separate from the hypervisor, though libvirt does setup a NAT network by default. I never use it and have always setup a bridge network for my VMs, unless it was just a quick play VM.  Networking between VMs and the host on the same physical machine are about 24 Gbps.
```
[  5]   0.00-10.00  sec  28.1 GBytes  24.1 Gbits/sec                  receiver
```
A few days ago, I thought I'd gotten 36 Gbps. Oh well.  Really fast networking is close enough.

For beginners, vbox is not a bad tool, except the licensing, if you care about that stuff.

---

### Post by SeijiSensei on 2020-09-07
> **TheFu said:**
> For beginners, vbox is not a bad tool, except the licensing, if you care about that stuff.
> The VirtualBox base package contains the full VirtualBox source code and platform binaries and is licensed under the GNU General Public License, version 2. You can distribute and modify the base package, provided that you distribute all modifications under the GPLv2 as well.

The VirtualBox Extension Pack is available under the VirtualBox Extension Pack Personal Use and Evaluation License, which is a free license for personal, educational or evaluation use, or an Enterprise License, which is a for-fee license that allows most commercial, non-distribution uses restricted by the PUEL. 

[https://www.virtualbox.org/wiki/Licensing_FAQ](https://www.virtualbox.org/wiki/Licensing_FAQ)

The Extension pack contains some things that are encumbered by patents as I [mentioned above]("https://ubuntuforums.org/showthread.php?t=2449940&p=13984280&viewfull=1#post13984280"). I'm don't see how Oracle can be any more open than to put the main code under the GPLv2 and the Extension Pack under a separate license for non-commercial use.

---

