---
title: "Vmware Workstation Performance Degradation"
date: 2008-06-18
forum: Virtualisation
---

### Post by Akeldama on 2008-06-18
I have a fresh install of Hardy 8.04 that is fully updated as the host OS on a Quad Core2 Q9300 with 3GB of RAM. I'm currently running Vmware Workstation 6.0.4 build-93057 with WinXP as the guest OS.

Right after a fresh boot, WinXP under Vmware runs well with snappy performance. However, after a seemingly random amount of time, performance of the virtual machine degrades. It's most easily noticeable by the way the Vmware control toolbar slides into view from the top of the display (when in full screen mode on the guest). Initially it 'snaps' down quickly. After degradation, it slowly slides down into place. Once performance has degraded, the entire virtual machine is slow. Rebooting the virtual machine has no effect. Shutting down the virtual machine, closing the Vmware application, and then opening Vmware and restarting the virtual machine has no effect. It will start in the degraded state. Even closing all currently running application within the host has no effect on the VM. They only way to free the VM from this degraded state is to reboot the host and start over.

I have tried to determine if an application on the host is causing this degradation, but have not been able to narrow it down. Throughout a normal day, on the host I have VMware Workstation running in addition to Rhythmbox, Evolution Mail and Firefox.

Does anyone have any ideas on what could be causing this degradation or how to fix it? Has anyone else experienced this?

---

### Post by zgornel on 2008-06-20
Have you checked how much of the system resources are allocated to vmware (how much processor /memory it consumes), it might be a memory leak or some sort of bug. Do you have virtualization suport enabled ? I'll check at home, maybe my virtual machine behaves the same ... What resources have you allocated to the gues os ? (including the type of drive - persistent/non-persistent, scsi, etc)

---

### Post by dpj23 on 2008-06-22
More than likely it is a memory leak from the host system...  A person can allocate say 1GB towards the vm and still have plenty for the host...  However, the more and more the programs loop around the more and more memory gets eaten up...

I know this isn't a quick and easy answer for you... but, it might be good to look at what programs are running on the host besides the virtual machine...  I have found that thunderbird at times can create a memory leak... so, when I run my vm's for extended amount of time... I usually make sure not to use that program...  Now, before anyone rips me...  this has worked for me in my environment... and is not the end-all for everyone... just an example of how a program on the host os can create a problem...

The most common problem I see is someone creating a vm with 2 processor because they have 2 host processors... If you have configured your vm's to run with 2 processor switch them to one and you problem will be fix...

---

### Post by Meow27 on 2008-06-22
i dont know about that......for me it seems like VMware doesnt even take memory from the ram but from the hard drive.... i always get errors that im running low on ram when i have plenty (2 GB and 1 GB is given) from what i see, as i see this error, i check how much sapce is on my host partition, and i see that its VERY low. i just dont get why it cant use the computer's actual memory......Virualbox does it like a charm but VMware doesn't

---

### Post by zgornel on 2008-06-23
> **Meow27 said:**
> i dont know about that......for me it seems like VMware doesnt even take memory from the ram but from the hard drive.... i always get errors that im running low on ram when i have plenty (2 GB and 1 GB is given) from what i see, as i see this error, i check how much sapce is on my host partition, and i see that its VERY low. i just dont get why it cant use the computer's actual memory......Virualbox does it like a charm but VMware doesn't
You can tell vmware to use only memory and not to swap.

---

### Post by Akeldama on 2008-06-23
> **zgornel said:**
> Have you checked how much of the system resources are allocated to vmware (how much processor /memory it consumes), it might be a memory leak or some sort of bug. Do you have virtualization suport enabled ? I'll check at home, maybe my virtual machine behaves the same ... What resources have you allocated to the gues os ? (including the type of drive - persistent/non-persistent, scsi, etc)

When I 'grep vmx /proc/cpuinfo' I get output flags for all four processors, so I assume that virtualization support is enabled.

As for system resources allocated to the VM, I've tried 1gb and 512mb of ram and neither setting makes a difference in regards to my problem. I've tried one and two processors, and the single processor setting is definitely faster. I've preallocated drive space for the VM, so the disk image isn't constantly being resized. Its a virtual IDE and is persistant. The CD-ROM is disabled most of the time. I only enable it to install software. I've told Vmware to fit all virtual machine memory into reserved host RAM. I recently changed to this setting, before it was set to allow the virtual machine memory to be swapped. Changing this setting seems to have had no effect with my issue.

Regarding the memory leak, I have system monitor running in my panel, and it has never gone above roughly 50% memory in use by programs, naturally all of the remaining memory is usually taken up by cache.

---

### Post by Akeldama on 2008-06-23
> **dpj23 said:**
> More than likely it is a memory leak from the host system...  A person can allocate say 1GB towards the vm and still have plenty for the host...  However, the more and more the programs loop around the more and more memory gets eaten up...

I know this isn't a quick and easy answer for you... but, it might be good to look at what programs are running on the host besides the virtual machine...  I have found that thunderbird at times can create a memory leak... so, when I run my vm's for extended amount of time... I usually make sure not to use that program...  Now, before anyone rips me...  this has worked for me in my environment... and is not the end-all for everyone... just an example of how a program on the host os can create a problem...

