---
title: "Ubuntu Server VM setup with KVM"
date: 2013-09-17
forum: Virtualisation
---

### Post by Volo on 2013-09-17
Hello.

A couple of months ago I decided to build a home server and since, I've been researching about every possible aspect I can think of. Now I'm close to actually building the machine and start setting up the system. Before I do it I wanted to ask for some opinions on virtualization. I'm gonna try to make this as brief as possible, though it's hard or me to write this in English.

I plan to run ubuntu server 12.04 LTS. I want this system to host multiple VM using KVM. The main reason I want to do that is so I can separate different services, and so if a part of the system breaks it won't be as terrible. This is what I was thinking:

-The host to run basic services. With this I mean printing and backups for all of the computers in my house.
-A VM running ubuntu server 12.04 which I want to use only as a media server. Here I plan to include torrenting, and media streaming on the local network and also over the internet (less often), and also on the fly transcode.
-A VM running ubuntu server 12.04 for a camera monitoring system. I plan on having 2-3 security cams on the outsides of my house and be able to remotely watch what those cameras are seeing. I'm not sure how to implement this yet but I'm sure I'll eventually find out a way.
-A VM running windows so I can use windows apps from my ubuntu laptop. I mostly plan to run office on the server and use it from my laptop. That way I'll finally be able to not have to dual boot linux and windows.

The machine I'm building is capable of running this number of VM's. The thing I'm not sure is if running the "basic" services on the core installation is the best idea. Another alternative would be to run an additional ubuntu VM for the printing and backups services. 
Or it might also happen that I'm overusing the virtualization concept and a better solution would be to have only 2 VM, one for the windows OS and another for the media server, having all the rest on the core install.

I hope I was clear enough. Basically I want to be sure if what I plan to do with VM's makes sense or not for a home server. Maybe it is an overkill and it'll brng more problems than it'll solve. Or maybe it's the perfect idea. I just want to be sure before I invest serious time setting up the system, this way I don't have to do everything again if I make a terrible mistake.

I trully appreciate any response, comments, tips you can give me!
Thanks!

---

### Post by sudodus on 2013-09-17
I'm using virtual machines only to test different various operating systems and tweaks so I am no expert in running a server with virtual machines. I think your concept is good, provided you have enough horsepower and memory in your host computer. So try with one system, and compare the performance running some application program in KVM to running it in the host operating system (without virtualisation).

-o-

I have been using VirtualBox for years, and I am only recently starting to learn how to use KVM. I have installed virtual machines using KVM, qemu, and virt-manager according to this wiki page

[https://help.ubuntu.com/community/KVM/VirtManager](https://help.ubuntu.com/community/KVM/VirtManager)

and it works well provided I run it in a computer with hardware virtualisation

[URL="http://pic.dhe.ibm.com/infocenter/lnxinfo/v3r0m0/topic/liaai.kvminstall/liaaikvminstallenable.htm"]http://pic.dhe.ibm.com/infocenter/lnxinfo/v3r0m0/topic/liaai.kvminstall/liaaikvminstallenable.htm
[/URL]
One advantage with KVM for me is that it can use virtual disks of many kinds, for example images of USB drives, which can be mounted as SATA drives. If it is the first drive, the virtual machine will boot from it. I use this method to test the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971").

---

### Post by Volo on 2013-09-17
Thanks for your answer. The computer is going to have 16GB RAM so I don't think there's gonna be a problem with running the VMs. I I think I'll give a try, at least it's gonna be fun since I don't have any experience and it's gonna be all learning.

One noob question in case someone can answer it. Should I leave a lot of free space for the core install (ubuntu server host) and install all of the VMs in there? Or should I use a different partition to insrtall the VM? maybe a different drive? Right now I was thinking of installing the VMs somewhere on the host's / directory, or maybe in ts /home directory but I'm not sure if it'll be the best idea.

---

### Post by sudodus on 2013-09-17
I think it is a good idea to have the VMs and particularly the virtual disks in another partition (not the root partition of the host OS). That partition can be on another drive or not, depending on how much you can invest in the machine.

For example, it makes it easier to separate the backup for the different parts.

---

### Post by Volo on 2013-09-17
Ok, I'm going to do that then. That way I can leave the host install as basic as possible. Thanks a lot. It seems I'm gonna be having lots of fun in the near future :)

