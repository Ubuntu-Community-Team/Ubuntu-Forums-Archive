---
title: "ubuntu 16.04 does not detect pentium G620 as 64bit (VM)"
date: 2016-06-23
forum: Virtualisation
---

### Post by Martin_Mller-Lin on 2016-06-23
Hi,

I've put ubuntu-16.04-desktop-amd64 on a pen-drive using LiLi and tried to boot Ubuntu in virtual box (host: Windows 7 Ultimate 64bit).
Error message: "This kernel requires an x86-64 CPU, but only detected an i686 CPU. Unable to boot - please use a kernel appropriate for your CPU." 
But a Pentium G620 is a 64bit CPU, isn't it?
Looks like a bad start for a newbie (really, totally new to linux, but ready to learn...!) :-( ;-)

Greetings from south-west Germany
Martin

---

### Post by QDR06VV9 on 2016-06-23
To be able to run a 64-bit OS in Virtual Box we have to make sure the virtual machine's architecture is set to 64-bit too.
Screenshot Added
Also Thread Moved to Virtualisation better fit

---

### Post by QIII on 2016-06-23
I think you have one BIOS/UEFI setting to deal with and one misconception about VirtualBox.

First, you will need to be sure that you have virtualization enabled via your BIOS/UEFI menu.  For Intel hardware, that is called VT-x.  You'll have to see if your motherboard allows you to enable it.

Second is that in general you don't install a guest OS somewhere and then open it up with VirtualBox.  The guest OS should be installed *in* VirtualBox.

So, first let us know if you can set VT-x in your BIOS/UEFI menu and then we'll see about using VirtualBox.

---

### Post by Martin_Mller-Lin on 2016-06-23
ad 1) Ok, I checked UEFI settings: CPU-Settings/Intel Virtualization Technique was enabled but North Bridge/VT-d was disabled. I enabled it, but - same error.

ad 2) Maybe I didn't find the right words. I used [LiLi]("http://www.linuxliveusb.com/") to create a bootable usb stick using the image ubuntu-16.04-desktop-amd64. LiLi automatically brings virtual box to start Linux from the stick inside a Virtual Box (Windows as host). The settings shown in the screenshot are similar to mine (64bit).
This was my first try to start Ubuntu. If I will manage to get Ubuntu up and running on my machine and everything works fine *then* I'll create a virtual machine for my old Windows stuff and install Ubuntu as hostsystem instead. But this is not the toppic of this thread, I just mentioned it as background information ;-)

So back to the facts: Maybe next step should be to find out how to boot the stick  (not as VM but on hardware), although a virtual Ubuntu to play around would be nice to have...

Thank you for your support!

Update: I managed to boot from the stick on hardware (after finding out that not all USB-ports of my board support booting - the front-USB3 doesn't #-o): **Ubuntu runs on my machine** => it's only a problem with the virtualization. Maybe we can solve this...?

---

### Post by QIII on 2016-06-23
I'd suggest cutting to the chase and doing this as simply as possible.

Using this third-party Lili arrangement seems a bit too prone to adding unnecessary difficulty.

Why not install VirtualBox ([www.virtualbox.org](www.virtualbox.org)), download the Ubuntu.iso, start VirtualBox and install Ubuntu in a VM directly from the downloaded ISO?  There's no need to burn it to a disk or make a live USB out of it.  You can install from an ISO on your hard drive or SSD.  If you are simply testing and do not require the ability to move from machine to machine, it seems to me that it would be much easier to simply use VirtualBox as it was intended and in an unadulterated manner.

---

### Post by QDR06VV9 on 2016-06-23
> **QIII said:**
> I'd suggest cutting to the chase and doing this as simply as possible.

Using this third-party Lili arrangement seems a bit too prone to adding unnecessary difficulty.

Why not install VirtualBox ([www.virtualbox.org]("http://www.virtualbox.org")), download the Ubuntu.iso, start VirtualBox and install Ubuntu in a VM directly from the downloaded ISO?  There's no need to burn it to a disk or make a live USB out of it.  You can install from an ISO on your hard drive or SSD.  If you are simply testing and do not require the ability to move from machine to machine, it seems to me that it would be much easier to simply use VirtualBox as it was intended and in an unadulterated manner.
+1 I did not even know Lili was Windows Based...as I do not use windows.
So I missed the mark completely. Nice Catch QIII:KS

---

### Post by Martin_Mller-Lin on 2016-06-24
> **QIII said:**
> I'd suggest cutting to the chase [...] Why not install VirtualBox ([www.virtualbox.org]("http://www.virtualbox.org")), download the Ubuntu.iso, start VirtualBox and install Ubuntu in a VM directly from the downloaded ISO?

Agree! I wasn't aware of beeing on an unusual way (because LiLi brought the VM-feature and LiLi seemed to be a good approach for starting if still on Windows).

I'll try as suggested and I'll mark the thread as [SOLVED] if it works that way.

Thank you for helping me to learn!

---

### Post by MAFoElffen on 2016-06-24
Intel says in specs for that CPU: 
> 
Advanced Technologies:
Intel® Hyper-Threading Technology = No
Intel® Virtualization Technology (VT-x) = Yes
Intel® Virtualization Technology for Directed I/O (VT-d) = No

If the CPU does not contain a technology in the CPU, it is not possible to enable that missing capability in the North Bridge.

Next, agreed. Install  VirtualBox and see if it will support 64bit guests. With what you have set in the BIOS, it's own options/prefrences will give you hints and answers on that and what you can install (as arch) as guests

---

### Post by Martin_Mller-Lin on 2016-06-24
> **MAFoElffen said:**
> If the CPU does not contain a technology in the CPU, it is not possible to enable that missing capability in the North Bridge.

sounds logical :D. So I've learned now, that a BIOS may offer options that are nonsense with the CPU intalled. Good to know.

I got Ubuntu bit up and running in Virtual Box (beside an error that - as I've read elsewhere - can be ignored: "no valid rapi doamins found in package 0alized upgrade bios or use force_addr=0xaddr").

Solved so far - thank you for your support!

---

### Post by MAFoElffen on 2016-06-24
> **Martin_Mller-Lin said:**
> sounds logical :D. So I've learned now, that a [COLOR=#ff0000]BIOS may offer options that are nonsense with the CPU intalled.[/COLOR] Good to know.
Yes. Well, sort of. Usually a motherboard with it's BIOS allows for a CPU upgrade, so options may be valid for one CPU model, but not for another. Usually, but not always, sometimes if an option does not make sense for an installed CPU, the option will be grayed out.
> **Martin_Mller-Lin said:**
> I got Ubuntu bit up and running in Virtual Box (beside an error that - as I've read elsewhere - can be ignored: "no valid rapi doamins found in package 0alized upgrade bios or use force_addr=0xaddr").

[COLOR=#ff0000]Solved[/COLOR] so far - thank you for your support!
Then if resolved and answered, please mark the thread as solved Upper right of page, link "Thread Tools" > "Marked Thread as Solved". This will help other to find answers to their similar issues.

---

