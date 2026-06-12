---
title: "the virtualization future"
date: 2007-02-10
forum: The Cafe
---

### Post by dmee on 2007-02-10
Hey guys,

what is your vision of virtualization future for linux? what will be the standard virtualization tool for ubuntu feisty w/ 2.6.20 kernel?

why such fresh and unstable thing like kvm is already a part of mainstream kernel?

where will we get 3d acceleration and the most impressive speed?

who will be the winner for the desktop virtualization: xen, kvm, vmware, virtualbox, parallels?

thank you guys.

---

### Post by matthew on 2007-02-10
This could be a very interesting thread...it's best suited for the cafe so I'm moving it there.

---

### Post by EdThaSlayer on 2007-02-10
I have never thought much about virtualization even though it is supposed to be the next big "thing".
I don't think Feisty will be focused on that, since Feisty is more focused on eye candy and easy codec installation. Maybe the one after that will be focused on virtualization once there are processors out that speed up the process of processing virtualization type of code(Meaning that Mac OS will run almost as fast in a virtualization software package as it would if it was installed to your hard drive).

---

### Post by aPello on 2007-02-10
tbh i dont see what advantages it has in a home user's environment. Its great for servers etc, but dont see the big advantage for a home user at all. 

Can some one enlighten me?

---

### Post by dmee on 2007-02-10
ok, got it.

and what for the overall virtualization trends and it's future? who is gonna present 3d acceleration and an amazing speed? i mean not only ubuntu branch.

> **aPello said:**
> tbh i dont see what advantages it has in a home user's environment. Its great for servers etc, but dont see the big advantage for a home user at all. 

Can some one enlighten me?

i guess there are lots of us who wants to get compiz/beryl 3d-cube with linux, windows and mac os on it :). am i right, fellows?

if you are a gamer then w/ virtualization tools you can forget dual-boot nightmare and play windows games w/ no problem (when we will get 3d acceleration).

if you are a software developer/web-developer you can develop, debug, test your projects in different operating systems.

if you are working w/ multimedia then w/ virtualization you can continue using your favorite professional software that is running windows or mac os.

i think, virtualization is a really great stuff even for the desktop application.

---

### Post by pay on 2007-02-10
> **aPello said:**
> tbh i dont see what advantages it has in a home user's environment. Its great for servers etc, but dont see the big advantage for a home user at all. 

Can some one enlighten me?Some might be forced to run software that only works on Windows and therefore they would need to run a virtual machine.

Also what about kqemu? It's finally gone open-source:):)

---

### Post by seijuro on 2007-02-10
I read an article a little while back about gaming on Linux and apparently vmware already has partial 3d acceleration support they had a screen shot of The Sims running under vmware. The article stated it was still in experimental stages but could be turned on easily by adding a line to a file. I don't know how old the article was so it could be even farther along now or scrapped who knows.

---

### Post by -Rick- on 2007-02-10
I've used vmplayer, Qemu and VirtualBox.

I started with Qemu. Qemu is slower than the others, but can emulate other architectures and runs on many different host systems, which was important when I was still using BSD's. vmplayer is what I use now. It's fast and supports many different guest OSs. VirtualBox has so far been useless for me. I tested 4 OSs with it: OpenBSD, Knoppix, Syllable and Sabayon. Only Knoppix would boot, I guess it needs still some time to mature.

I use emulation mostly for porting my project. With vmplayer compiling in a guest OS is still reasonable fast and so a good way to test my code on many different systems.

---

### Post by dmee on 2007-02-10
> **pay said:**
> Some might be forced to run software that only works on Windows and therefore they would need to run a virtual machine.

Also what about kqemu? It's finally gone open-source:):)

I think kqemu is not a competitor to kvm because the latter is faster.

> **-Rick- said:**
> With vmplayer compiling in a guest OS is still reasonable fast and so a good way to test my code on many different systems.

How can you estimate vmware player's speed in comparison to native system?

---

### Post by AndyCooll on 2007-02-10
> **aPello said:**
> tbh i dont see what advantages it has in a home user's environment. Its great for servers etc, but dont see the big advantage for a home user at all. 

