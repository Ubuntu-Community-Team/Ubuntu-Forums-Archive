---
title: "How to use KVM as easily as Virtualbox?"
date: 2023-03-19
forum: Virtualisation
---

### Post by Tadaen_Sylvermane on 2023-03-19
I don't use either much these days but something has puzzled me. People recommend kvm > vbox most of the time. Yet in my experience i can't get near the performance (when testing gui stuff) that Virtuabox can give me. Guest additions alone make it a whole new machine so to speak. Is there a guide somewhere that advises how to make full use of kvm for gui stuff or is passthrough pretty much a requirement for gpu stuff?

---

### Post by TheFu on 2023-03-20
For desktop-on-desktop VMs, virtualbox isn't bad, if you can swallow the "guest additions" non-F/LOSS license from Oracle.
KVM started out for server-on-server virtualization and grew to a support server on desktop and desktop on desktop virtualization.  Since 2016, the performance of desktop-on-desktop virtualization for KVM has improved drastically.
Spice, VirGL GPU, Virtio GPU or Intel GVT-g are all the main options today. [https://www.reddit.com/r/VFIO/comments/ufseh1/virgl_vs_gpu_passthrough_vs_virtio_or_qxl/](https://www.reddit.com/r/VFIO/comments/ufseh1/virgl_vs_gpu_passthrough_vs_virtio_or_qxl/)

Since I usually connect to my desktop over a network connection, I use spice when not going over the internet.  This is great for non-gaming desktop needs.  Office productivity stuff works like it is local.  Video editors do not.  Slow games work fine, but FPS or even Tuxcart doesn't run great using Spice.

If you remove the GPU part of the question, KVM is the fastest hypervisor that I've used. It is also extremely stable. I can't remember the last time any KVM VM had an issue related to the VM - it has been years.
Used ansible to see the uptime for most of my systems:
```
 12:25:17 up 16 days, 49 min,  5 users,  load average: 0.79, 0.90, 0.91
 12:25:17 up 16 days, 49 min,  1 user,  load average: 0.06, 0.06, 0.01
 12:25:17 up 5 days, 14:50,  2 users,  load average: 0.08, 0.02, 0.01
 12:25:17 up 16 days,  1:33,  2 users,  load average: 0.30, 0.12, 0.10
 12:25:17 up 16 days, 49 min,  1 user,  load average: 0.13, 0.03, 0.01
 12:25:17 up 16 days, 49 min,  1 user,  load average: 0.00, 0.00, 0.00
 12:25:17 up 16 days, 49 min,  1 user,  load average: 0.11, 0.21, 0.24
 12:25:17 up 16 days,  1:03,  1 user,  load average: 0.19, 0.07, 0.07
 12:25:17 up 14 days,  1:00,  1 user,  load average: 0.19, 0.07, 0.07
 12:25:17 up 15 days, 17:37,  1 user,  load average: 0.19, 0.07, 0.07
 12:25:18 up 16 days, 54 min,  1 user,  load average: 0.19, 0.07, 0.07
 12:25:18 up 16 days,  1:03,  5 users,  load average: 0.19, 0.07, 0.07
```
Anyways, very stable, but only a few are non-servers.

---

### Post by MAFoElffen on 2023-03-20
monkeybrain20122 and I both Tested VirGL when it came out. We both have played TuxCart on VM's using VirGL for about a year and a half nowL. That works great. We found that VirGL works better on Intel CPU's than AMD.

---

### Post by TheFu on 2023-03-20
> **MAFoElffen said:**
> monkeybrain20122 and I both Tested VirGL when it came out. We both have played TuxCart on VM's using VirGL for about a year and a half nowL. That works great. We found that VirGL works better on Intel CPU's than AMD.

Accessing the desktop system over a network?
Or is this just local access.  In my remote connection attempts, I had to use QXL + SPICE.  For local connections, I am able to choose virtio for the video option rather than QXL or VMVGA or Cirrus or ... whatever the other options are.

Is this a 22.04 option or was it working well under 20.04 libvirt too?  I'm not seeing VirGL in libvirt options on 20.04.

I need a features and release table to keep all this stuff straight.

---

### Post by MAFoElffen on 2023-03-21
Was in QEMU 6.0 and later. So is in 22.04. (And works with Spice.)
```

mafoelffen@Mikes-B460M:~$ kvm --version
QEMU emulator version 6.2.0 (Debian 1:6.2+dfsg-2ubuntu6.6)
Copyright (c) 2003-2021 Fabrice Bellard and the QEMU Project developers

```
RE: [https://wiki.archlinux.org/title/QEMU/Guest_graphics_acceleration#Virgil3d_virtio-gpu_paravirtualized_device_driver](https://wiki.archlinux.org/title/QEMU/Guest_graphics_acceleration#Virgil3d_virtio-gpu_paravirtualized_device_driver)

As I remember: We had to manually add it via the XML in the VM Domain configs for it to work. It wasn't something that could be done automatically (menu driven) from Virtual Manager to get it to use the driver. It took some trial and error playing around to get it to work. I can remember we kept messaging each other on what each others challenges were until we got it working. Once we got it working, it did work well. But only works for OpenGL and Mesa types of 3D Acceleration.

---

### Post by TheFu on 2023-03-22
Sigh.
```
$ kvm --version
QEMU emulator version 4.2.1 (Debian 1:4.2-3ubuntu6.24)
```
  And that's for a relatively new install on hardware here.
"Relatively new" means 20.04.  We all have different ideas for what "new" means. ;)

Maybe in 2 more years.

---

### Post by SeijiSensei on 2023-03-22
On 22.04 I have
```
QEMU emulator version 6.2.0 (Debian 1:6.2+dfsg-2ubuntu6.6)
```

---

### Post by ajgreeny on 2023-03-22
> **MAFoElffen said:**
> monkeybrain20122 and I both Tested VirGL when it came out. We both have played TuxCart on VM's using VirGL for about a year and a half nowL. That works great. We found that VirGL works better on Intel CPU's than AMD.
I saw this post just after you wrote it and had been trying to figure out how to use VirGL since then but had no time to search properly until tonight. I have now enabled it and found it works very well using my Intel HD 4600 and is easy to enable using these few changes needed in the Details window of virt-manager.
Firstly in the host OS install ***virgl-server***
[LIST=1]
[*]In the Display Spice enable ***Listen type*** to ***None*** then enable ***Open GL.***
[*]Set ***Video Virtio*** and enable ***3D acceleration***.
[/LIST]

This seems to give very smooth and fast graphics compared to the non GL I was using previously.

---

### Post by ajgreeny on 2023-03-26
Having been trying this for a few days now I unfortunately have had to go back to using **Listen type: Address ** for the display spice server and **disabled OpenGL** option as I was seeing a very strange delay in moving any windows on the screen, making it unusable for me.

Perhaps this is a result of using fairly old lower power Intel graphics but it's all I have so no way to try anything else.

---

### Post by monkeybrain20122 on 2023-03-26
It was not easy to set up shared folders in kvm. But now there may be an easy way because of virtiofs. [https://www.debugpoint.com/share-folder-virt-manager/](https://www.debugpoint.com/share-folder-virt-manager/)

I have deleted the vm so I can't test it now.

---

### Post by ajgreeny on 2023-03-26
Thanks for that link monkeybrain20122, I shall give that a try as soon as I'm able and will report back here.

---

### Post by TheFu on 2023-03-26
> **monkeybrain20122 said:**
> It was not easy to set up shared folders in kvm. But now there may be an easy way because of virtiofs. [https://www.debugpoint.com/share-folder-virt-manager/](https://www.debugpoint.com/share-folder-virt-manager/)

I have deleted the vm so I can't test it now.

NFS works fine and at 38.6 Gbits/sec (that's the slowest from iperf3 test)  for intra-computer networking, it is VERY fast.
```
[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-10.00  sec  48.5 GBytes  41.7 Gbits/sec    0             sender
[  5]   0.00-10.04  sec  48.5 GBytes  41.5 Gbits/sec                  receiver
```
Very fast.

---

### Post by ajgreeny on 2023-03-27
Something else to try with NFS which I've never used though I have used SSH very successfully.

I'm learning every day!

---

### Post by TheFu on 2023-03-27
> **ajgreeny said:**
> Something else to try with NFS which I've never used though I have used SSH very successfully. 

I treat NFS storage like it is local storage ... because it performs that way.  It is another good reason to avoid snaps, which used to have issues with all NFS storage. I don't know if that is still true, but snaps certainly don't like HOME directories on NFS storage.

---

### Post by tea for one on 2023-03-27
> **monkeybrain20122 said:**
> It was not easy to set up shared folders in kvm. But now there may be an easy way because of virtiofs. [https://www.debugpoint.com/share-folder-virt-manager/](https://www.debugpoint.com/share-folder-virt-manager/)
I have deleted the vm so I can't test it now.
Thank you, monkeybrain20122, your link is very useful.
I've just tested it and achieved a perfect result.

---

### Post by TheFu on 2023-03-27
Just saw that in the Pwn2Own 2023, that virtualbox and VMware Workstation were cracked from inside a VM to gain host access.
There were also a few Ubuntu Desktop local privilege escalation cracks this year by multiple teams.> 
The highlight of the day was the Ubuntu Desktop operating system getting hacked three times by three different teams, although one of them was a collision with the exploit being previously known.

The three working Ubuntu zero-day were demoed by Kyle Zeng of ASU SEFCOM (a double free bug), Mingi Cho of Theori (a Use-After-Free vulnerability), and Bien Pham (@bienpnn) of Qrious Security.

While the first two were each awarded $30,000 for their zero-day exploits, Pham only earned $15,000 due to a bug collision.

Tesla had a bad year too.

Of course Windows11 and MSFT-Teams were included and successfully cracked a few times each, along with MS-Sharepoint.
Day 1: [https://www.bleepingcomputer.com/news/security/windows-11-tesla-ubuntu-and-macos-hacked-at-pwn2own-2023/](https://www.bleepingcomputer.com/news/security/windows-11-tesla-ubuntu-and-macos-hacked-at-pwn2own-2023/)
Day 2: [https://www.bleepingcomputer.com/news/security/windows-11-hacked-again-at-pwn2own-tesla-model-3-also-falls/](https://www.bleepingcomputer.com/news/security/windows-11-hacked-again-at-pwn2own-tesla-model-3-also-falls/)
Day 3: [https://www.bleepingcomputer.com/news/security/windows-ubuntu-and-vmware-workstation-hacked-on-last-day-of-pwn2own/](https://www.bleepingcomputer.com/news/security/windows-ubuntu-and-vmware-workstation-hacked-on-last-day-of-pwn2own/)

I didn't see that KVM cracking was attempted, but there have been some client breakouts from KVM/QEMU in the past, usually related to forgotten older hardware emulations. There was some removal of the older hardware features in QEMU a few years ago, but for any complex software, there are always more bugs than known, often hundreds or many thousands more.

---

### Post by SeijiSensei on 2023-03-27
> **ajgreeny said:**
> Something else to try with NFS which I've never used though I have used SSH very successfully.
I have a CentOS server in my closet that runs both NFS and Samba. It makes things very easy when using virtual machines. Being able to transfer files between machines is simple. Shared folders are good if the content you need is on the host computer, but if you run multiple VMs on multiple hosts, having a central server is the way to go.

---

### Post by ajgreeny on 2023-03-28
Just for information, all my VMs are Linux distros, usually the various Ubuntu versions or things like Mint, based on Ubuntu, or Debian on which all the family are based.
I do not run them for any long periods, nor do I really use them for anything serious other then checking progress of the new versions, even before they're released and as soon as I've checked all is well I shut them down and most are then deleted after a few weeks, or once the new version has been released.

I accept that computing is never going to be totally 100% safe against determined crackers but I suspect my use of KVM VMs is as safe as anything can be.
Perhaps I'm wrong?

---

### Post by TheFu on 2023-03-28
An added bonus to using pre-existing, standardized, tools, is that more than 1 group has looked at the code and it has decades of active use in the world.  Can't say that for any VM-access-host-filesystem tools.  We know the security issues with NFS and CIFS and sshfs.
> 
I accept that computing is never going to be totally 100% safe against determined crackers but I suspect my use of KVM VMs is as safe as anything can be.
Perhaps I'm wrong? 
We can only do what we can do. Not that it means much, but I still use KVM/QEMU VM isolation as a security tool and hope that any flaws are quickly addressed by the F/LOSS teams. I have less trust in proprietary software, because to them it is just another bug in a huge, proprietary, list that nobody else will see.  Until a large customer is impacted, it won't become important enough to fix, unless a coder is already there doing something else.  That's the nature of proprietary software.  There are always paying customers waiting for new features, so they get priority over bugs, until the bugs are public AND impacting. Then we get to read > "we take the security of our products very seriously and do all we can to protect the data of our clients."

---

### Post by undecidable on 2023-04-02
Shared folders work poorly for any but the simplest cases.
See thread:
[https://forums.virtualbox.org/viewtopic.php?f=7&t=69097]("https://forums.virtualbox.org/viewtopic.php?f=7&t=69097")
for some of the issues.  
I have used NFS with OSS Virtualbox since 14.04 with no problems.
though it has a bit more of a learning curve and a bit more setup.

(apologies, was trying to do this as a reply to an earlier set of posts about shared folders on VBox,
somehow it ended up at the end).

---

### Post by mikodo on 2023-04-18
A bit more on shared directories. I was reading and saw the page below on SSHFS:

  [https://en.wikipedia.org/wiki/SSHFS](https://en.wikipedia.org/wiki/SSHFS) 

I imagine it will work for sharing directories between host and guest. Seems easy enough for even me to do, and is reported to be fast:

[URL="https://askubuntu.com/questions/15782/how-do-i-share-a-folder-with-another-linux-machine-on-the-same-home-network"]https://askubuntu.com/questions/15782/how-do-i-share-a-folder-with-another-linux-machine-on-the-same-home-network
[/URL]
Addendum:

I was thinking I would have to skip the auto-mount with /etc/fstab, because of it being a vm but, now I think I'll not have to. We'll see.   

Just my $.02 worth ...

---

