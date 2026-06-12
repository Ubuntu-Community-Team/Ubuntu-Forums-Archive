---
title: "Virtualization methods"
date: 2005-02-15
forum: The Cafe
---

### Post by TravisNewman on 2005-02-15
OK. I have a mac and a pc. Mac on linux is fantastic. I'm running in OSX under Ubuntu right now with virtually no performance hit, and it's not virtualized, from what I've read. The Mac OS is running natively on the Mac hardware through MOL. For those with a Mac, it's kinda like starting up Classic inside OSX (though LESS of a performance hit. I can run Ubuntu, MacOSX and MacOS9 at the same time and OSX runs smoother this way than if I had classic running in the background.

So if the Mac OS can run natively on the Mac hardware through a program that provides an interface to it with no modification to the guest OS (mac os 9/x in this case) and only a kernel module added to the host OS (in this case Ubuntu), then why can't the same idea be realized for PC operating systems/hardware?

---

### Post by kassetra on 2005-02-15
*drool*  I'm sure there's some reason why not... but that sounds absolutely wonderful to these ears... er eyes... er both.
 
 must ponder this.

---

### Post by Zundfolge on 2005-02-15
[QUOTE=panickedthumb]... why can't the same idea be realized for PC operating systems/hardware?[/QUOTE]
Maybe because Mac OS X *is* Unix ... which is close enough to Linux.

Also OS X is designed to work with the Mac processor, not an x86, so you would somehow have to emulate the Mac processor in addition to other overhead, so if you could do it I doubt it would run well (lets not discount the fact that if Apple found someone able to run OS X on an Intel/AMD based machine I image Steve Jobs would hunt them down and kill them with his bare hands).

---

### Post by rufius on 2005-02-15
[QUOTE=Zundfolge]Maybe because Mac OS X *is* Unix ... which is close enough to Linux.

Also OS X is designed to work with the Mac processor, not an x86, so you would somehow have to emulate the Mac processor in addition to other overhead, so if you could do it I doubt it would run well (lets not discount the fact that if Apple found someone able to run OS X on an Intel/AMD based machine I image Steve Jobs would hunt them down and kill them with his bare hands).[/QUOTE]
 Mmmm, I wouldn't go so far as to say 'close enough' to linux. Its close yes, but the kernel setups are far from being the same. OSX runs a mach kernel while linux uses mono-kernel. There's your major difference, other than that, the internal stuff (SystemV init scripts), and the like are similar. But lets not venture to say its 'close enough' ;).

---

### Post by TravisNewman on 2005-02-15
Thought of that, but no, that's not it.

Mac OS 9 is most definitely not Unix. But it's just as smooth and compatible.
Even if it was, there's nothing comparable to this for PCs to run two PC systems, even with two *nix systems.

But I'm not saying emulating a mac on PC, I'm saying run two pc os's concurrently, say running Warty and Hoary, natively with their own kernels. You can do it with Xen, but that's a lot of modification, same with UML.

---

### Post by jdong on 2005-02-15
Have you tried VMWare before? Expensive, yes, but perfectly and effortlessly emulates PC hardware -- right down to "Invalid Boot Disk, Press any key"! :D

EDIT: I have full confidence that the Fedora team will make Xen as easy-to-use as the rest of Fedora.

---

### Post by TravisNewman on 2005-02-16
VMWARE?! Nah, that's slow as crap man. Like... molasses crap. I'm talking basically full performance, minus the memory and processor cycles it takes to run the host OS, of course. That's basically what MOL does.

VMWare is most definitely effortless, and it's hardware emulation is pretty freakin' amazing, but like I said, sloooowww...

---

### Post by kassetra on 2005-02-16
Some of us use vmware to run all of our expensive graphics applications and will admit that while it's not as fast as native, it's doing much better these days.
 
 heh.
 
 not that I uh know anyone uh using vmware.  heh.

---

### Post by jdong on 2005-02-16
[QUOTE=panickedthumb]VMWARE?! Nah, that's slow as crap man. Like... molasses crap. I'm talking basically full performance, minus the memory and processor cycles it takes to run the host OS, of course. That's basically what MOL does.

VMWare is most definitely effortless, and it's hardware emulation is pretty freakin' amazing, but like I said, sloooowww...[/QUOTE]

1. I disagree that VMWare is as slow as you make it out to be -- I use it quite often to emulate Windows boxes on Linux, and it feels pretty damn (err, darn) close to native speed, though disk I/O does fall a bit short. Have you used the latest (4.5.2) VMware? It gets better release after release.

2. Mac on Linux is more along the Xen lines -- that is, a paravirtualization layer over the OS/Underlying Hardware. Very little emulation is involved. Just that the implementation is a lot more user-friendly! Windows AMD64 owner? Heard of WOW64? Basically, Windows XP 64-bit Edition for x86_64 runs a 32-bit copy of Windows within itself, with minimal performance impact. Again, **paravirtualization**


As I said before, Xen is what you want -- I just hope Fedora makes a user-friendly GUI config tool for it by Core 4's release.

---

### Post by TravisNewman on 2005-02-16
Yeah, I wish Adobe et als. would jump on the Linux train... it'd get them more revenue definitely.

But yes, I admit, it's much better than it used to be.

