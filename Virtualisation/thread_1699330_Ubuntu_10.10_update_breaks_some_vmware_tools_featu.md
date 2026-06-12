---
title: "Ubuntu 10.10 update breaks some vmware tools features"
date: 2011-03-03
forum: Virtualisation
---

### Post by Zoea on 2011-03-03
Has anyone else run into this? I have a VMWare image of a 10.10 install (upgraded from 10.4) which is running on a Windows 7 SP1 host (recent sp1 installed). The virtual machine was working perfectly until I installed the software updates yesterday. These included a new kernel image. 

Afterwards the cross-vm copy/paste wasnt working so I reinstalled VMWare tools. This is where the problem started. Previously when I resized the vmware window the x screensize would be changed to match the window size automatically. Now the screen is stuck at a fixed size, 1280 * 720 I think. This is annoying since I have to scroll the screen to use it all on my small res laptop display.

I am not sure if any other vmware tools features are not working.

Has anyone else come across this problem before and can suggest a fix? Or perhaps the update has caused the same problem for you? I can post more details if necessary (new kernel version etc). 

BTW, The additional drivers tool shows I am running :
-VMware Virtual Ethernet Driver
-VMware Virtual Machine Communication Interface.
i.e. i'm not running a special vmware display driver (is there such a thing?)

---

### Post by Zoea on 2011-03-08
Bump, this is still annoying me.
I checked and vmware-user (or at least vmware-user-loa???) is running and it is the tool meant to do this function. Do I need to wait for a new version of vmware tools?

Any luck using the open source vm tools to do this instead? I only need copy/paste and resize nothing else.

---

### Post by politikdurden on 2011-03-19
I am running VirtualBox on an XP host and running Ubuntu 10.10 Maverick as a guest OS in a virtual machine. I had the same issue; I couldn't run the Ubuntu 10.10 virtual machine in full screen after I ran Ubuntu updates. I resolved this by re-installing VirtualBox's "Guest Additions"; Virtual Box's software that runs on the guest OS. Maybe vmware has some equivalent that you can re-install ?

---

### Post by Zoea on 2011-03-28
Hi

Thanks for the reply but I have already tried reinstalling the VMWare equivalent, vmware-tools. This didn't fix it.

I might just use another VM software. Can you convert images between VMs yet?

That would be cool if you could !

ps VMWare specific help still welcome

---

### Post by Zoea on 2011-03-28
I switched from VMWare Player to VirtualBox (by Sun / Oracle, OSS) and the resize feature is working again with the Virtual Box Additions software running in my ubuntu guest.

For anyone who needs a solution and is prepared to try this major change:

- Uninstall VMWare tools in vmware guest (vmware-uninstall-tools.pl)
- Shutdown the guest (not suspend!) and close VMWare
- Install VirtualBox
- Create a new Virtual Machine and point it to your existing VMDK file. I have the hard drive split across many files but I pointed to the main VMDK file (without the -s0xx suffix at all) and it picked up all the files as one drive.
- Change any settings you need to change with the settings window. I went with 512MB, old style timing and one processor to save idle cycles.
- Install Guest Additions in your guest OS. See the docs for how (you can just mount the image and let it autorun though).
- Run the new VM with Virtualbox. Your Guest OS should run. 

First impressions of virtualbox are good. I was using 5% average cpu doing nothing with vmware hopefully that should be fixed too.

Hope this helps!

---

### Post by crazydrve on 2011-11-23
I also have the same problem with vmware and ubuntu.

config:
windows 7 x64 host
vmware workstation 7.15
was running ubuntu 10.04 with workstation 7.12? went thru workstation upgrades, then also did the ubuntu upgrade to 10.10. 

just noticed the monitor issue. 

tried removing drivers, vmtools, etc with no luck. 

I have not tried fresh intstall with vm 7.15 but I did a fresh install with new vmware workstation 8 and ubuntu 10.04 then upgrades to 10.10 and it works fine...

So must be something with combo upgrading vmware and ubuntu? 


Cant find how to remove video driver ( I am new to linux when it comes to troubleshooting)

Anyone have any ideas except using virtual box...

---