The most common problem I see is someone creating a vm with 2 processor because they have 2 host processors... If you have configured your vm's to run with 2 processor switch them to one and you problem will be fix...

I thought Thunderbird might be causing my issue as I've had memory problems with Thunderbird in the past, so I completely switched over to Evolution Mail. This switch did not solve my issue with Vmware.

Other than Evolution Mail and Vmware Workstation, throughout a normal day I usually have Rhythmbox, Firefox and a terminal running.

Initially I tried using the 2 processor setting, but performance was abysmal! I've been using the single processor setting for quite some time now.

---

### Post by zgornel on 2008-06-23
Is the host system performance degrading as well or is it exclusively a gues os (XP) problem ? I experienced no slowdown with my XP guest. What version of XP is it (service pack) ?

---

### Post by Akeldama on 2008-06-24
> **zgornel said:**
> Is the host system performance degrading as well or is it exclusively a gues os (XP) problem ? I experienced no slowdown with my XP guest. What version of XP is it (service pack) ?

Honestly, I don't really notice any performance issues with the host system.

The guest OS is XP Professional SP2 + a ton of installed updates.

---

### Post by Julian Lewis on 2008-06-26
> **zgornel said:**
> Is the host system performance degrading as well or is it exclusively a gues os (XP) problem ? I experienced no slowdown with my XP guest. What version of XP is it (service pack) ?

Interesting, I set the CPU monitoring GUI active on both systems, Windows XP Task manager, and System Monitor under Ubuntu.
My windows virtual machine was showing a movie, every now and the task manager shows a peak on CPU usage. (I have a quad, and allocated 2 to vmware VM XP Pro). 
Occasionally the video froze/hick-upped, glitched.. and a very strong corresponding peak was observed on the windows task manager CPU usage graph. I watched the Ubuntu system monitor and all four CPUs were nearly flat. To my surprise, there is no correlation between the windows and ubuntu CPU activity graphs.
I think this observation could have some relevance about VMWARE performance.
   Cheers Julian
:confused:

---

### Post by Akeldama on 2008-06-26
Perhaps this is some strange performance bug that applies to quad core processors? I also have an old laptop that I use on a daily basis. It has only 756mb of ram and an Intel Celeron M 1.5GHz processor. I'm running 8.04 Hardy on it as well, and I have none of these performance issues in the WinXP Pro VM.

---

### Post by Akeldama on 2008-07-18
I've done some further testing on this issue and have narrowed the problem down to my email application.

From a fresh boot, I opened Firefox with about 10 open tabs, opened Rhythmbox and started it playing my entire collection of songs, and finally launched Vmware Workstation, started the WinXP virtual machine, and opened several applications within it.

I left the computer running in this state for roughly 12 hours. Upon my return, I tested the VM, and performance was snappy. Without closing any currently running applications, I launched Evolution Mail. Within 10 minutes, I noticed performance degradation with the VM.

I suspect that this issue would continue with Thunderbird if I used it instead of Evolution. Initially I was using Thunderbird and thought it might have something to do with this VM issue, so I switched to Evolution.

Any suggestions?

---

### Post by oligoelemento on 2008-10-26
I've the same problem. I have a Fedora 8 host with VMware WS 6.0 and Windows XP Pro as guest. After using Windows 10 minutes it goes anormally slow. I don't use Thunderbird, so it's no a memory leak from it.

Next week I'm going to try VirtualBox and VMware WS 5.5, perhaps it's only a VMware VW 6 issue.

---

### Post by Akeldama on 2008-10-27
oligoelemento,

Please keep us updated on your situation. Currently I'm running Vmware Workstation 6.0.4 build-93057 (I know there are newer versions, I just haven't upgraded yet), and I still have this problem.

---

### Post by oligoelemento on 2008-10-30
After trying several [performance tricks ]("http://maple.rsvs.ulaval.ca/mediawiki/index.php/VMWare_tips_and_tricks")in my VMware WS 6.0 Fedora 8 host I observed no improvements running Windows guest. While in Windows host I don't observe this performance degradation.

Finally, I've tested VMware WS 6.5.0, VMware WS 5.5.8 and VirtualBox 2.0.4 in my Fedora 8.

VMware WS 6.5 has similar performance problems than 6.0.

VMware WS 5.5 works better than 6.0 and 6.5 in linux. I'm still testing but I could say it works ok, without performance degradation. Unique defect is USB 1.1 ports. In VMware WS 6 there is an option to convert virtual machines to 5.5 format.

VirtualBox 2.0.4 also works ok, similar performance to VMware WS 5.5. But it's a bit [tricky its USB support]("http://www.spodesabode.com/discussion/34/-googleadsectionstart-usb-fix-for-virtualbox-on-fedora-8-host-googleadsectionend-/") and it doen't recognise my pendrive, but it recognises my portable hard disk and my scanner.

I'll continue testing both, but I'd like to hear from others experiences with VirtualBox and VMware.

PD: it helps to performance to desactivate services like yum-update or similar

---

