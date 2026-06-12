---
title: "VMware Player - system requirements for host system and guest OS"
date: 2014-08-14
forum: Virtualisation
---

### Post by steve7777777 on 2014-08-14
I have a system with:
GIGABYTE GA-880GA-UD3H 
AMD Phenom II X4 955
8GB DDR 3
VMWARE Player
On-board video - no separate GPU
Ubuntu 10.04 soon to be reinstalled to 14.04

I'd like to not touch the base system for daily use and use several VMWARE Player guest operating systems (Ubuntu 14.04 and maybe Windows 8) - only two guest OS simultaneously at most.

I have the VMware tools in the guest operating system installed.
For the guest operating systems (also Ubuntu) I have 2GB RAM and 2 CPU allocated for one and 1 CPU allocated for the other - so the base system always has at least 1 CPU.
Virtualization is enabled in the bios and "automatic" set for for the guest OS.

**Problem - video playback (VLC) is poor.**

Would adding a dedicated GPU solve the problem? Do I need a better system - such as an i5 or i7 non "K" based CPU (for virtualization)?

Any other suggestions or guides appreciated. Thanks!

---

### Post by TheFu on 2014-08-14
Video playback in any guest OS is a hack. Guests do not see the real video hardware - just the emulated video card provided by Player. What specific onboard video chips are provided?   Any current-generation onboard chips handle video fine and a separate GPU won't help.  Any $20 nvidia card w/ 3D accel can do 1080p video just fine.
[B]
lshw -c video[/B] output will help us.

If the videos in question are flash or web videos - those use very little GPU and do most of the decoding in the CPU.

---

### Post by steve7777777 on 2014-08-14
> **TheFu said:**
> Video playback in any guest OS is a hack. Guests do not see the real video hardware - just the emulated video card provided by Player. What specific onboard video chips are provided?   Any current-generation onboard chips handle video fine and a separate GPU won't help.  Any $20 nvidia card w/ 3D accel can do 1080p video just fine.
[B]
lshw -c video[/B] output will help us.

If the videos in question are flash or web videos - those use very little GPU and do most of the decoding in the CPU.

This is the output:
```
*-display               
       description: VGA compatible controller
       product: SVGA II Adapter
       vendor: VMware
       physical id: f
       bus info: pci@0000:00:0f.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=vmwgfx latency=64
       resources: irq:16 ioport:1070(size=16) memory:e8000000-efffffff memory:fe000000-fe7fffff memory:c0000000-c0007fff

```---
[FONT=Arial][COLOR=#000000]The built in GPU is "Integrated ATI Radeon HD 4200" which is roughly (almost) [/COLOR][/FONT][FONT=Arial][COLOR=#000000]equivalent[/COLOR][/FONT][FONT=Arial][COLOR=#000000] nvidia gt620.  So I can see how a separate GPU won't help.[/COLOR][/FONT]

---

### Post by steve7777777 on 2014-08-14
Also, the player is VLC. The video isn't streaming - I've been testing MKV and mp4 files - low resolution. The files are local, but the connection to the shared folder isn't slow.
-Ubuntu Restricted-Extras is installed on the guest OS
-I confirmed VMware Tools is installed properly

Update - I found this - Virtual Box discussion but similar concepts and constraints:
[https://forums.virtualbox.org/viewtopic.php?f=6&t=33015](https://forums.virtualbox.org/viewtopic.php?f=6&t=33015)
"*Generally speaking, high end multimedia performance is always on the bleeding edge of what is possible in a virtual machine.**To have even a remote chance of getting this to work you would need a very high performance Host PC with a fast CPU that includes hardware virtualization support.*"

Thoughts on this? Also using a large, expensive, energy demanding GPU isn't an option.

---

### Post by TheFu on 2014-08-17
I think that statement is old. Hardware made in the last 4 yrs shouldn't have any issues with playback of 600p or less videos, even in a VM.  Prior to that, it was true.  I don't recognize your GPU, but know that I have old nVidia cards here - 7600GS is the oldest and it handles video playback - non-HD - in a VM fine.

The CPU is more than enough to handle this stuff. That isn't an issue.

Still - hoping for perfect playback inside a VM is often wishful thinking, especially on older hardware. Depending on the total workload running on the system and I/O capabilities inside the VM, it may work without issue or not. Hard to say.  If you optimize the IO for the VM, that could help. The default settings for most VMs are less-than-optimal. Make the VM have the lowest overhead will help.

If the hostOS is doing nothing but supporting the VM, it may work completely fine.

VLC works cross platform - perhaps playback on the real hardware can be used? It should solve this issue.

---

### Post by steve7777777 on 2014-08-19
> **TheFu said:**
> **I think that statement is old. Hardware made in the last 4 yrs shouldn't have any issues with playback of 600p or less videos, even in a VM**.  Prior to that, it was true.  I don't recognize your GPU, but know that I have old nVidia cards here - 7600GS is the oldest and it handles video playback - non-HD - in a VM fine.

The CPU is more than enough to handle this stuff. That isn't an issue.

Still - hoping for perfect playback inside a VM is often wishful thinking, especially on older hardware. Depending on the total workload running on the system and I/O capabilities inside the VM, it may work without issue or not. Hard to say.  If you optimize the IO for the VM, that could help. The default settings for most VMs are less-than-optimal. Make the VM have the lowest overhead will help.

If the hostOS is doing nothing but supporting the VM, it may work completely fine.

VLC works cross platform - perhaps playback on the real hardware can be used? It should solve this issue.

I disagree. I tested an  i5 3570k (the "K" does not support vt-d). Video playback in the Ubuntu 14.04 guest and 12.04 host is choppy at best - both h264 and MP4 video. I have a friend with a non-k i7 and it plays h264 and MP4 video just fine in guest Debian 7, Debian 7 host. The 3570k was much better than the AMD Phenom II x4 955, but the 3570k was much better.

By the way the 3570k is a dual boot. Windows 8 with hyper v - host and Ubuntu 12.04 guest plays all video I can throw at it - but there's no sound since hyper V results in "dummy sound" - which is a topic for a new thread perhaps on a Windows forum :p.

---

### Post by TheFu on 2014-08-19
I've had video playback work OK on systems without VT-d. The system was a 1st-gen Core i5 mobile processor  - 50% slower than the AMD CPU mentioned above ... so nowhere near the performance of any "k" models.  Prior to that, I vaguely recall trying it on a C2D, but don't remember being happy with video.

These days, I use KVM for all production-level virtualization, but that doesn't usually include viewing videos.

VT-d should only matter if GPU passthru has been setup.  VT-x matters for pure virtualization. Using VT-d GPU-passthru is a non-trivial setup with very specific hardware and kernel settings. Does "Player" even support GPU passthru? 

We used virtualbox on a Win7 host with a Mint guest - to get Amazon Prime videos working in 2013. It was just a test for a few days. Worked fine.

"Acceptable playback" is subjective, so there isn't a good way to compare results.

---

