---
title: "Windows 10 runs but will not display in VM"
date: 2016-07-12
forum: Virtualisation
---

### Post by cjsmall on 2016-07-12
Xubuntu: 16.04
Qemu-KVM: 1:2.5
System: [FONT=arial] Dual Xeon E5-2630 v2 CPUs, 32GB RAM, Nvidia K-4000 GPU[/FONT]

Well over a year ago I created a VM (2 CPU cores, 2048 MB RAM, 30 GB disk) and installed Windows 8.1.  I cloned the VM and immediately upgraded to Windows 10.  Both VM images have run successfully since then, although the Win-10 is the only one being actively used.  I upgraded Xubuntu from 15.10 to 16.04 a couple of months ago and everything appeared to be OK.  I'm pretty sure that I used Win-10 successfully a few times after the upgrade.  Since then there have been a few software updates, to 16.10 but I see nothing in the logs that would obviously be related to the following problem.

About a week ago I started up the Win-10 VM.  It boots, shows the early Windows logo and then the screen goes gray and the spinning circle icon is displayed.  This spinning icon never quits and the Windows desktop never displays regardless of how much time passes.  Usually the gray screen continues to be displayed, but a couple of times, after a few hours passed, the Windows login screen with the user picture might appear, but still the icon spins and there is no access to the desktop ever.  Despite this, the OS actually has booted fairly quickly and I can access the Windows filesystem remotely using the Linux file manager.  (Nemo in my case.)  I can shutdown and reboot the VM as often as I like and Windows appears to be running behind the scene, but it will not display the desktop.  While this is happening, the VM console shows the VM CPU pegged at 100% and this continues indefinitely.

I can start the Win-8 VM and it boots and operates just fine.  I thought I might have a corrupted disk image or that Microsoft had updated something that caused a problem.  I had a Win-10 backup image file from January, so I copied it in place and rebooted, but I get the identical behavior.

I am using an Nvidia K-4000 GPU and read that some people had display problems with the Nvidia-361.45.18 driver; problems which were fixed by installing the nvidia-364.19 driver.  I installed and am now running this, hoping for some improvement, but no luck.

So I'm in need of some suggestions as to what might be wrong.  Why did a working Win-10 stop working, and why does Win-10 run, but fails to display graphics, while Win-8 works fine?   Thanks for any suggestions.

---

### Post by KillerKelvUK on 2016-07-12
Can you get into safe mode? would suggest removing the drivers completely, reboot and see if that allows access to the desktop again, reinstall latest nvidia drivers from their.

Also, (throw away suggestion) I had issues with my windows vm failing to get to the desktop properly (slightly different symptoms) because of a usb passthrough issue, my only recovery was to remove the usb devices, reboot into safe mode and then reboot normally without the usb devices passed through and then attached them post boot.  Any parallels with your setup?

---

### Post by MAFoElffen on 2016-07-13
In KVM? In the XML of your VM Guest, what is your Video type and your graphics model type set to?

.Also, "what" are you using to display your VM Guest session as a VM Console? Virt Viewer?

As KillerKelvUK said... You won't much of have a chance at the initial boot of a Win 8.1 VM, but once running, if you send it a Hard machine reset from the Guest Console menu to cycle it, then immediately start pressing the <F5> key... to try to get it into safe mode. You might have a better chance.

Just a thought.

---

### Post by cjsmall on 2016-07-21
Apologies for the week's delay in responding to these suggestions, but Ubuntu Forums has been down since shortly after I posted my original query and this was the first time I have been able to access this thread.

First, let me follow up with another piece of new information.  About a week ago i restarted the Windows-10 VM and it responded as described above with the gray screen and spinning icon, followed by the login screen with the spinning icon and a pegged CPU.  This time I left it running for three days and was surprised to discover that it had actually resolved and was displaying the normal Windows-10 desktop with the CPU quiet.  The Windows/VM system worked fine while I left it running.  After a day I had to know whether the problem was resolved, so I shut down the machine and restarted it.  Unfortunately, the same problems developed.  I have since had one situation where the machine appeared to hang (the spinning icon froze on the gray screen) and a number of other attempts have moved onto the login screen where the icon continues to spin for days.  I haven't had it successfully complete and get to the desktop again.

I now am thinking that this is NOT related to the graphics driver.  It displayed the desktop just fine when it got past whatever is blocking it, and it does properly display the login screen with the user picture and 4-pane windows logo in the dark blue background

 				 				 					 						 	[[COLOR=#000000]KillerKelvUK[/COLOR]]("https://ubuntuforums.org/member.php?u=1728893") asked if I could boot into safe mode, but I have found no way to do that.  From what I've read, Microsoft has changed something in Win-10 that makes it just about impossible to access the BIOS during boot.  [[COLOR=#C61919]**MAFoElffen**[/COLOR]]("https://ubuntuforums.org/member.php?u=1044547"), you suggest doing a hard reset from the console.  I'm not sure how to do this.  Could you be more specific as to what you mean abd what I could then do at that point to diagnose the problem.

I'm using virt-manager to manage these VM sessions.  From the VM hardware details screen, here are a few of the most relevant settings:

Hypervisor:  KVM
Architecture: x86_64
Emulator:     /usr/binkvm-spice
Firmware:    BIOS
Chipset:       i440FX

CPUs:          (2) SandyBridge
Memory:      2048 MiB
NIC:            Bridge br0: Host device eth1  Device model rtl8139
Display:       Spice server - Localhost only - Port 5900 - TLS port Auto
USB Ctrlr:    USB 3

The five USB Redirectors are type SpiceVMC, but none are assigned.  I have attempted to attach them to USB devices in the past, but this has not worked (that's another problem) so they are not in play at the moment.




I'm still struggling with this, so any additional suggestions are appreciated.  There seems to be some hardware issue involved, but if it's not graphics, then any ideas as to what else it might be and any workarounds I could try?

---

### Post by cjsmall on 2016-07-29
Just to close out this discussion, I was never able to get the Windows 10 VM working properly, despite much investigation.  Therefore, I created a new clone of the original Windows 8.1 system which was still running and displaying properly, performed another update to Windows 10, and then went about the long drawn out task of reinstalling the missing software and reconfiguring everything!  This new machine is running properly.

For those who stumble upon this thread, I will mention that I am on a system with[FONT=arial] dual Xeon E5-2630 v2[/FONT] CPUs.  In order to successfully upgrade to Windows 10 it was necessary to change the VM CPU type from SandyBridge to core2duo, perform the upgrade, and then change the CPU back to SandyBridge.  Hopefully that will save others from some problems.

---

