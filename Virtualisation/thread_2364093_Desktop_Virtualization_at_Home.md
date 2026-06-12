---
title: "Desktop Virtualization at Home"
date: 2017-06-18
forum: Virtualisation
---

### Post by phosphide on 2017-06-18
Was hoping one of you can point me in the right direction.

I am currently dual-booting ubuntu and windows on both my laptop and desktop. The laptop can handle most of what I need to do so I don't really use the desktop anymore (especially windows). Here and there I would like to be able to use the desktop when I am away and also just use ubuntu on the laptop. Can also stick the desktop away and not take up desk space.

Instead of doing a simple RDP setup, I wondered if it would be possible to convert the desktop to more like a server and connect to virtual machines on it? That way I can start/stop VMs without having to turn the computer on and off and not hog resources on my laptop with a local VM. I can convert the current OS's to VMs but not sure how it would get served up exactly.

Hopefully I'm using the right words to describe what I would like to do. Have any of you tried this? Seems like I would need to install a hypervisor, import the VMs, and then connect to the OS via RDP? Also curious about security implications and such.

---

### Post by TheFu on 2017-06-18
Yes, you can accomplish what you are talking about.  I've been running my main "desktop" inside a KVM virtual machine for 6 yrs now. It can be accessed from anywhere in the world (almost), securely using the NX protocol. NX is 2-3x more efficient (and faster) than either RDP or VNC protocols AND it uses ssh for all authentication and tunneling. That makes it highly secure.  The normal techniques to secure ssh are sufficient to secure NX.   Of course, with Linux, you really don't need a full desktop 99% of the time, so straight ssh is more efficient and 99.99999% lighter.

So, there are many different ways to accomplish what you are asking about.  Most people start out using virtualbox, then graduate to KVM.  KVM is much faster and much more capable than Virtualbox, but with great power comes some added complexity.  In my experience, virtualbox wasn't stable like KVM.  I've never had any issues with stability that was cause by KVM either on the host or the client VMs.  I've had total system lockups with virtualbox, but many people here find it fits their needs.

There really aren't any 'conversion' tools for VMs. Just use your normal backup and restore methods. This won't work for Windows, but for all Linux OSes, it works perfectly provided any hardware specific drivers have been removed - things like GPU drivers and any RAID card drivers.  For networking, use the virtio devices.

