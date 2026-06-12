---
title: "Ubuntu in virtual box bad performance (graphics)"
date: 2021-06-21
forum: Virtualisation
---

### Post by sciro16v on 2021-06-21
Hello everyone,
as windows-user, I tried Linux in the last 20 years serveral times. The result was always the same, I didn't get simple things managed. Now I have to use Linux on my job and tried to run it on my private notebook also. I installed Oracle virtual box and some linux distributions:
- raspberry OS
- Lubuntu focal fosa
- Xbuntu focal fosa

In every case I have no graphic performance. I'm not able to watch a video. It doesn't matter if it's from my mobile self-recorded or from youtube. 

My idea was, I have a problem with virtual box. So I installed Budgie (focal fosa) on an USB-stick and booted from there. Same Problem, and the all-around performance is maybe also a little bit lower.

I was running a website called speed-battle, I don't know if the results are accurate. It shows a not very good performance of my notebook in windows-mode. With vm+linux it's round about 55 %. 

My job-notebook is more high-priced. I ran the same test. Windows performance was good, vm+linux was 20 %. As slow as my private-notebook with linux. And also with this notebook I am not able to play videos. 

As setting I used: VMSVGA, 128 MB graphic memory + 3D-acceleration (I don't know, if that's the correct word in english)

What am I doing wrong?
sincerely yours

---

### Post by slickymaster on 2021-06-21
Thread moved to **Virtualisation** for a better fit

---

### Post by dddman on 2021-06-21
IMO the guest requires a minimum of 2 core and 2G ram.  I run Ubuntu in Virtualbox and video performance is ok.  Windows performance is a little bit better and I tend to use both.  Also do not use 3d acceleration until you get Ubuntu working right.  Could you post a link to this speed test, I want to try it.

---

### Post by sciro16v on 2021-06-21
@slickymaster Thanks for moving and sorry for posting in the wrong forum.

@dddman I'm running it with 2 (of 4 cores) and with 4 GB (of 8 GB) RAM. With or without 3d is no different behavior (for my eyes). 

I hope it is allowed to post the link here. Is there maybe another performance test often used, here in the forum?

[http://www.speed-battle.com](http://www.speed-battle.com)

At the topic "Render" I have more than 75 with windows (not good, but it's a Acer Swift 1). With vm+xbuntu I reach 45. And the videos looks like this. Sometimes I have a time mismatch between picture and sound.

---

### Post by dddman on 2021-06-22
Well Ubuntu scored above average on all three and Windows was still higher.  My "render" is 70 out of 82.
<snip>

---

### Post by TheFu on 2021-06-22
Graphics performance is not the same as system performance.  If you would like a snappier experience, 
a) don't use the Gnome3 Desktop; Choose almost any other DE version - xubuntu, lubuntu, Ubuntu-Mate and the performance should be much better. I use fvwm.
b) Put VMs on an SSD, not a spinning HDD. If a HDD must be used, then pre-allocated all the storage, don't let it resize dynamically. In the storage section, there is a sparse file option. Don't use that, unless the physical storage is SSD.
c) be certain to load the correct guest additions. That's a vbox thing.
d) choose virtio for the NIC and Storage controller. No need to emulate hardware or have bandwidth limitations due to that virtual, emulated, hardware.
e) choose the Intel ICxx motherboard, not the PIIX version.  I'm not looking right now, so the ICxx might not be correct.

New Ubuntu users should only run LTS releases unless they have a very good reason that something newer is required.  The current LTS is 20.04. Use that - but avoid the Gnome3 DE (which is the default, bloated, wants-direct-GPU-access, DE).  All the others should work find under a VM, though I do recall having terrible performance with Ubuntu-Mate after a fresh install using ZFS.  Quickly did a reinstall, this time using LVM and the performance was better, but still not great. That was after a fresh install into a VM, but before I had the SPICE libraries loaded.

Perhaps I missed it, but did you say what the hostOS was running?  Is it Linux or Windows?  That changes a few things in the settings. If the hostOS is Linux, I'll go away.  I never had luck with vbox under Linux, but many people use it daily, all the time.  I'm a KVM/libvirt VM guy and have been over a decade after leaving Xen, VMware tools and VirtualBox.  KVM is what all the big VPS companies use unless they have to eat their own dogfood (microsoft, VMware, Xen).  Oracle's cloud uses KVM, however. So does Amazon and almost all the VPS hosting companies in the world.

