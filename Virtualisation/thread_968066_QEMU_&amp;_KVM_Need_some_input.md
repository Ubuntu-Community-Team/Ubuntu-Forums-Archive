---
title: "QEMU &amp; KVM Need some input"
date: 2008-11-02
forum: Virtualisation
---

### Post by BGFG on 2008-11-02
Hi All, 
I was put on to QEMU by Smartboyathome (Thanks man)
now i just want to clear up some stuff.
I've installed QEMU KVM and Qemulator 0.5, It was sugested that i use KQEMU but i want to avoid KDE libraries on my machine.
Question:
Do KVM and QEMU automatically work together or do i need to do something further?

System: Intrepid Ibex X64, Athlon X2 4000+

---

### Post by smartboyathome on 2008-11-02
I've been reading, and you need to rename the QEMU binary
```
sudo mv qemu-old
```
then symlink qemu to kvm
```
sudo ln -s /usr/bin/kvm /usr/bin/qemu
```
And it should work. But KVM is different than KQEMU.

I can't tell you if KVM works, though, as I'm having problems of my own which I am about to post a new topic on.

**BIG EDIT**: Disregard the above, I hadn't known about the option to go into Edit > Preferences, then click x86 in the bottom box of the window which shows up, and set it to kvm. Then click add, and delete the first x86 option. Do the same for x86-64 if you want (though not really needed imo).

---

### Post by red_team316 on 2008-11-02
On Kubuntu Hardy, all I had to do was install kvm and qemu. Then to fire it up

```

sudo kvm -cdrom whatever.iso -boot d -m 1024

```

smartboyathome, I think your codeblock is wrong :P

---

### Post by smartboyathome on 2008-11-02
> **red_team316 said:**
> On Kubuntu Hardy, all I had to do was install kvm and qemu. Then to fire it up

```

sudo kvm -cdrom whatever.iso -boot d -m 1024

```

smartboyathome, I think your codeblock is wrong :P

I put a big edit above, which says to disregard that, as you can set it to use kvm in the GUI. He's using Qemulator instead of the CLI.

---

### Post by red_team316 on 2008-11-02
the error was and still is in your ln command ;) You linked kvm to itself

---

### Post by smartboyathome on 2008-11-02
> **red_team316 said:**
> the error was and still is in your ln command ;) You linked kvm to itself

Oops, fixed. :oops:

---

### Post by bodhi.zazen on 2008-11-03
> **BGFG said:**
> Hi All, 
I was put on to QEMU by Smartboyathome (Thanks man)
now i just want to clear up some stuff.
I've installed QEMU KVM and Qemulator 0.5, It was sugested that i use KQEMU but i want to avoid KDE libraries on my machine.
Question:
Do KVM and QEMU automatically work together or do i need to do something further?

System: Intrepid Ibex X64, Athlon X2 4000+

Well, just to clarify a few things.

Unlike most "K" apps, kqemu and kvm are not KDE apps.

Second kqemu is a accelerator for qemu. Unfortunately qemu is still slow even with kqemu :(

kvm is "Kernel Virtual Machine"

[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

If you have the hardware, it is much much faster then qemu ;)

HTH

---

### Post by red_team316 on 2008-11-03
I knew kvm wasn't but I thought kqemu was(learned something). Anyways, forget kqemu like bohdi said. It does nothing for you but kvm is wicked fast. I started using it now instead of Virtualbox as virtualbox can't support 64-bit ISOs.

---

### Post by bodhi.zazen on 2008-11-03
> **red_team316 said:**
> I knew kvm wasn't but I thought kqemu was(learned something). Anyways, forget kqemu like bohdi said. It does nothing for you but kvm is wicked fast. I started using it now instead of Virtualbox as virtualbox can't support 64-bit ISOs.

Sorry, my mistake.

There are actually 2 kqemu.

The first is unrelated to KDE and is kernel module that acts as an accelerator for qemu.

[http://bellard.org/qemu/kqemu-tech.html](http://bellard.org/qemu/kqemu-tech.html)

[http://lwn.net/Articles/220807/](http://lwn.net/Articles/220807/)

The second, which unfortunately has the same name, IS a KDE application and is a GUI front end for qemu.

[http://kqemu.sourceforge.net/](http://kqemu.sourceforge.net/)

---

### Post by BGFG on 2008-11-03
> **bodhi.zazen said:**
> Sorry, my mistake.

There are actually 2 kqemu.

The first is unrelated to KDE and is kernel module that acts as an accelerator for qemu.

[http://bellard.org/qemu/kqemu-tech.html](http://bellard.org/qemu/kqemu-tech.html)

[http://lwn.net/Articles/220807/](http://lwn.net/Articles/220807/)

The second, which unfortunately has the same name, IS a KDE application and is a GUI front end for qemu.

[http://kqemu.sourceforge.net/](http://kqemu.sourceforge.net/)

Thanks to all for the responses, Was beginning to think i was being ignored till i realized you were all probably at work :)

I managed to get XP installed, but as you all alluded to, it's terribly slow. I don't however have the correct kqemu installed. Will that make any difference ?
As for KVM, i'd like to try it but is it exclusively CLI ? not that i mind but if there was a GUI i'd definitely use it.
I came across Virtual Machine Manager and installed it, is that a useful tool ?

On changing X86 to KVM in Qemulator, do i simply change the "PATH" to KVM ?

Thanks All.

---

### Post by BGFG on 2008-11-03
> **red_team316 said:**
> I knew kvm wasn't but I thought kqemu was(learned something). Anyways, forget kqemu like bohdi said. It does nothing for you but kvm is wicked fast. I started using it now instead of Virtualbox as virtualbox can't support 64-bit ISOs.

I suppose KVM is it, but I think VB supports 64bit now though. I'd still prefer to use something native to the kernel. So i think i'll learn KVM.

---

### Post by bodhi.zazen on 2008-11-03
IMO, kvm is easier to run on the command line.

There is a GUI for it, virt-manager. I am sure virt-manager will improve, but it does not have all the options.

I wrote a brief how-to on KVM at the top of these forums. To be honest, it is not difficult to run KVM from the command line.

If you are looking for virtualization with a nice gui, I suggest VMWare (I think VMWare will automate a little more then VBox). 

As an alternate, take a look at VirtualBox.

---

### Post by BGFG on 2008-11-03
I was using virtualbox, but with VB i can't do anything else on the machine. With QEMU i still have resources to use.
Apparently it was as easy as changing the X86 path to KVM in Qemulator, since i have the machine open right now and everything is working. Although it is slow. 

So KVM for the absolute fastest ? If so then that's what i'll use.

---

### Post by bodhi.zazen on 2008-11-03
IMO, if you have the hardware, KVM is faster.

KVM also has support for 64 bit guests and multiple cores.

---

### Post by red_team316 on 2008-11-03
> **BGFG said:**
> I suppose KVM is it, but I think VB supports 64bit now though. I'd still prefer to use something native to the kernel. So i think i'll learn KVM.

the OSE version? linky!

What I mean is that I am running a 64-bit OS and Vbox will work fine but the virtual OS can't be 64-bit. If this has changed, I'm interested.

---

