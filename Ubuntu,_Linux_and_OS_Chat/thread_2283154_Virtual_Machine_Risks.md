---
title: "Virtual Machine Risks"
date: 2015-06-19
forum: Ubuntu, Linux and OS Chat
---

### Post by Kurt_Alan on 2015-06-19
I dual-boot LTS (14.04 Ubuntu and Xubuntu) for a reason--stability, same as everybody else.

But I still want to play!

I haven't used a virtual machine program for ten years.

I have now installed vmware player and I'm ready to grab my first Manjaro .iso.

What kind of a risk will I be taking to my stable setup? I particularly worry about the fragility of GRUB.

---

### Post by QIII on 2015-06-19
A VM in VMWare or Vbox should not affect GRUB.  It only runs in the context of the virtualization software installed on the host.  It's not discoverable by GRUB.

---

### Post by wildmanne39 on 2015-06-19
The OS you run in a vm it is like putting it in a box made of steal it can not touch the host system, I personally like using vm's for testing for that exact reason I can break the guest OS as much as I want and my production machine that the vm is running on is never affected.

---

### Post by ajgreeny on 2015-06-19
One of the beauties of VMs is that they don't have any effect on the host OS, unless, of course, you deleted any files or folders that are in a shared folder in your host.  This assumes that vmware has a system of shared folders in the same way that VBox does.

I run 8 separate VMs in my Xubuntu 14.04 host (not all at the same time, of course) and they are all as safe as a house.  I have snapshots of all of them so that if something goes wrong I simply revert to the last working snapshot, and I'm back where I was before.

---

### Post by Bucky Ball on 2015-06-19
In other words, jump right in! :)

* Just a note. Not sure VMware is available in the official repositories. Virtualbox is and you know that is officially supported and updated. You don't need to deal with a manual install, you just install from Software Centre or Synaptic. VMware may have advantages over Virtualbox or vice versa, I don't know, only ever used VBox. Good luck and have fun. ;)

---

### Post by Kurt_Alan on 2015-06-19
> **Wild Man said:**
> The OS you run in a vm it is like putting it in a box made of steal it can not touch the host system, I personally like using vm's for testing for that exact reason I can break the guest OS as much as I want and my production machine that the vm is running on is never affected.

I know that vm's are supposed to be like a sandbox. Just afraid that a crash of the vm guest might cause a crash of the host, so I guess I just have to have FAITH.

It seems that you are saying that if there is a vm crash, that it self-implodes (along with the guest OS) but that's the end of it.

Everything's running so clean now; just afraid to jump off that board for the first time!

---

### Post by Bucky Ball on 2015-06-19
Have you got another partition? I have about four for OSs and other stuff. I have a couple of 12.04 LTS installs and my main squeeze, a stable 14.04 LTS. One of the 12.04 installs has Virtualbox and I use that for messing about. 

If you're really dubious this might be a way to go. Do a basic install on another partition then install VMware and go for it. If the VM breaks (the VM *is* the guest OS, BTW) and takes the host with it, highly unlikely and in many way not possible, then no drama.

---

### Post by wildmanne39 on 2015-06-19
I have been using virtualbox for about 7 years and I have never had the guest OS crash and make the Host crash too.

When you set up the host and guest you have to make sure to allow enough resources for both operating systems.

---

### Post by Bucky Ball on 2015-06-20
> **Wild Man said:**
> When you set up the host and guest you have to make sure to allow enough resources for both operating systems.

Good point. The host and guest share the RAM and processor so, for instance, if you have 4Gb of RAM installed you would share it between the two. How is up to you. 2Gb each or 1 and 3Gb. Depends what you're doing.

---

### Post by Kurt_Alan on 2015-06-20
> **Bucky Ball said:**
> Have you got another partition? I have about four for OSs and other stuff. I have a couple of 12.04 LTS installs and my main squeeze, a stable 14.04 LTS. One of the 12.04 installs has Virtualbox and I use that for messing about. 

If you're really dubious this might be a way to go. Do a basic install on another partition then install VMware and go for it. If the VM breaks (the VM *is* the guest OS, BTW) and takes the host with it, highly unlikely and in many way not possible, then no drama.

In fact, I have two partitions, i.e., I dual-boot partly as my long_ss workaround to dropbox.com's recent failure to support Xubuntu. So in Ubuntu, my Dropbox works perfectly; in Xubuntu, it works passively--no menu access. Depending on my Dropbox needs, I will boot to the one partition or the other.

But this has taught me that there is this inherent advantage of dual-booting Linux: you always have a backup OS on the same machine. So, if my VM guest OS crashed my host OS, I could just boot to my second partition to troubleshoot.  Long live dual-boot!

P.S. I had no problems running Manjaro as a VM. vmware player documentation does not support this distro, but there is an option for kernel 3.xx.  Ah, now I can try my first Ubuntu alpha and Win 3.x and . . .

---

### Post by Bucky Ball on 2015-06-20
Yep. Go crazy with virtual machines in the Xubuntu install and keep the other one as your rock. Have fun. I certainly did when I first tried Virtualbox and spent about a week checking all the distros I'd been curious about. :)

One thing it is very useful for is trying out different apps and desktop environments. Once you're happy (and that took me about five years) do a mini install, which is just the kernel, add your favourite desktop environment and only the apps you want/need/use, from basically anywhere. As long as the app will run on the Ubuntu kernel (which means anything in any of the Ubuntu flavours and the majority of things in the spins/distros based on it) you're looking good.

This can lead to a very streamlined workhorse or a bulky bells and whistles hybrid. Whatever suits.

---

### Post by SeijiSensei on 2015-06-20
> **Kurt_Alan said:**
> But this has taught me that there is this inherent advantage of dual-booting Linux: you always have a backup OS on the same machine. So, if my VM guest OS crashed my host OS, I could just boot to my second partition to troubleshoot.  Long live dual-boot!
VM managers like VirtualBox and VMware let you take "snapshots" of the guest systems. When you get a VM configured the way you like, take a snapshot and save it elsewhere in the file system.  If something goes wrong, you can import the snapshot and be back with a clean configuration.

VirtualBox is very stable; I've never had a problem in a VM guest affect the VM host.  The guest thinks it's running on separate hardware.  It doesn't see the physical hardware, just the emulated hardware provided by the VM manager.  I don't have any experience with VMware since it's proprietary so I've stuck with VirtualBox. It does have some proprietary bits to handle things like USB which are encumbered by patents that are contained in an "Extension Pack."  Otherwise it's open-source.

---

### Post by pretty_whistle on 2015-06-21
I agree.  Running a vm doesn't affect the host at all.  I have vbox and have never encountered an issue with it.

---