---

### Post by sudodus on 2013-09-17
Good luck :-)

---

### Post by TheFu on 2013-09-18
Your plan seems fine, though running a desktop OS VM on a server will be a challenge - no GUI.  As long as you have another machine with a desktop, then you can remote into the "desktop VM".  Just be smart about that and avoid using VNC. Don't expect audio or video playback to work without using Spice.  I use NX to remote into my "private cloud desktop"- works great for office productivity apps from anywhere in the world with minimal bandwidth.

Adding a GUI to a server reduces the stability. Servers without GUIs work for years. With a GUI, we talk about months.  It is probably just fine for most home users.

I'd put the VMs on a different HDD and avoid running anything except file services from the hostOS.

Having a separate VM just for camera monitoring is 1000x overkill. It will be 1 tiny process snapping a photo every 5-10 seconds with a datestamp.

Transcoding is a terrible thing to put into a VM, constant CPU use. It isn't a nice VM neighbor and will suck all available CPU from the system, impacting other VMs. Sure, you can tune the VM settings, but that is an advanced setup.

16G of RAM is overkill for 4 VMs.  Windows will work great in 2G and even the heaviest Linux VMs are happy with 1-1.5G of RAM.  Just leave 1 vCPU and 1G of RAM for the hostOS.

For storage, you have lots of options.  Many people put each VM into a separate volume group under LVM2. Great flexibility, but a little more complexity.  If you use snapshots for backups, it remove any downtime. Impressive.  I prefer to backup from inside each VM these days. Use to do it from the hostOS, but found that too cumbersome and not portable enough to other systems. I probably didn't understand something.

Watch out for VM sprawl. We all have it.

---

### Post by CharlesA on 2013-09-20
Yes, I'm late to the party. :p

> **TheFu said:**
> Your plan seems fine, though running a desktop OS VM on a server will be a challenge - no GUI.

I run Ubuntu Desktop 12.04 on my Proxmox host, but I also access the thing via SSH 99% off the time as it's pretty much been depreciated as a web development box. So you can run a Desktop OS, but it is a bit more difficult unless you have console access. Does virtmanager let you do that?

> 16G of RAM is overkill for 4 VMs.  Windows will work great in 2G and even the heaviest Linux VMs are happy with 1-1.5G of RAM.  Just leave 1 vCPU and 1G of RAM for the hostOS.

Indeed. I've been meaning to bump my Win7 VM from 4GB to 2GB of RAM as the damn thing is idle more often than not.

> For storage, you have lots of options.  Many people put each VM into a separate volume group under LVM2. Great flexibility, but a little more complexity.  If you use snapshots for backups, it remove any downtime. Impressive.  I prefer to backup from inside each VM these days. Use to do it from the hostOS, but found that too cumbersome and not portable enough to other systems. I probably didn't understand something.

I have all my VMs stored in a folder (proxmox handles the rest) on my RAID6 array, but that's probably overkill. The array is running LVM2, so I can do snapshots and stuff with little problem. :)

> Watch out for VM sprawl. We all have it.

The VMs.. they are everywhere!

---

### Post by TheFu on 2013-09-22
> **CharlesA said:**
>  So you can run a Desktop OS, but it is a bit more difficult unless you have console access. Does virtmanager let you do that?

Yes. virt-manager provides console access via VNC. It sucks compared to NX for performance - feels about 10x slower even just for text.

> **CharlesA said:**
> Indeed. I've been meaning to bump my Win7 VM from 4GB to 2GB of RAM as the damn thing is idle more often than not.

