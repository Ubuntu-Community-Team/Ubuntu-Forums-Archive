---
title: "Dual boot or not dual boot?"
date: 2010-04-19
forum: The Cafe
---

### Post by Glenn Jones on 2010-04-19
Hi Guys and Gals,

I need some advice with regards to my new workstation. I've started a new job and I'm getting a new workstation but I'm unsure as to which OS to run on it. I'm going to need both Linux and Windows 7 on it. A number of possibilities include

Dual boot

Virtual Machine via Virtual Box

Cygwin 

andLinux or coLinux

and Wine

I'd rather not dual boot at it's a royal pain in the a**. But I'm unsure what the best option is. Any suggestions?

Cheers

Glenn

---

### Post by Crunchy the Headcrab on 2010-04-19
I'm a fan of virtual machines.  If you run Linux as your primary OS, put Windows in a virtual machine.  If you run Windows as your primary OS, put Linux in a virtual machine.

---

### Post by CharlesA on 2010-04-19
> **Crunchy the Headcrab said:**
> I'm a fan of virtual machines.  If you run Linux as your primary OS, put Windows in a virtual machine.  If you run Windows as your primary OS, put Linux in a virtual machine.

This.

If your machine can handle running another OS in a VM, of course.

---

### Post by Roasted on 2010-04-19
I've -never- had a problem with dual booting, and actually I swear by it due to my gaming nature. However, I still run virtual machines as well just in case I ever need them, however I can't remember when I last used them. It really just depends what you need... dual booting for me makes sense due to the better graphical performance for gaming, but virtualizing is SO convenient.

---

### Post by CharlesA on 2010-04-19
If you are just doing stuff that doesn't need a bunch of graphical eye candy, a VM would work almost as well as dualbooting.

---

### Post by Glenn Jones on 2010-04-19
Thanks guys.

I won't be using crazy graphics just number crunching with fortran ...

I guess the VM option would be best them. Out of curiosity has anyone tries andLinux?

---

### Post by MindSz on 2010-04-19
I've had dual-boot in my last 3 computers (1 PC, 2 laptops) and no problems at all. One thing though, it's a pain in the backside if you're in Ubuntu and realize you wanted to boot in Windows ...

---

### Post by CharlesA on 2010-04-19
Interesting, that andLinux.

I doubt I'd use it tho. I'll just run a regular install in a VM.

---

### Post by pricetech on 2010-04-19
I've done both and VM is definitely my preference.

---

### Post by undecim on 2010-04-19
VM is the best option if you can use hardware virtualization. Often times you will have to enable that in the BIOS.

---

### Post by gchand7 on 2010-04-19
At home I dual boot. at work I run Ubuntu in a VM just for the internet.

---

### Post by Lightstar on 2010-04-19
I dual boot, keep both OS on their own partition (of course) and I keep them clean.  I have a third partition for documents, media, etc that both OS can access.

I'm too scared to mess up the host and end up losing both OSs.
dual-boot is right for me.

---

### Post by mamamia88 on 2010-04-20
i prefer the virtualbox option with windows in vm.  you can take a snapshot of fresh install in case something happens you just revert back to clean install.  and if you have dual monitors you can have windows on one monitor and linux on the other

---

### Post by user1397 on 2010-04-20
I'm of the one OS per computer philosophy.

This is of course if you have more than one computer.

I recently bought a netbook and now I have my desktop with Windows 7 and my netbook with Ubuntu.

---

### Post by Glenn Jones on 2010-04-22
Thanks guys

I was considering using andLinux or coLinux but they aren't 64 bit so I decided to ditch that idea for now. The other option was cygwin. I haven't heard much about that from anyone here. If anyone has an opinion on that would be great. 

A few quickfire questions on VM. The goal would be to run Linux in VM and run any code etc there. Are there any downsides to running Fortran/C code in VM? Is accessing and customizing the VM linux easy eg fonts etc etc?

One more strange question has anyone tried the GNU compilers for windows?

Thanks

---

### Post by cap10Ibraim on 2010-04-22
dual boot with windows 7 
or XP on VM

---