Way to go on getting VIPed kassetra. You have to imagine StrongBad saying VIPed there, as in how he says "404'd" when you type a wrong url on homestar. ie: [http://www.homestarrunner.com/randomcrapthatdoesntwork.html](http://www.homestarrunner.com/randomcrapthatdoesntwork.html)

Sorry, I'm feeling random tonight.

---

### Post by kassetra on 2005-02-16
Sometimes I go to a nonexistent page on h*r just for that!  I love that site.  so between hearing the count, "1, 1 cup of Ubuntu, ah ah ah ah" and "VIP'd!" ... I'm a nut.

---

### Post by TravisNewman on 2005-02-20
Oooooh it appears I have gotten my wish, from qemu no less:

[http://slashdot.org/article.pl?sid=05/02/19/1538231&tid=190&tid=126&tid=1](http://slashdot.org/article.pl?sid=05/02/19/1538231&tid=190&tid=126&tid=1)

---

### Post by TravisNewman on 2005-02-20
I just got it compiled and tried it out, first without and then with the kqemu module, and WOW it's fast. Much faster than VMWare, and it seems faster than MacOnLinux, but I'd have to try them both on the same physical computer to really know that, and MOL won't run on a PC, and qemu with the kqemu module won't run on a mac. So who knows... but it is definitely amazing. You might wanna think about using this over VMWare, kassetra and jdong!

And woohoo! post 1000 ;)

---

### Post by kassetra on 2005-02-20
Congrats on post 1k!!
 
 Hmmm, maybe I will look into that option... because sometimes when I'm working with my giganto 500+Mb files in photoshop, my machine grinds to a screeching halt.
 
 More new stuff to try!  woo!

---

### Post by poofyhairguy on 2005-02-21
[QUOTE=jdong]As I said before, Xen is what you want -- I just hope Fedora makes a user-friendly GUI config tool for it by Core 4's release.[/QUOTE]

If there is one thing Fedora can make, its nice GUI tools. Only with Hoary (and no other distro) do I not envy Core 2's network tool.

---

### Post by jdong on 2005-02-22
[QUOTE=poofyhairguy]If there is one thing Fedora can make, its nice GUI tools. Only with Hoary (and no other distro) do I not envy Core 2's network tool.[/QUOTE]

They're so much farther and more mature than us that they can afford to spend the time on Xen.

BTW, Xen is in the daily SuSE kernel builds, too -- Go SUSE!

---

### Post by poofyhairguy on 2005-02-22
[QUOTE=jdong]
BTW, Xen is in the daily SuSE kernel builds, too -- Go SUSE![/QUOTE]

Go linux!

---

### Post by goofrider on 2005-04-07
[QUOTE=panickedthumb]VMWARE?! Nah, that's slow as crap man. Like... molasses crap. I'm talking basically full performance, minus the memory and processor cycles it takes to run the host OS, of course. That's basically what MOL does.

VMWare is most definitely effortless, and it's hardware emulation is pretty freakin' amazing, but like I said, sloooowww...[/QUOTE]

For what I understand, VMware, MOL and Xen are pretty similiar in architeture (and you might as well include QEMU with the QEMU aceelerator in this category too). Only core peripheral hardware (video, sound, disk I/O, etc.) is emulated, CPU instructions in the guest OS are otherwise passed through to the real CPU (as opposed to Bochs, Virtual PC and QEMU proper, where the CPU is emulated).

I can't see why MOL on PPC can be significantly faster than VMware on x86, other than the possiblity that MOL might be trapping OS9/OSX system calls (especially disk I/O and video) and translate them to native Linux system calls. But this would put MOL into the API emlation territory alas WINE.

Also don't forget that VMware comes with display drivers of Windows and Linux guest OSes that traps GDI and X Window calls in the guest OSes and hand them over to VMware to render them natively in the host OS. I believe the guest OS in MOL simply uses native display drivers, therefore video in MOL should be completely emulated unless I missed something. This might also attribute to your unfavorable experiences with VMware: VMware performance suffers a great deal if you did not install the special VMware display drivers properly in the guest OS.

Another factor is memory. VMware uses static memory allocation, so if you didn't allocate the guest OS sufficient RAM, it'll have to swap to disk via emulated disk I/O, which causes huge performance hit. Does MOL allocate memory dynamically? FWIW, VMware ESX server uses dynamic memory allocation.

Lastly, compared to PowerPC (or most other modern 32-bit CPUs for that matter), the IA32 architeture is inheritly difficult to virtualize/compartmentize. x86 OSes frequently require priviledge instructions that can not be virtualized in IA32 and hence must be trapped and emulated. This increases complexity tremendously because now the virtualization layer must maintain the VM's state partially in emulated mode and the rest in native mode. Other modern RISC CPU architetures like PowerPC and Alpha were designed to allow complete virtualization/compartmentization from the get-go. Future Intel and AMD CPUs will feature proper virtualization in the CPU core (branded VT and Pacifica respectively).

From my experience, VMware performs extremely well as long as resources are properly allocated. I think it's about 70-80% native speed with CPU-intensive tasks with little disk and video I/O. Graphics performance is about 50-70% native, and disk I/O performance depends on a lot of factors like whether you're using raw phyical disks or virtual disk files.

---