2G has been [working here]("http://blog.jdpfu.com/2012/02/06/running-windows7-media-center-inside-a-kvm-vm") for the Win7 Media center VM. It just records shows using an HDHR3 network tuner. Highly recommended setup, BTW.

> **CharlesA said:**
> I have all my VMs stored in a folder (proxmox handles the rest) on my RAID6 array, but that's probably overkill. The array is running LVM2, so I can do snapshots and stuff with little problem. :)


Can you restore a snapshot to another machine?
I try to put VM virtual HDDs as single files on a raptor, though I know companies who use RAID1 SSD storage and find that FANTASTIC for VM storage - plus they can use sparse allocations.  They are using server-class SSDs, not the cheap stuff sold to hobbyists.  If running just 1 or 2 VMs, the driver performance isn't too bad as long as USB is avoided - including USB3. Seems the USB drivers have queuing problems when too many requests are made. If using file-based V-HDDs, be certain to pre-allocate the entire HDD before installing any OS. I think that is 50% of performance issues on VMs - sparse V-HDD allocations. Avoid unless on SSDs.

> **CharlesA said:**
> The VMs.. they are everywhere!
Indeed.

---

### Post by Volo on 2013-09-22
Wow, a lot of new info, thanks! I have a couple of questions though.

How would I solve the problem of transcoding? TheFu you clearly advised advised against using a VM for for transcoding. I don't see that many options, I could only allow a limited number of CPU cores to work on that VM, if I'm not mistaken that could be easily done. Or should I look for a more drastic approach?

About where to install the guests, I have 3 drives, one SSD with 64GB where the host OS will be and nothing else, and two 2TB HDD  where everything else will be. Would it be a good idea using LVM to make a volume group for VM's where i use the 2 HDD so I can put 2 VM's on each drive and use the rest for storage? That way when I get new drives in the future I can easily add space to the VM volume group and move VM's to the new HDD so that way I am closer to having each VM on a different drive. It should be better than saving space for VM in only one HDD right? Or maybe I should put one of the VM on the SSD with the host OS while putting the others across the HDD?

I'm going to start doing the little research on NX so I can access the windows VM. NX is installed on the host OS right?

THanks guys, I really appreciate the help I've been getting in this thread. I never tought I would have gotten this much!

---

### Post by TheFu on 2013-09-22
I don't think Windows supports NX as a server, just a client.  NX has a client side and a server side.  To access Windows, I use rdp ... and it sucks. You could play with Spice, it might work better/easier than the list time I tried it.

As to disk drives ... the only time I've had massive data loss was when I extended VGs across multiple drives without having excellent backups.  3 drives were involved and the middle disk failed.  I was unable to access data on the other 2 drives.  I will not span disks without RAID1-10 AND without excellent backups of all the data.  In no way would I have use RAID0.
After that, do whatever you like - your needs are different from mine.

---

### Post by CharlesA on 2013-09-22
> **TheFu said:**
> Yes. virt-manager provides console access via VNC. It sucks compared to NX for performance - feels about 10x slower even just for text.

Ouch. I've been using the console that Proxmox provides (java-based VNC) and it seems fairly responsive. Not true to native speeds, but manageable.

> 2G has been [working here]("http://blog.jdpfu.com/2012/02/06/running-windows7-media-center-inside-a-kvm-vm") for the Win7 Media center VM. It just records shows using an HDHR3 network tuner. Highly recommended setup, BTW.
Nice, I might have to give it a shot. As of now, I only really use that VM for Office and other stuff when I am not at home.

> Can you restore a snapshot to another machine?

Haven't tried it. Now that I poke around in the directory the VM is stored, I don't see any actual snapshots. Does KVM use one file for everything? I've been running qcow2 hdds.

> **Volo said:**
> How would I solve the problem of transcoding? TheFu you clearly advised advised against using a VM for for transcoding. I don't see that many options, I could only allow a limited number of CPU cores to work on that VM, if I'm not mistaken that could be easily done. Or should I look for a more drastic approach?


