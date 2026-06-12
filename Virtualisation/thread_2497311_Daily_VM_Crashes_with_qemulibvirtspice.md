---
title: "Daily VM Crashes with qemu/libvirt/spice"
date: 2024-04-29
forum: Virtualisation
---

### Post by undecidable on 2024-04-29
Over the last few weeks I have been trying to move from Virtualbox to  qemu/libvirt/spice.
I had been using virtualbox since 2018 under Xubuntu 18.04 then Xubuntu 22.04.
Once you get over the (massive) learning curve,
I have found the Spice/Libvirt/qemu/kvm setup intuitive, transparent and really nice to work with.

The problem is:  
*over my 3 VMs I'm getting about 1 crash a day. * 

First there is 1 message like this on journalctl:
```
[drm:qxl_gem_object_create [qxl]] *ERROR* Failed to allocate GEM object (261100, 1, 4096, -12)
kernel: [drm:qxl_alloc_ioctl [qxl]] *ERROR* qxl_alloc_ioctl: failed to create gem ret=-12
```
followed by many messages like this, usually about every 15 seconds:
```
kernel: [TTM] Buffer eviction failed
kernel: qxl 0000:00:01.0: object_init failed for (3149824, 0x00000001)
kernel: [drm:qxl_alloc_bo_reserved [qxl]] *ERROR* failed to allocate VRAM BO
```

and then
```
X connection to :0 broken (explicit kill or server shutdown)
```
The virt-viewer  screen is frozen, 
However I can ssh in and reboot.  

The crash can happen if I am browsing,  or deleting a (shared) directory in the file manager, 
or when the VM is idle and I'm having a cup of tea.
I return to find it frozen.
It is independent of how much memory I allocate to the VM or to the QXL graphics driver.  

_Setup_
The VMs are on a clean install of Xubuntu 22.04 with the -hwe kernel linux-image-6.5.0-28
running on 2 different Xubuntu 22.04 hosts, one with 
the -hwe kernel linux-image-6.5.0-28-generic and one with the standard linux-image-5.15.0-105-generic.

_Versions_
I doubt it is relevant but the versions I am running:
qemu-system-x86  6.2, libvirt  8.0.0, libspice-vdagent  0.22.1, spice-client-gtk 0.39

It is *possible* that this kernel bug is the same:
[https://lore.kernel.org/lkml/db4c8e74-5c79-49be-9781-a5d8669eccc1@leemhuis.info/T/]("https://lore.kernel.org/lkml/db4c8e74-5c79-49be-9781-a5d8669eccc1@leemhuis.info/T/")
(though being an ordinary ignoramus I cant be sure)
and also I can't tell from the thread when / in what kernel version it will be patched
though it doesn't seem like in the 6.8 kernel in 24.04.  

Does anyone have any idea of possible causes?
or any mitigations I can take?
A crash in the middle of doing something serious could be disastrous.

---

### Post by ajgreeny on 2024-04-30
It would be interesting to know what VM settings you are using and your host machine spec.
How many CPU cores and how much ram do your VMs have allocated; which video setting do you use?

I have many VMs of Xubuntu Noble running in KVM/QEMU with no problems at all of the kind you are suffering from.

My VMs all have 4G ram from the 8G on the two host machines, one using the 5.15 kernel series, the other using the 6.8 hwe series.
I don't use QXL video but both use virtio video with no problems. Both hosts have integrated Intel video hardware without dedicated GPUs. 

Give us as much detail as you can and we may have a better chance to help you.
I've never used it in a VM but show us the output of terminal command
**inxi -Fzx**
which may give some clues.

---

### Post by undecidable on 2024-04-30
Thanks for the reply - here's the detail.

I run the VMs on 2 laptops with attached screens:
[LIST]
[*]Main machine with 32gb of ram, 12 cores and 3 screens, with the hwe kernel -6.5.0-28.  
On this machine I run the VMs in dual screen mode, keeping 1screen for the host..
[*]Warm standby with 64gb of ram, 12 cores and 2 screens with the standard kernel -5.15.0-105-generic.  
On this machine I run the VMs in single screen mode, keeping 1 screen for the host.
[/LIST]
Both machines use the integrated Intel Iris Xe Graphics

The 3 VMs are cloned from the same master VM and all 3 sent to both machines.
and I can test different parameters by editing the individual xml (in virt-manager).

For the VMs: Main memory: Either 6gb or 8gb, and 2 allocated cores.  
This is v similar to the configuration I used for vbox.  
Watching main memory and cpu utilisation, there is no strain on the host.  

Video memory:
I have tested, apart from the original default, the following in both single head and dual heads:
```

<model type="qxl" ram="131072" vram="131072" vgamem="32768" heads="2" primary="yes"/>
<model type="qxl" ram="262144" vram="262144" vgamem="65536" heads="2" primary="yes"/>
<model type="qxl" ram="262144" vram="524288" vgamem="131072" heads="2" primary="yes"/>
<model type="qxl" ram="262144" vram="524288" vram64="1048576" vgamem="131072"  heads="2" primary="yes"/>
```

Had never come across inxi, but it provides quite nice output - below, from 1 of the VMs:

```
System:
  Kernel: 6.5.0-28-generic x86_64 bits: 64 compiler: N/A Desktop: Xfce 4.16.0
    Distro: Ubuntu 22.04.4 LTS (Jammy Jellyfish)
[redacted]

```

Let me know if there is anything else useful I can provide.

---

### Post by ajgreeny on 2024-04-30
That is, I'm afraid, way past my skill-set to interpret very helpfully.
You real hardware is much newer and should be more capable than mine which is now 11 and 10 years old, neither with two monitor output.
I will look at my VM inxi output later to see if any clues are available from that when compared with yours.
Watch this space!

---

### Post by undecidable on 2024-04-30
"That is, I'm afraid, way past my skill-set to interpret very helpfully."
(chuckle) - yes, mine also.;)

