---
title: "Noob question about processor architecture"
date: 2011-09-01
forum: Ubuntu Studio
---

### Post by nick2k11 on 2011-09-01
I downloaded Ubuntu Studio (AMD64). I have a Core 2 Duo processor and a 64bit version of Vista *shudder*... When I tried to test Studio in VirtualBox, it wouldn't install because the processor architecture was wrong (it needed x86-64, it only found i686) Does that mean that I need to download another version of Studio

~Thanks in advance!

---

### Post by pqwoerituytrueiwoq on 2011-09-01
i know most AMD boards have a option in the bios (with processor that supports vitalization) that let a 64bit guest os run in virtualbox probably worth giving it a look if not you will need the 32bit in the virtual box
you could just try it as a live cd (if your goal is to try it before installing)

---

### Post by nick2k11 on 2011-09-01
I would try it as a Live CD but, unfortunately, there is no option for that in the menu.

---

### Post by b0b138 on 2011-09-01
Ok this might sound silly, but, when you set up you VM, did you tell it your VM machine is 64bit, or is the VM 32?  Because other than that, I'm failing to find a reason for it not to install :(

---

### Post by pqwoerituytrueiwoq on 2011-09-02
> **nick2k11 said:**
> I would try it as a Live CD but, unfortunately, there is no option for that in the menu.
live usb then or unetbooting via hdd
what kind of computer (other than a netbook as they typically don't have one) does not support boot via cd dive in the bot menu

---

### Post by Sylos on 2011-09-02
> **pqwoerituytrueiwoq said:**
> live usb then or unetbooting via hdd
what kind of computer (other than a netbook as they typically don't have one) does not support boot via cd dive in the bot menu

Perhaps the OP means there is no option on the CD for trying in a live environment. I seem to recall one of the US versions is afflicted with this.

---

### Post by jejeman on 2011-09-02
Not all C2D processors have VT-x technology. For example my laptop has C2D T5800 and when one look at specs, one can see this:
> Intel® Virtualization Technology (VT-x) 	NoFor result I can't run 64bit virtual machines only 32bit. But of course I can run 64bit OS, as I already am.
Check the specs. for your cpu.

---

### Post by nick2k11 on 2011-09-03
There is no option on the (US) install menu to run without installing. Specs for my comp are as follows:

Core 2 Duo P7350 @ 2GHz
4GB RAM
200GB HDD
nVIDIA GeForce 9700 (if that matters)

---

### Post by jejeman on 2011-09-03
You see, your cpu also does not support VT-x technology
> Intel® Virtualization Technology (VT-x)	No
Thats why you cant run 64bit systems in Virtual Machines. You need to download 32bit version.

source
[http://ark.intel.com/products/36750/Intel-Core2-Duo-Processor-P7350-%283M-Cache-2_00-GHz-1066-MHz-FSB%29](http://ark.intel.com/products/36750/Intel-Core2-Duo-Processor-P7350-%283M-Cache-2_00-GHz-1066-MHz-FSB%29)

---

### Post by nick2k11 on 2011-09-03
Thanks! :D

---

### Post by drdos2006 on 2011-09-03
Another way to check your architecture is to run from a terminal:
lscpu

regards

---

