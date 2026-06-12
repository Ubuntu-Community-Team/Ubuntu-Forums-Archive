---
title: "how to convert local machine to virtual machine (for error analysis)"
date: 2021-07-14
forum: Virtualisation
---

### Post by ATSC on 2021-07-14
Hey,


I have problems with my system related to one or more problematic packages of the graphic performance (Nouveau, X, drm). I believe this began after updates of these packages and I'm trying to find the culprit by replicating the situation. Rather than experimenting with snapshots, I was thinking about creating a virtual machine from my local machine (**not** the hdd) and monitor package updates from there. I've read that VMware has a tool for that purpose. I've never used VMware before but I've extensively used Virtualbox. My root and home-partition have the ext4-filesystem and the home-partition is too large to be duplicated.

1.: Can I safely use my local home-partition as a partition in the virtual machine (instead of using a duplicate)? Or can I simply ignore the partition as it's not subject to the experiments anyway?
2.: What is -generally speaking- the best approach for doing this? Make copies of all (?) partitions, convert them to images and then to vdi's?
3.: Is there anything specific to this purpose (making the copies, creating the vm) that one has to keep in mind?


cheers

---

### Post by scorp123 on 2021-07-14
> **ATSC said:**
>  I have problems with my system related to one or more problematic packages of the graphic performance (Nouveau, X, drm). I believe this began after updates of these packages and I'm trying to find the culprit by replicating the situation.

If the problem is related to specific hardware (e.g. Nouveau = Nvidia graphics) then making a VM clone of a real installation will not give useful results.

> **ATSC said:**
>   Rather than experimenting with snapshots, 

That's why I use ZFS for that exact reason.

> **ATSC said:**
>  I was thinking about creating a virtual machine from my local machine (**not** the hdd) and monitor package updates from there.

Not sure how this would help?

> **ATSC said:**
>   I've read that VMware has a tool for that purpose. 

**For Windows only**, yes.

> **ATSC said:**
>  My root and home-partition have the ext4-filesystem and the home-partition is too large to be duplicated.

Why would you even need to duplicate the partitions and their sizes?? Just reproducing the relevant content (e.g. all the ~/.config and ~/.local files inside your $HOME, all the system-wide settings inside /etc ...) is all you need.

> **ATSC said:**
>  1.: Can I safely use my local home-partition as a partition in the virtual machine 

Probably not and this is a bad idea anyway.

> **ATSC said:**
>  Or can I simply ignore the partition as it's not subject to the experiments anyway?

Depends? If personal settings that originate from inside your $HOME are causing issues then you might need the settings that are stored there. So you'd to replicate those.

> **ATSC said:**
>  What is -generally speaking- the best approach for this approach? 

I doubt doing it this way will yield useful results. You mentioned Nouveau... this indicates that your problem is tied to Nvidia hardware? So that's already a problem there because there's no way you will get Nvidia hardware inside a VM. If I was in your place I'd either get myself an identical PC with identical hardware and use that for experimenting or work with ZFS snapshots and then go back to a working system snapshot if something breaks. I've had to do both approaches many times in the past, e.g. at work to troubleshoot customer issues. 

> **ATSC said:**
>  Make copies of all (?) partitions, convert them to images and then to vdi's? 

Waste of space and time. You don't need the partitions, their sizes, etc.  All you need is their contents, e.g. the files. So a few tar.gz files that contain everything is more than enough. You transfer the tar.gz files into your VM and unpack them there again... and if done right, your VM and your original system should now have the same configuration files. This takes 30 minutes at most.

> **ATSC said:**
>  Is there anything specific to this purpose (making the copies, creating the vm) that one has to keep in mind? 

A real PC and a VM usually have very very different hardware. So depending on what's causing the problem (a hardware driver?) simulating this inside a VM will not yield useful results because there's no way you will be able to simulate the hardware in question or trigger the driver's behaviour. Without the needed hardware inside the VM there's no way you will get the driver loaded or even working.

Simulating a real PC by making a VM copy of it will only be useful if you are 100% sure that all the issues are caused by software. If that is still what you want then all you need is to make sure your VM gets a copy of all the settings (e.g. /etc, the settings inside your $HOME) and all the software your original PC had. 

Good luck.

---

### Post by MAFoElffen on 2021-07-14
> **scorp123 said:**
> If the problem is related to specific hardware (e.g. Nouveau = Nvidia graphics) then making a VM clone of a real installation will not give useful results....

Simulating a real PC by making a VM copy of it will only be useful if you are 100% sure that all the issues are caused by software. If that is still what you want then all you need is to make sure your VM gets a copy of all the settings (e.g. /etc, the settings inside your $HOME) and all the software your original PC had. .
Agreed. Very well said.

One of the big reasons for creating a test environment on a VM, IS that VMs have the ability to be snapshot'ed easily, so that to be able to make changes and roll them back... That part of your idea is sound. 

But as scorp123 said, if your problem that you are trying to trace is a hardware related problem, especially tied to video, then doing that is not going to help you. When you convert a physical machine, or migrate a physical machine, you generalize the hardware dependencies into a virtual environment. (That is also one of the major Business reasons for Physical to Virtual is to make something portable to other systems, that is not tied to hardware.) One of the those major generalizations is "video". 

There are ways that exist to replicate that, but not easily, nor as a general. practical rule. This is why TEAAS (Test Equipment As A Service) exists...

*** There are many here and in other sections of this forum, that do have Nvidia Graphics, including myself. The question remains on what problem you are having, and what are you trying to trace down? As scorp123 implied, there are many options open to you on your existing physical machine, that would give you the ability to back up your system, or to take "snapshots" through a disk management system, such as LVM or ZFS. You could do the same "rolling back changes" if you do that... That is always a good idea and practice.

---

### Post by TheFu on 2021-07-14
I agree with scorp123. About the only things that virtual machines aren't useful to test is when hardware or drivers are the problem. Virtual machines hypervisors provide virtual hardware to the guests, not real hardware.  Further, they provide the most compliant, compatible, and tested hardware so it would be extremely unlikely that any VM would see any issue that real hardware would have.

DRM is hardware.
GPUs are hardware.

I.e. - VMs aren't gonna be useful.  Even for an expert in hypervisors who can passthru the GPU to the guest VM, that setup still will be so different from what happens on real hardware as to be invalid.

Now, if you are having trouble configuring server software, then using a VM to test different configs would make perfect sense.

---

