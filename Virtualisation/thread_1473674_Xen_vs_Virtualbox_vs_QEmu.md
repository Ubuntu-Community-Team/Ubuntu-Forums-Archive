---
title: "Xen vs Virtualbox vs QEmu"
date: 2010-05-05
forum: Virtualisation
---

### Post by slooksterpsv on 2010-05-05
All,

I love virtualization, it's something that I just love to work with, love to do, love to try out. Anyways, I have a couple of questions (for those that know):

1. Is Xen faster than VBox or QEmu
2. OpenSuSE lets you install Xen, if Xen is better in some respects would you recommend SuSE for Virtualization or another distro?
3. Any additional remarks regarding Xen?

Hmmm it's early, can't think so not sure if I saying what I wanna say - I love Ubuntu, don't get me wrong, but I love Virtualization even more hehe =P.

---

### Post by slooksterpsv on 2010-05-06
Ok, Xen is not what it used to be, installing it was a pain, had to wait 1 1/2 for 331MB of updates to install (sorry but SP2 for vista installs faster and that's a 500MB download), SuSE updates are just ridiculous, I can work with VirtualBox, if I need a more powerful solution, VMware is free.

Don't mess with Xen unless you have time to figure out every little piece that isn't working. Novells OpenSuSE has went downhill

---

### Post by robvas on 2010-05-06
I followed the Debian Xen Wiki ([http://wiki.debian.org/Xen](http://wiki.debian.org/Xen)) and it worked fine. 

Citrix also offers the free Xen Server ([http://www.citrix.com/lang/English/lp/lp_1688615.asp?ntref=hp_promo_2a](http://www.citrix.com/lang/English/lp/lp_1688615.asp?ntref=hp_promo_2a)) which is point and click, a piece of cake to use.

---

### Post by TheFu on 2010-05-06
Xen is not included in the base kernel, so it will always lag as newer kernel team approved virtualization methods are promoted.

I've been using Xen for almost 2 years on work production systems, but I've avoided any customization and only used the Ubuntu Xen packages. Those are still running TODAY on 8.04 LTS with 8 VMs active. 

With 10.04, those packages aren't available (so I hear) and KVM is being pushed by both [FONT=Arial, Helvetica, sans-serif][SIZE=2]  Canonical[/SIZE][/FONT] and Redhat for future virtualization needs. KVM is very interesting and I've looked at migrating our production servers to it.  I've been using KVM (9.10) in the lab and honestly, I haven't been impressed. The GUI tools are toys and the instructions are not impressive, at least for my needs. I'm not happy with many of the defaults, especially where the VMs get placed. I know I can move them, but honestly, who wants a VM under /var?

For someone new to Linux, I'd recommend they go with VirtualBox to start. When you find the stability lacking or you're more comfortable with a shell (no GUI), then some other hypervisor could be better. I've never used Vbox with a Linux host, only Vista and Win7, so I really can't comment with any authority about it the way most people here run it. I'm worried what Oracle will do with it.

I've used VMware Player, Server, ESX and ESXi. For desktops, I think "Server" is the best free answer from VMware for desktop users, but many other people will recommend the paid "Workstation" product.  ESX is too expensive to be considered for home use. ESXi is limited but rock solid. I've had both a Windows7 desktop and Ubuntu, SuSE, OpenSolaris and a few other VMs running on an ESXi box for 8+ months with ZERO problems besides that all the tools are MS-Windows specific and usually they withhold some critical feature to get your $800 for the paid version. VMware appears to be "going windows" even more since they're leaving Perl and doing some windows specific scripting now.

To answer your questions:
1 - is Xen faster?  Xen supports paravirtualization, so if the drawbacks involved with that method are ok with you, then yes, it will probably be faster. It may not be quicker to implement, but that is completely depend on you background, knowledge and skill. If you don't understand those limitations, you really need to do some reading.

2 - I haven't used SuSE in a few years and never used any virtualization with it. "I don't know" is the only truthful answer.

3 - I've had issues with Xen over the years, but overall I've been happy. That happiness could just be that I'm comfortable with it and know the tricks to make it run well. One of the key limitations is that when you need a kernel update, then if you are using paravirtualization (as I am) then all the kernels need to be updated, including the host. For us, Xen is solid. Having a full Linux host provides some very nice bonuses that ESXi cannot. Our backups are simply amazing, quick, incremental and free.  Amazon uses Xen for their Cloud Server offerings, so it can definitely scale.  I've never used the HVM (hardware virtual machine) under Xen, but that is an option for some.

---

### Post by tgalati4 on 2010-05-06
Citrix purchased Xen (I'm still trying to figure out how you purchase an open source project.)  According to the Xen presentation at SCALE, Citrix plans to keep it open source and they have a roadmap for development.  So Xen is not dead yet.  Ubuntu's decision to go with KVM has been debated and it makes sense for Desktop use cases (I need Windows to run XYZ . . .).

[https://www.socallinuxexpo.org/scale8x/presentations/open-source-virtualization-xen-way](https://www.socallinuxexpo.org/scale8x/presentations/open-source-virtualization-xen-way)

---

### Post by slooksterpsv on 2010-05-07
I've used VirtualBox, VPC, VMWare, Hyper-V, Parallels, QEmu, KVM, etc. VirtualBox is great, but has some drawbacks. Hyper-V is great if you have $$$ to spend on it - lets see I think standard is $700. VMWare is awesome, fastest I've used, but its only Windows. KVM is nice, but way way too slow - took 5 hours to install Vista (VBox only takes about 45 min.) - QEMU is like KVM. Parallels, costs $$$, but is great otherwise. VPC is Microsofts and it's slow.

I wanted to use Xen for the Paravirtualization features, granted it has some major drawbacks, but for the purposes that I wanted to use it for, it would have been perfect.

Looks like I'll stick with VirtualBox as it's quick, reliable, etc. even the features are great.

---

### Post by tgalati4 on 2010-05-07
Find a curbside box and follow the tutorials and build your own Xen box.  Then post your experiences.  That will quickly get you up to speed.

---

### Post by agent8131 on 2010-05-11
1. Is Xen faster than VBox or QEmu

Absolutely.  I just gave KVM another try and it was painfully slow compared with Xen.  Load averages on the virtual servers were 2x as high.

2. OpenSuSE lets you install Xen, if Xen is better in some respects would you recommend SuSE for Virtualization or another distro?

If you're used to Ubuntu and want to use Xen than Debian might be the best way to go.

3. Any additional remarks regarding Xen?

It's far and away the best virtualization solution for servers, in terms of performance and stability.  However, it is more difficult to use than KVM/QEMU and VirtualBox.  So if you're looking for a desktop solution Xen is unlikely to be your best bet.  Also, Xen prior to 3.4 (I believe) did not have power management so that's something to keep in mind.

---

### Post by tgalati4 on 2010-05-12
xen 3.3 is built for jaunty.  So if you want a less painful way to play with xen, install jaunty server then install xen 3.3 from the repos.

xen 3.2 is built for hardy as I just checked the repos on one of my hardy servers.

Xen is also more efficient than other VM's because of it's multiple init processes that share the same kernel resources.  This reduces the duplication of these resources for each VM instance.

---

### Post by TheFu on 2010-05-13
With both Redhat and Ubuntu dropping Xen from their offered kernels for KVM, I'm curious whether that figures into your decision?

I've been running Xen from Ubuntu Server repos for almost 2 years. I like it, but with 10.04 dropping Xen kernels, I feel that I need to migrate. Am I wrong?

---

### Post by LiLoather on 2010-09-20
Seems a pity to let this thread hang, as it's a subject of on-going interest to many.

I'm looking to virtualise a Linux guest on Ubuntu 10.4 LTS server as host but can't use KVM as my hardware isn't 'virtualised' - although it might sound antiquated at all of six years old it's is still perfectly good and grunty enough for the job which makes it pointless spending money on replacing it.  Which makes me slightly annoyed that the Ubuntu developers would plump for kvm when Linux is great for squeezing a few more years use out of perfectly good equipment - save the planet and all that.

I've tried VMWare and VirtualBox, and found the latter much easier to set up and run.  Xen never seemed to bother about 'casual' users, and if you go to the Citrix site to have a look at the free XenServer you'll find you need a Masters in Computing just to comprehend half of the home page!

So it's VirtualBox for me as it may not be the flashiest or the fastest, but it's the friendliest.

---

### Post by TNT1 on 2010-09-20
This is like a "which is better, linux, or windows, or macOS?" thread.

---

### Post by LiLoather on 2010-09-20
> **TNT1 said:**
> This is like a "which is better, linux, or windows, or macOS?" thread.

Sure, and in discussing the pros and cons of any alternatives the open-minded can learn and refine their opinions and the tyro can just learn.

And hopefully more people are open-mined about their choice of virtual machines than they are about their choice of OS.

---

### Post by manzdagratiano on 2010-09-20
I have used Virtualbox extensibly in the past, but I have now moved on to qemu-kvm; I like it because it provides me hardware virtualization (it is enabled in the CPU, which was, this time, one of the primary factors in my buying the laptop I did), and therefore I know for sure how the virtual machine would actually behave on my system, if installed, which is why I like it. Virtualbox was very good for basic virtualization, but the guest additions package gave me very many issues - it would stop working if something went wrong and not function until I rebooted the VM, not to mention that I wanted to see what a hardware virtualized machine would be like.

In all honesty, I found the VMs to be faster under qemu-kvm as compared to Virtualbox. including network performance, which was certainly slower in Virtualbox for me - I realize that qemu-kvm is much faster than qemu with no kvm support. Trouble only brews when I switch to high graphics mode, when the video behaves sluggishly, even though all other functions are still fast. I am looking into how to increase the gpu memory in kvm - I have yet to find the answer. I like qemu-kvm much much more than Virtualbox, because I can just operate everything from the command line, not to mention the extreme customizability I now have; I do not think I shall ever be going back to Virtualbox again.

Xen, now, is an entirely different animal. I would soon try to fiddle with it in one of my VMs which run Debian, but I have so far not used it since Ubuntu does not support it anymore - and mixing sources, in this case to pull a dom0-kernel from Debian, has only brought me grief in the past, as things always break later on. I certainly imagine Xen would be faster than qemu-kvm as well.

Ergo, IMHO, Xen (expected) > qemu-kvm > Virtualbox

If one wants to run Xen, installing Debian on the machine is the best way to go. This would certainly be an optimum choice for servers, but for desktops/laptops, Ubuntu supports the hardware most smoothly of all, which I, being a die-hard Debian addict in the past (and still one, but not Debian-only anymore), can testify. I am not aware how well supported Xen is under Arch Linux, since I just started fiddling with it.

---

### Post by slooksterpsv on 2010-09-21
I'll try qemu-kvm here in a bit, probably after Maverick is released, I'm running the beta as my OS now, it's really really stable, surprisingly. Only issue I've had is with npviewer.bin crashing all the time, but doesn't bug me. So yeah I'll try qemu-kvm, I think I was harsh earlier and wanted Xen to install quickly. I like Debian, it's amazing, so I'll have to try Xen in Debian.

---

### Post by LiLoather on 2010-09-21
> **manzdagratiano said:**
> I found the VMs to be faster under qemu-kvm as compared to Virtualbox. including network performance, 

I find this worrying, as the VM I wish to run on Ubuntu Server is a network router which will be handling a lot of networking across five NICs.

---

### Post by rupert160 on 2010-09-21
I was informed some time ago that Xen was not running their development inline with the main line kernel which I thought was a bit dumb. Not sure if they'll merge back to the mainline. Anyway I gave it a miss for that reason.

I recently wanted to venture into kernal assisted virtualisation using ubuntu. It was a nightmare. 
*Upgraded my cpu. done. 
*Installed windows because I had no other way to flush the bios to the most last beta (yes I tried FREEDOS but the Gigabyte Motherboard install tool required a GUI environment)
*Rebuilt the kernel to include Tap/Tun for networking which wasn't included in the generic ubuntu build (ffs Canonical - you say you support kvm and you don't include the main networking modules required for it to work?)
*Installed the user space hook-in Qemu and the GUI aQemu (it seems to be missing a number of features)
AND:Screen resolution sucked and I still couldn't get bridged networking to work. 

I have big expectations for Ubuntu 10.10! But KVM needs to mature a bit more before I use it again or at least systems designed to use it need to - It's just too frustrating to setup. But it is reputed to have blistering speed and amost 99% of native speed when you install linux on linux. It can't be beaten there.

Now I'm back to my favourite VirtualBox. excellent screen resolution, even natively supports self adjustment to scaling of the window and networking was like a native computer. Couldn't have been easier. Make sure however you install the closed source edition to get all the features including USB.

---

### Post by TheFu on 2010-09-21
Just to clarify, VMware has 5+ different virtualization tools (hypervisors) and they are definitely NOT all for Windows and not all have a cost. They have a mix of VM tools that work for desktops and others for servers and others for pseudo-servers.  If you want performance and can live without a local GUI, check out VMware ESXi. You'll need a Windows machine to control the hypervisor running on another machine. That's a major drawback for me.

---

### Post by manzdagratiano on 2010-09-21
> **rupert160 said:**
> I was informed some time ago that Xen was not running their development inline with the main line kernel which I thought was a bit dumb. Not sure if they'll merge back to the mainline. Anyway I gave it a miss for that reason.

I recently wanted to venture into kernal assisted virtualisation using ubuntu. It was a nightmare. 
*Upgraded my cpu. done. 
*Installed windows because I had no other way to flush the bios to the most last beta (yes I tried FREEDOS but the Gigabyte Motherboard install tool required a GUI environment)
*Rebuilt the kernel to include Tap/Tun for networking which wasn't included in the generic ubuntu build (ffs Canonical - you say you support kvm and you don't include the main networking modules required for it to work?)
*Installed the user space hook-in Qemu and the GUI aQemu (it seems to be missing a number of features)
AND:Screen resolution sucked and I still couldn't get bridged networking to work. 

I have big expectations for Ubuntu 10.10! But KVM needs to mature a bit more before I use it again or at least systems designed to use it need to - It's just too frustrating to setup. But it is reputed to have blistering speed and amost 99% of native speed when you install linux on linux. It can't be beaten there.

Now I'm back to my favourite VirtualBox. excellent screen resolution, even natively supports self adjustment to scaling of the window and networking was like a native computer. Couldn't have been easier. Make sure however you install the closed source edition to get all the features including USB.

Well... I thought it was a nightmare to setup until I found help on the forum here in this post:

[http://ubuntuforums.org/showpost.php?p=9217393&postcount=4](http://ubuntuforums.org/showpost.php?p=9217393&postcount=4)

(with a minor correction In am rectifying below) and trust me, nothing is easier! All you really need to do is:

```
egrep --color=auto '(vmx|svm)' /proc/cpuinfo
```to check is virtualization is enabled in the CPU - if it is, you shall see `vmx' or `svm' listed in the output, and if nothing, you are out of luck. Qemu will still run but without kvm support.

Install kvm:
```

sudo apt-get install kvm qemu bridge-utils uml-utilities
sudo modprobe kvm
```Add the user to the kvm group:

```
sudo usermod -G kvm -a <user>
```Make a virtual hard drive:

```
qemu-img create -f qcow2 <harddrive>.qcow2 100G
```The size of the created file would only be some 264KB or something - it is going to be a dynamically expanding storage.

Run kvm:
```

kvm -m 512 -cdrom <disk>.iso -boot d -hda <harddrive>.qcow2 &
```You may also use 'qemu' instead of 'kvm' - kvm has been merged into qemu and the default is to run qemu with kvm support.

Once the OS has been installed, run using harddrive only:

```
kvm -m 512 -hda harddrive>.qcow &
```Add the switch '-soundhw all' for sound, and '-vga std/cirrrus/vmware' for video. vmware video drivers are the best so far, at least for my Debian VM. They did not work for me on either my Arch or my Gentoo VM.

And that's it! You do not need to create a bridged network card - your network card will show up as an ethernet connection on the VM.

---

### Post by agent8131 on 2010-11-27
I just wanted to update on my experience with KVM vs Xen on the server.  Under Ubuntu 10.04 I found that loads for KVM vs Xen are no longer 2x as high.  Now they are only 20-25% higher.  Still a big hit but also showing improvement.

---

