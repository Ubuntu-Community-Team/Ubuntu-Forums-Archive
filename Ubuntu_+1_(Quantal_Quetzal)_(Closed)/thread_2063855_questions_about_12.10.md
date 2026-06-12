---
title: "questions about 12.10"
date: 2012-09-27
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by 123456789123456789123456 on 2012-09-27
I don't know if this is the correct place for this question or not, I can't ever seem to get an answer for this question.

I have an older system, it can only run unity 2d at the moment, it only has a 32 bit processor, and can not run any games that require high visual content, as it will move very slow.

I recently installed the 12.10 beta 1 on virtual box, giving the virtual machine 800mb ram, since I only have 2 gb total on the machine, and allowed 3d acceleration from virtual box.  The 12.10 started up, but when it got to unity, it performed so slow it was completely unusable, the only way to shut off the virtual machine was to do so through the turn off machine command in virtual box itself.

I also attempted to run the live cd, in live mode.  it was also unusable, however it did respond fast enough to allow me to restart the computer, to eject the dvd.

My question is, based on this information, will the actual installation be this slow, and I should in that case, just keep 12.04, until I can upgrade the computer, or perhaps even get a newer computer, or will it be operational, with only minor slow downs, as other sites seem to suggest.

---

### Post by kansasnoob on 2012-09-27
In Quantal they dropped Unity-2D, which used the Metacity window manager, in favor of using Compiz + llvmpipe.

Good info here:

[http://www.phoronix.com/scan.php?page=news_item&px=MTE2Mjc](http://www.phoronix.com/scan.php?page=news_item&px=MTE2Mjc)

> there will be systems that are simply too old to run Unity. In those cases it would be necessary to either stick with 12.04 LTS or run another desktop environment. We want this transition to go as smoothly as possible and are working on supporting as much hardware as we reasonably can. Hopefully we should have most of the wrinkles worked out by 12.10 release with just a little hangover for 13.04." Those wanting a lighter desktop to try should check out Xfce or LXDE.

---

### Post by effenberg0x0 on 2012-09-28
12.10 uses Unity 3D as a default and only option (no more Unity 2D). Unity 3D is a Compiz Plugin. Compiz is a Compositing Window Manager. This means that Compiz relies on OpenGL technology. OpenGL is processed by your GPU (GPUs have dedicated hardware to do that better and faster than CPUs). 

In order for that to work and be fast, you got to have a GPU and proper GPU drivers installed. 

Until recently, Unity 2D would load if you didn't had a GPU, if you had a very old GPU or if you didn't had proper VGA drivers installed, because OpenGL woudn't be able to run in this scenario. When Unity 2D was dropped, a new strategy was adopted: indirect rendering through llvmpipe. It was the only way to allow people with no GPU, very old GPUs or no proper VGA drivers to at least use Unity 3D, although with a reduced performance. 

Indirect rendering means that even a system with no GPU, a very old GPU or no proper VGA drivers - a system that can't run OpenGL to the required specs, will be able to boot and load the desktop, but all processing will be done by the CPU. In this scenario, a fast enough CPU will allow you to use the desktop OK. A ridiculously fast CPU will even give you a reasonably fast performance. A slower CPU, on the other hand, makes things slow (as the CPU is doing everything, including rendering OpenGL graphics). 

It's important to mention something about virtualization of 12.10: When you run a guest OS like Ubuntu 12.10 through VirtualBox (or any other virtualization technology) it does not interact with real hardware on the host. It interacts with virtual hardware. And the virtualization software (in this case VirtualBox) interacts with the kernel of the host OS. This is OK when there was no OpenGL in the game. But when the guest OS can't directly access the host real VGA card to process OpenGL, we have a problem. This is why it's hard to run games in Virtual Machines. Games need access to the real VGA card, not the virtual (slower) one. VirtualBox has some technology to try to improve this situation a little - it permits OpenGL, but with low performance (the guest OS still has no direct access to the host VGA card). There's work being done on Xen and KVM (PCI-E Passthrough) to remedy this problem, allowing guest OSs real access to the host VGA card. But it's not ready for consumers yet.   

If the 12.10 guest OS can't find the VirtualBox virtual GPU or is not using drivers for it, it will try to use indirect rendering (llvmpipe). There's a performance drop there. And if the host OS is also not using the GPU (using llvmpipe) there's yet another performance drop. A lot of indirect rendering, a lot of CPU usage, a increase in temperature, power usage, fans, cooler, memory usage. So what you see in VirtualBox right now can't really be considered a valid benchmark of Ubuntu 12.10 speed in your hardware.  

Virtualization aside, maybe we can still expect some improvements to Compiz and to Unity before release, some code refactoring and memory usage improvements, etc. But, at any rate, a system that is relying on indirect rendering and llvmpipe won't see a really drastic improvement on speed IMO.

Considering these factors, I would personally suggest you keep your currently working install in this machine, until you can get either a new VGA Card (even older models are generally enough) or a new PC. If you insist on the upgrade to 12.10 you will probably be using indirect rendering and hogging the CPU - which will result in bad performance.

Regards,
Effenberg

---

### Post by jbicha on 2012-09-28
And VirtualBox has not released guest drivers for xorg-server 1.13 which is used in Quantal, so you'll be stuck with llvmpipe.

---

### Post by grahammechanical on 2012-09-28
May I add something?

Over the last few weeks there have been really bad issues with the Live CD not loading to a usable desktop unless it was run with the nomodeset option. Also a new install would not load to a usable login screen unless the nomodeset option was set in the Grub menu.

That has also been true for 2 existing 12.10 installs that I have had. This has nothing to do with the hardware and everything to do with the Xserver and video drivers and that sort of stuff. So, I am not surprised that you have had problems.

So, I say: Do not expect 12.10 at its present level of development to be representative of 12.10 at its release date.

I have just seen that Beta 2 has been released. I intend to download it and test it out as a Live CD and as an install disk. You might find better results if you wait until 12.10 is officially released.

In view of the things that effenberg0x0 has written you would need to think about testing 12.10 in a dual boot set-up before making it the main OS on that computer.

Regards.

---