But there is one idea you have given me: you are using Virtio, whereas I am using QXL.

The kernel bug I referenced in the 1st post specifically refers to QXL:
> Steps to reproduce:
> 1) Install Debian 12 as a virtual machine using virt-manager, choose qxl
>    graphics card...

I had thought Virtio was older and less functional than QXL, and didn't support dual screens
 - but really the documentation is very sparse.

So I just changed 2 of the VMs on the warm standby to Virtio, and put them in dual screen mode, and it seems to work with no problems.

So I'll leave them like that for a few days and see which machine is more stable.
Will update when I have any useful information.

---

### Post by ajgreeny on 2024-04-30
Sounds like a possible answer doesn't it!

Do please let us know as it would be good to see a more definitive answer to your problem.
I'm not on a Linux box  at the moment but using an Android tablet  so I can't even look to see what video options are available when setting up a new virtual machine but I seem to recall there are more than just those two options.

Next time I create a new VM I might try using QXL to see what difference, if any, it makes to the system stability compared to virtio.

---

### Post by undecidable on 2024-04-30
Of course will do.  
I have split the machines today to see how it goes.

The options available in virt-manager are:
[LIST]
[*]None
[*]Bochs
[*]QXL
[*]Ramfb
[*]VGA
[*]Virtio
[/LIST]

