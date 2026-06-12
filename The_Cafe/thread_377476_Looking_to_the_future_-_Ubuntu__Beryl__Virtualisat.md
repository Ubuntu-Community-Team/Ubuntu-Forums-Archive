---
title: "Looking to the future - Ubuntu / Beryl / Virtualisation / Windows"
date: 2007-03-06
forum: The Cafe
---

### Post by myxiplx on 2007-03-06
Hey folks,

I'm seeing some very cool stuff coming out on Linux now.  I'm a longterm windows admin, who's been watching Linux from the sidelines for years.  Well I have to say, some of the new stuff in Ubuntu amazes me.  Installing and patching apps is stupidly easy, Beryl / Compiz look stunning, and with OpenOffice it's good enough for nearly everyone.

But despite all that, I still think that one of the biggest hurdles for Linux has still not been addressed - the sheer volume of windows software out there.  The average user doesn't understand the difference between Windows & Linux (more than you would believe don't even understand the difference between Windows & Office).  They just expect their programs to work, and that causes a problem when it comes to Linux adoption.

This is especially true for games.  The only thing stopping me migrating to Linux at home is that I play everquest.  Ok, I could probably get it going in Wine or something, but in all honesty I don't want to commit the time or effort (and I'm a geek!).  Many home users are in this boat, and the average parent is never going to run Linux if it means their kids end up constantly complaining they can't play their games.

So, what I'm thinking is this:  I know there's some virtualisation stuff going into the new Linux kernel.  Does anyone know if that means you could soon run a full copy of XP inside Linux?

Now this may be wishful thinking, but if that's possible, what's to stop the next generation of Linux installers taking your current installation of XP and sandboxing it inside a virtual machine?  I'd love to see Linux install on a windows box by just taking your existing windows install, and giving it back to you as a shortcut on your Linux desktop :-D

You'd wow anyone with that kind of functionality, and it'd make a very smooth transition to linux for a lot of folk - they can keep running their windows apps anytime they want, but at the same time all that Linux eye candy and ease of use is going to be there, tempting them over.  Especially if all their windows files are still available from Linux.

There are also a lot of fringe benefits.  Ghosting or backing up the windows box now becomes an easy task.  Remote support of a dead windows install also becomes a possibility, right down to remotely re-installing from scratch.  Combine that with an Anti-virus program that can run from Linux to clean your windows box and all of a sudden you've got a far more stable base for a home computer.  Even if windows does get infected, update your AV software in Linux and it's a simple matter to clean it.  

That point is so important I think it bears repeating:  Windows running inside linux is more stable, more reliable, and easier to support than windows running alone.

Hell, now I've written this I think you'd want a corporate version of this too.  For the corporate version have a bare bones linux, secured and centrally managed, with just the minimum features available to the users.  if you could do that I'd migrate our entire company to Linux right now.  The ability to remotely support a windows machine from boot would be worth it's weight in gold!

please discuss ;-)

Myxiplx

---

### Post by TheSqueak on 2007-03-06
VMWare works wonderfully well :)

I'm not sure whether or not you can set it to read a current installation of Windows, as opposed to setting aside a chunk of disk space and installing a fresh copy, but i'd be interested to know if that's possible.

---

### Post by Tichondrius on 2007-03-06
I guess OP doesn't realize that graphics performace sux in aVM because the VM can only access hardware using virtual devices and not directly. For example, a graphics driver running inside the VM accesses a virtual graphics card that is exposed by the VM. Usually the graphics virtual devices exposed by the VM are simple framebuffer devices, and not accelerated graphics (although that might be avialbe in the future, but it would still incur a large performance hit). A much better option for running windows games under linux is by using Windows API emulators like wine and cedega.

---

### Post by myxiplx on 2007-03-06
I thought the whole point of the new work in virtualisation was to allow direct hardware access?  I thought they'd just added a load of features to the CPU's recently allowing direct hardware access?  I guess if not it's not going to work yet, but it's still possible in the future.