All of these things are shown in hundreds of youtube videos, if you learn that way. 
[https://help.ubuntu.com/community/KVM/VirtManager](https://help.ubuntu.com/community/KVM/VirtManager) is the Ubuntu Community guide for KVM and virt-manager. [https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation) might be helpful too. I only use virt-manager to setup VMs, not for day to day access.  If you are on the same LAN, then you can use SPICE as the display type and have excellent performance. Over the internet, a full VPN is needed to ensure the SPICE connection is encrypted.  

x2go is the best of the remote desktop solutions for WAN/internet use, IMHO.  x2go doesn't care if it is running inside a VM or on real hardware. It just doesn't matter.

Of course, there are usually 10-50 different solutions for any issue with Unix. Hopefully, some others with different ideas will respond with their insights too.

BTW, there is an entire forum here just for virtualization. The posts in there might provide some more ideas for your consideration.

---

### Post by QIII on 2017-06-18
*Moved to **Virtualisation***.

---

### Post by phosphide on 2017-06-19
> **TheFu said:**
> Yes, you can accomplish what you are talking about.  I've been running my main "desktop" inside a KVM virtual machine for 6 yrs now. It can be accessed from anywhere in the world (almost), securely using the NX protocol. NX is 2-3x more efficient (and faster) than either RDP or VNC protocols AND it uses ssh for all authentication and tunneling. That makes it highly secure.  The normal techniques to secure ssh are sufficient to secure NX.   Of course, with Linux, you really don't need a full desktop 99% of the time, so straight ssh is more efficient and 99.99999% lighter.

So, there are many different ways to accomplish what you are asking about.  Most people start out using virtualbox, then graduate to KVM.  KVM is much faster and much more capable than Virtualbox, but with great power comes some added complexity.  In my experience, virtualbox wasn't stable like KVM.  I've never had any issues with stability that was cause by KVM either on the host or the client VMs.  I've had total system lockups with virtualbox, but many people here find it fits their needs.

There really aren't any 'conversion' tools for VMs. Just use your normal backup and restore methods. This won't work for Windows, but for all Linux OSes, it works perfectly provided any hardware specific drivers have been removed - things like GPU drivers and any RAID card drivers.  For networking, use the virtio devices.

All of these things are shown in hundreds of youtube videos, if you learn that way. 
[https://help.ubuntu.com/community/KVM/VirtManager](https://help.ubuntu.com/community/KVM/VirtManager) is the Ubuntu Community guide for KVM and virt-manager. [https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation) might be helpful too. I only use virt-manager to setup VMs, not for day to day access.  If you are on the same LAN, then you can use SPICE as the display type and have excellent performance. Over the internet, a full VPN is needed to ensure the SPICE connection is encrypted.  

x2go is the best of the remote desktop solutions for WAN/internet use, IMHO.  x2go doesn't care if it is running inside a VM or on real hardware. It just doesn't matter.

Of course, there are usually 10-50 different solutions for any issue with Unix. Hopefully, some others with different ideas will respond with their insights too.

BTW, there is an entire forum here just for virtualization. The posts in there might provide some more ideas for your consideration.

Thanks for the info! You make it seem easy haha. Ok, after watching some videos and reading some of the links out there, is this the approach I need to take:

1. Install Ubuntu server onto host machine (or a full version of Ubuntu if desired)
2. Install KVM on host and do network configurations as needed
3. Create VM's on host machine
4. Install virt-manager (or equivalent) onto my laptop and connect to the host
5. Start/stop machines as needed
6. Have fun

---

### Post by TheFu on 2017-06-19
You need to install and configure ssh on all the systems - physical and virtual. Virt-manager works through ssh for remote connections. If you don't set that up ... well, just set it up.

Don't forget bridge-utils.  I always manually create a bridge, never use the automatic one that libvirt makes. Early on, there were some bad issues with the non-manual bridges. Don't know if those are solved or not. Don't take the time to test when I have a solution that "just works."

And in many instructions, they have virt-install which just isn't necessary unless you want to automate VM builds. For a point-n-click user, you can ignore it completely.  In 2010, it was helpful, but since then it is completely unneeded.

---

### Post by phosphide on 2017-06-19
For linux machines I understand ssh, but what if I needed to run Windows?

I planned to do the bridge-utils based off most of the instructions, so I should be good there.

Noted about virt-install. I don't anticipate creating a lot of machines.

---

### Post by TheFu on 2017-06-20
> **phosphide said:**
> For linux machines I understand ssh, but what if I needed to run Windows?

The solution depends on your needs.  I run 7MC in a VM to record OTA TV, but only use it for productivity-type applications; finances, stocks, and taxes. No multimedia, no high-graphics and I always use a Linux "jump box" to connect to it from the LAN because RDP isn't secure over the internet. Mine is Win-Ultimate (free from MS a long time ago). This doesn't work for Win-Home installs.

If you desire gaming or multimedia playback, someone else will have to help. That is much harder, extremely HW specific and doesn't work remotely to my knowledge.

---

### Post by lammert-nijhof on 2017-06-24
I run all my OSes as a Virtual Machine on both desktop and laptop. On both systems I use a slightly trimmed version (400MB) of Ubuntu 16.04 as Virtualbox Host. I only use the host for Virtualbox and watching YouTube Videos. Before that I tried Peppermint and the Ubuntu Server as host, but I stopped it, because all time-based processes in the guests would be starved of cpu time occasionally. Playing music in the Guest sounded terrible. I do it now for 3 months and I'm happy. Virtualbox is very reliable nowadays and I use 5.1.18. I always installed it using the deb file, keeping full control on the need for an upgrade. After buying my laptop, my systems were up and running again, in the time I needed to copy the VMs to the laptop. No tuning, no programs to be installed everything directly ready to be used and everything on exactly the same spot.

The guests I use are: Ubuntu 16.04 (for all money related issues) and for fun: Ubuntu 17.10 pre-alpha, Linux Mint 18.2, Peppermint 8, Ubuntu Mate 17.04, Deepin and the activated  Windows 7, Windows Vista and Windows XP. I often use XP to play music while restarting and playing with e.g. Deepin. I have duplicated the VMs, because if I'm on holiday in Belgium, I want all facilities and fun from home. It also provides a back-up in case of e.g. broken disks. My hosts are open for e.g. Samba access, but my VMs use Shared Folders and are completely closed for external incoming access.

The SSD makes the system really fast also for the VMs. The Host loads in 15 seconds and Windows XP/7 in around 30 seconds, even old, awful Windows Vista loads within a minute. Another advantage is that on restarts, the system is partly booted from the host page cache, restarts take close to 20 seconds for e.g. Windows.

---