Can some one enlighten me?

The immediate big advantage for Linux desktop users is that virtualisation enables you to run a Windoze client _at the same time_ as running your Linux desktop. No need for dual-booting.

I voted for kvm, simply because it's going to be in the next Linux kernel.

:cool:

---

### Post by reacocard on 2007-02-10
You missed one: qemu w/ qemu accelerator.

Not quite as fast as the options you list, but it's completely GPL'ed and doesn't require hardware support or kernel recompilation.

---

### Post by -Rick- on 2007-02-10
> **dmee said:**
> I think kqemu is not a competitor to kvm because the latter is faster.

I think KQEMU doesn't use hardware virtualization.

> How can you estimate vmware player's speed in comparison to native system?
About 80-90%

---

### Post by dmee on 2007-02-11
> **reacocard said:**
> You missed one: qemu w/ qemu accelerator.

Not quite as fast as the options you list, but it's completely GPL'ed and doesn't require hardware support or kernel recompilation.

Could you tell us a bit more about qemu w/ qemu accelerator?

---

### Post by cowlip on 2007-02-11
[http://linuxvirtualization.com/](http://linuxvirtualization.com/)
> QEMU vs. KQEMU vs. KVM

Posted by Fraser Campbell 4 days ago

With the just announced open sourcing of the QEMU accelerator it would be interesting to have some idea of the performance differences between QEMU, QEMU + accelerator and KVM.

It turns out that someone has already done the hard work for us. See [http://linux.inet.hr/](http://linux.inet.hr/) article Finally user-friendly virtualization for Linux.

KVM and QEMU with it&#8217;s accelerator both appear to be capable of utilizing CPU and memory at close to native speeds (perhaps 80%). Definitely worth another look on the laptop.

[http://linux.inet.hr/finally-user-friendly-virtualization-for-linux.html](http://linux.inet.hr/finally-user-friendly-virtualization-for-linux.html)

> Some benchmarking [img]http://img185.imageshack.us/img185/4291/pcmark2002memorysb8.png[/img][img]http://img185.imageshack.us/img185/1825/pcmark2002cpuxb4.png[/img]

OK, so with Windows XP installed in no time, I had plenty of time left to do some simple benchmarks. Nothing comprehensive or scientific, I remind you, just a few quick tests so that you have rough idea how KVM works in practice. I've also included few other interesting cases, because it was easy to do. Once I had installed Windows OS, it could be run even under unmodified QEMU, no problem. And with a little additional effort I also compiled kqemu, QEMU accelerator module written by QEMU's original author, unfortunately a closed-source product. Finally, the choice of the applications that I ran has fallen to only two of them, PCMark2002 and Super PI (ver 1.1e) with the sole reason that I had numbers from those two applications from the times when I had Windows XP installed natively (but that was few months ago, and I have since deleted it). Before I forget, the tests were run on an Intel E6600 processor.

I think it's pretty obvious how much improvement both kqemu and KVM bring over QEMU emulator alone. Also, it seems that kqemu still commands a slight lead over KVM, but I'm sure that KVM performance will only improve over time, it's really young compared to all other virtualization products.

Running Super PI is another story, KVM is the fastest one here, running at 84% of the native speed, which is a great result. Stock QEMU is so slow at this task, that graph above is hard to decipher, so I'll list all the results here (time to generate first million digits of pi, less is better): QEMU: 492.5 sec, kqemu: 28.5 sec, KVM: 25.5 sec, native: 21.5 sec.

Conclusion

While still in the early development stages, KVM shows a real potential. It's fun working with it, and I suppose we'll hear more and more good news about it in the following months. At the time when this technology gets incorporated in the mainstream Linux distributions (in not so distant future) virtualization will become a real commodity. And not only for data centers and server consolidation purposes, but also on Linux desktops everywhere. Mostly thanks to a really great work on behalf of QEMU & KVM developers. But, you can start playing with it today...

---

### Post by ffxr on 2007-02-13
i like virtualbox for its ease of use...  compared to vmware anyway (for a relative noob)

can anyone offer a quick synopsis of 64bit support of the various virtualisation methods.. ?

---