Best explanation of seen of them is at:
[https://www.kraxel.org/blog/2019/09/display-devices-in-qemu/]("https://www.kraxel.org/blog/2019/09/display-devices-in-qemu/")
though it doesn't compare QXL and Virtio other than from the point of view of compatibility.


*"I might try using QXL to see what difference, if any, it makes to the system stability compared to virtio"*
This bug seems to keep coming back.
I saw people mentioning it as a regression in 4.7& 4.8, 
5.0.n it was still there, it is in my 5.15 & 6.5 kernels,
yet somewhere on the kernel thread it was said they had only been notified of it 120 days before
and to fix it would restore some code that had been removed.  

Of course they speak a variation of Ancient Greek so I may be misinterpreting.

---

### Post by undecidable on 2024-05-05
Circling back here with the results from 4 days running VMs with either QXL or Virtio.

1.  remarkably, no crashes in either. 
Why no crashes in the QXL VMs for 4 days I have no idea.
Despite what Einstein said, I suspect God does play dice with the Universe.

2.  Performance seems similar. so no idea what the difference is. 

3.  But,  I have now converted all graphics to Virtio - it is much easier to use:

**_Starting Dual Screen with QXL - like feeding a 1 year old porridge_**

When you start a dual screen QXL VM in virt-viewer, only 1 screen comes up.
You then have to wait till you can log in,
then get your mouse to the top of the virt-viewer menu
 then click View / Displays / Display 2.

It is chaos then trying to place the 2nd window & resize by hand, 
(many reasons, one is that 2nd window could end up under the 1st window, the cursor could be grabbed,...)
so I have a host script I manually run in a terminal somewhere after manually enabling the 2nd screen
 which then places and resizes both windows,
 and * then* a guest script using xrandr's to get them both to the correct resolution,
The guest script needs several attempts with a sleep in between 
as it can't be sure when the host script has run.

**_Starting Dual Screen with Virtio - kid is now 4, eats porridge with minimal entropy _**

With Virtio, both windows come up immediately, which means the resizing and placing of windows 
 can happen in the one start VM script with no manual intervention, 
 and the script in the VM to set resolution can also run automatically
 as it knows if it is being called, the host script has already run.
 
 Much more polite and orderly.  
 If only I could persuade my descendants to be similarly orderly.
 
(Of course, there are 2 things I still don't understand:
 1.  why virt-viewer can't remember the window sizing and placement.  
 Most other programs can.
 2.  why the guest doesn't know the display resolution, and settings/display is ignored,
 necessitating running xrandr on every startup.  
 But these are minor questions, overall once you have the scripts, it works well. )

I should also add a thank you to ajgreeny for giving me the solution: Virtio instead of QXL.

---

### Post by MAFoElffen on 2024-05-05
Glad you found a solution...

I was wondering if you were running these cloned VM's at the same time as each other?

I tend to use Spice/QXL as my KVM defaults. I don't have this problem with mine. I also create VM templates that I clone from... But for the templates, I do virt-sysprep on them so there are not any underlying conflicts in running them concurrently:
> 
Virt-sysprep can reset or unconfigure a virtual machine so that clones can be made from it. Steps in this process include removing SSH host keys, removing persistent network MAC configuration, and removing user accounts. Virt-sysprep can also customize a virtual machine, for instance by adding SSH keys, users or logos. Each step can be enabled or disabled as required.

Another thing is the unique machine-id...

---

### Post by undecidable on 2024-05-05
I do run three dual-screen clones at the same time, on 3 different host virtual screens.
I also sync them nightly to my warm-standby, so they are running on 2 hosts.

I delete and recreate them weekly from an updated master (your "templates").
The xml's (initially created with virt-clone) I keep and re-use to recreate the clones.  

I looked at sysprep when I was working out my procedures, but realised it wasn't necessary.
Most of the information which needs to be unique is in the xml (clone uuid, mac address, filenames).
Only major item not in the xml is the hostname.   
I can't think of anything else which needs to be unique?
  
So to clone I simply do a physical copy of the master .raw
create qcow2's using it as a base (qemu-img create)
then define each clone using its (backed up) .xml
which points to the new .qcow2 (virsh define).

Each clone has a unique data disk (/dev/vdb) holding the hostname (symlinked), and state info,
and the virsh define using the .xml also brings in this data disk.

wrt the sysprep functions:
1.  I want them to have the same user accounts.
2.  mac addr is in the .xml
3.  I dont ssh from the clones, so they dont need their own private keys
  I do ssh into them if there is a problem but for that they store the host public key. 
4.  it is no problem that the fstabs are the same.

I was wondering if you were thinking that the crashes might somehow be related to some lack of uniqueness
in the VMs, or running 3 QXL instances at once.  
Seems unlikely (but of course not impossible) given that only 1 VM interface was crashing at a time
and that there were kernel messages in the guest but not the host.  
Over 3 VMs on each of 2 hosts, in a day maybe 1 would crash, or one on each host would crash.

---

### Post by MAFoElffen on 2024-05-09
Dang it...

All through DEV-Noble, the dailys were fine for me, installing them in KVM with Spice/QXL. 

Since the release... I just spun up a release ISO 24.04 with my defaults (Spice & QXL) for filing a bug on something unresolved, where the bug report got closed... and the screen is black in the Live Environment unless I use nomodeset on the boot.

This is LTS... I'll file a bug report on that. If I don't, then that will bite us in DEV-Ocular, when the Daily's are available for that.

---

### Post by undecidable on 2024-05-14
Added an entry to an existing bug on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-qxl/+bug/1972914](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-qxl/+bug/1972914)

though there is also a more relevant kernel bug thread there:
[https://lore.kernel.org/lkml/db4c8e74-5c79-49be-9781-a5d8669eccc1@leemhuis.info/T/](https://lore.kernel.org/lkml/db4c8e74-5c79-49be-9781-a5d8669eccc1@leemhuis.info/T/)

It seems to be being addressed, but not clear in which kernel version.

---