I wouldn't do transcoding on anything that didn't have a beefy video card. Transcoding with the CPU only can be daunting.

> **TheFu said:**
> I don't think Windows supports NX as a server, just a client.  NX has a client side and a server side.  To access Windows, I use rdp ... and it sucks. You could play with Spice, it might work better/easier than the list time I tried it.

I just use RDP and it runs fine for me over SSH.

---

### Post by TheFu on 2013-09-23
> **CharlesA said:**
> Ouch. I've been using the console that Proxmox provides (java-based VNC) and it seems fairly responsive. Not true to native speeds, but manageable.
I just can't load java.  Our CSO won't allow it.  The KVM console uses VNC, but it feels like an extra slow VNC to me. I haven't used VNC server inside a VM in about 2 yrs.  It is hard to explain, but NX on the same machine feels 2-3x faster AND NX bandwidth can be talored by the client connection .... GigE LAN to 14.4Kb dial up.

> **CharlesA said:**
> Nice, I might have to give it a shot. As of now, I only really use that VM for Office and other stuff when I am not at home.  I actually find that remoting in via NX, then using RDP from the Linux Desktop is faster. Strange?

> **CharlesA said:**
> Haven't tried it. Now that I poke around in the directory the VM is stored, I don't see any actual snapshots. Does KVM use one file for everything? I've been running qcow2 hdds.  
KVM can do whatever you like for storage. Partitions, logical volumes, any of 5+ different single-file storage methods or split the files into 2G sizes.  You realize that Proxmox is just a GUI over KVM and LXC, right?  Or is that Xen?

> **CharlesA said:**
> I wouldn't do transcoding on anything that didn't have a beefy video card. Transcoding with the CPU only can be daunting.  I've never had anything called a "beefy GPU" in any of my machines and I transcode all day long - Core i5.  I think that machine has a $20 video card.  I recall being pissed when the 7600gs died and having to spend the money for any new video card at all.

> **CharlesA said:**
> 
I just use RDP and it runs fine for me over SSH.
Charles!  I need to get you converted to NX. You don't know what you are missing.  ;) After you try it, you'll never go back.

We should probably work out a Spice How-to for the rest of the world too. Getting Spice to work should bring audio and video to remote desktops with encrypted tunnels built-in.  I think spice can only be performed under KVM virtual machines.  I've had it working for a few days, but it wasn't stable.  Spice clients exist for Windows and Linux ... don't know about OSX.  Spice server code appears to be available for Windows and Linux too.  Both **must** run under a special KVM process (kvm-spice) to work.

---

### Post by CharlesA on 2013-09-23
> **TheFu said:**
> 
KVM can do whatever you like for storage. Partitions, logical volumes, any of 5+ different single-file storage methods or split the files into 2G sizes.  You realize that Proxmox is just a GUI over KVM and LXC, right?  Or is that Xen?

KVM/OpenVZ, but yeah. ;)

> I've never had anything called a "beefy GPU" in any of my machines and I transcode all day long - Core i5.  I think that machine has a $20 video card.  I recall being pissed when the 7600gs died and having to spend the money for any new video card at all.

Nice. I haven't don't much seriously transcoding except when I had my old machine. The new one is an i7 with a crappy Intel card, so maybe there is a huge difference. :)


> Charles!  I need to get you converted to NX. You don't know what you are missing.  ;) After you try it, you'll never go back.

We should probably work out a Spice How-to for the rest of the world too. Getting Spice to work should bring audio and video to remote desktops with encrypted tunnels built-in.  I think spice can only be performed under KVM virtual machines.  I've had it working for a few days, but it wasn't stable.  Spice clients exist for Windows and Linux ... don't know about OSX.  Spice server code appears to be available for Windows and Linux too.  Both **must** run under a special KVM process (kvm-spice) to work.

Hmmm.  That sounds interesting. I think I'll poke around a bit and see what I can find.

---