I'd never heard of that speed-battle. A few results:
On my VMhost, 
```
$ inxi -CGS
System:    Host: hadar Kernel: 5.4.0-74-generic x86_64 bits: 64
           Desktop: **FVWM** 2.6.7 Distro: Ubuntu **18.04.5 LTS**
CPU:       6 core AMD Ryzen 5 2600 Six-Core (-MT-MCP-) cache: 3072 KB
           clock speeds: max: 3500 MHz 1: 1374 MHz 2: 1374 MHz 3: 1374 MHz 4: 1359 MHz 5: 1364 MHz 6: 1498 MHz 7: 1374 MHz 8: 1374 MHz 9: 1375 MHz 10: 1369 MHz 11: 1349 MHz 12: 1370 MHz
Graphics:  Card: NVIDIA GP108 [GeForce GT 1030]
           Display Server: x11 (X.Org 1.20.8 ) **driver: nvidia**
           Resolution: 1920x1200@59.95hz
           OpenGL: renderer: GeForce GT 1030/PCIe/SSE2
           version: 4.6.0 NVIDIA 460.80
```
I got an overall score of 411.09  w/ Render near 99. I should point out that my browser was running inside a constrained "firejail" to protect against bad internet sites. 

Inside a VM running on that hardware,  
```
$ inxi -CGS
System:    Host: regulus Kernel: 5.4.0-74-generic x86_64 bits: 64 Desktop: FVWM2 2.6.8 
           Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
CPU:       Topology: 2x Single Core (4-Die) model: AMD EPYC (with IBPB) bits: 64 type: MCM SMP 
           L2 cache: 1024 KiB 
           Speed: 3493 MHz min/max: N/A Core speeds (MHz): 1: 3493 2: 3493 
Graphics:  Device-1: Red Hat QXL paravirtual graphic card driver: qxl v: kernel 
           Display: x11 server: X.Org 1.20.9 driver: none unloaded: fbdev,modesetting,vesa 
           resolution: 1680x1050~60Hz 
           OpenGL: renderer: llvmpipe (LLVM 11.0.0 256 bits) v: 4.5 Mesa 20.2.6  
```
got an overall score of 931.64  w/ Render near 57.  Watching videos in the VM is possible, but why would anyone do that?  That isn't what using VMs is about.

---

### Post by dddman on 2021-06-22
> **TheFu said:**
> got an overall score of 931.64  w/ Render near 57.  Watching videos in the VM is possible, but why would anyone do that?  That isn't what using VMs is about.
When I go full screen, Windows no longer exist and I expect Ubuntu to be a full service OS.  It's not about watching a movie, it's things like the news, reddit, imgur...  I am using Ubuntu about [s]90%[/s] 95% of the time these days.  IMO a VM is sooo much easier to maintain, I doubt that I will ever dual boot again on this machine.

@sciro16v
I also run the vmSVGA driver, xorg should run on any of the three virtualbox drivers, I would try the others.  Two machines doing the same thing and it looks like only vbox is common to both.  If it was me, I give VMware a try.

---

### Post by deadflowr on 2021-06-22
> Watching videos in the VM is possible, but why would anyone do that? 
Indeed it should run fine.
As far as why anyone would, my own experience in the past was because of non-existent drm in linux.
When flash was the go to video plugin they did offer drm version which was only available in Windows/Mac(?, I think) and ChromeOS.
A handful of streaming sites used it so if on linux it was a difficult thing to overcome. 
Your options were to either painstakingly extract the flashplugin from a ChromeOS version or use windows. (Or Mac I guess.)
Since dual-booting just for the sake of watching a video didn't make sense, virtualizing windows was a quick and easy solution.

Thankfully the world has dropped flash and current html5 has easier to deal drm support with widevine handling a large swath of streamers,
Since widevine is supported on linux across an array of browsers, it's just a simple click on a checkbox to enable if required.

Edit: I forgot about wine as an option, but mainly because running windows-based browsers in wine as an option is such a hit or miss option.

---

### Post by dddman on 2021-06-23
I increased video ram to 256M:

"C:\Program Files\Oracle\VirtualBox\VBoxManage.exe" modifyvm "[COLOR=#008000]guest session name[/COLOR]" --vram 256

Render did not change.  I guess a test of time is required.

---