Squeak:  Yes, you can image a current machine.  We've even moved a couple of Win2k servers to VMware straight from our ghost backups.  Provided you have drivers for the virtual hardware already installed it's a simple case of ghosting the original & loading that in the virtual machine.

I know I can do something like this with VMware now, but I don't really want to be messing around configuring it.  What I'm wondering is whether it's feasible in the long term to do something like this out of the box.

---

### Post by macogw on 2007-03-06
i dont think they got all of the virtualization stuff implemented.  i think they just got it to "theoretically, if someone wanted to write a program that could do it, it could hook into this part of the kernel"

myxiplx, VirtualBox is a Free (speech/beer) virtual machine that runs faster than VMWare, at speeds similar to Qemu, but with an open source driver instead of Qemu's closed source one and with no mouse lag.  Setting it up is dead simple.

---

### Post by Tichondrius on 2007-03-07
> **myxiplx said:**
> I thought the whole point of the new work in virtualisation was to allow direct hardware access?  I thought they'd just added a load of features to the CPU's recently allowing direct hardware access?  I guess if not it's not going to work yet, but it's still possible in the future.

Squeak:  Yes, you can image a current machine.  We've even moved a couple of Win2k servers to VMware straight from our ghost backups.  Provided you have drivers for the virtual hardware already installed it's a simple case of ghosting the original & loading that in the virtual machine.

I know I can do something like this with VMware now, but I don't really want to be messing around configuring it.  What I'm wondering is whether it's feasible in the long term to do something like this out of the box.

No, you are very very wrong. Virtualization techonlogy in the CPU has NOTHING to do with allowing a VM direct access to the hardware. Surely, you understand that a VM usually runs in a window on the desktop of the host OS, and that the filesystem of the guest OS, which is running in the VM, is simply a single file in the filesystem of the host OS. So, even though the guest OS thinks it's running on a real machine, with a real screen and a real hard drive, it's actually just accessing virtual devices that are made available to it by the VM software. Now, regarding the screen - the guest OS can run in full-screen mode, in which case it would be possible for the graphics virtual device driver to allow the guest OS to directly access the video card, including accelerated 3D features. But that's not implemented yet in any of the VMs available.

Regarding CPU virtualization technology, it's simply a feature which provides special instructions to allow control of process running in privileged and user mode. That is required in order to allow the guest OS to run in a "virtual" privileged mode so it can perform its critical functions, yet still be under the control of the host OS.

---

### Post by Iarwain ben-adar on 2007-03-07
And what about KVM then? Is it not known to allow alot more "direct" access to your hardware?

It could very well be that i am completely off track here:KS 


Iarwain

---

### Post by myxiplx on 2007-03-07
Yeah, reading into it the new CPU stuff does exactly what Tichondrius says.  I knew it had improved something, but it sounds like it's essentially just improved CPU support.  On the graphics front, VMware are getting there with the GPU virtualisation, they have beta support for DirectX 6 at the moment, and AMD / ATI are apparently working on virtualisation friendly GPU's, but they're not due out until 2008-9.

The smart money says VMware will have virtualised 3D accellerated graphics later this year, I'll keep my fingers crossed those improvements make their way to Linux.

So not there yet, but at least KVM's in the kernel so whatever gains are made in virtualisation should make it into Linux shortly after.

One day....

---

### Post by myxiplx on 2007-03-07
PS.  Iarwain, KVM sounds like it has less features than the other VM's at the moment.  It runs slower than Xen from what I can see because it doesn't implement para-virtualisation (whatever that is).

KVM's in the kernel because it's much smaller - it was designed to be part of the kernel, and uses Linux' memory management, etc...

I've no doubt KVM will gain features as time goes on though.

---

### Post by Iarwain ben-adar on 2007-03-07
Thanks for clearing that up :D

I don't know much about all that stuff..


Iarwain

---

