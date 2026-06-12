---
title: "Thoughts/ideas about this project?"
date: 2010-11-12
forum: The Cafe
---

### Post by Dustin2128 on 2010-11-12
I'm working on computer projects aplenty currently, between my new hex-core desktop, search for a laptop and now classic computer project. This one however is probably doable tonight or tomorrow. 

I like classic PC games, and I happen to have in my possession a 486 processor with 32 or 64Mb RAM, plus assorted expansion cards (this was before everything was integrated on the motherboard) and a 6GB hard drive (original was 700MB but I need some breathing room). Its pretty much up and running, I just need to build a simple case, hook everything up and after that's done, load FreeDOS. 

The custom case is what I'm currently debating- I'm not sure whether to make a normal case, a side case enabling quick swapping of motherboards with my plethora of others (I've currently got a 486, Pentium pro, pentium 2, pentium 3, 2 pentium 4's and a Celeron D, most without cases) or a single piece- that is, integrate the monitor and motherboard with the keyboard and trackball, running it all through one power cord.

Also, is freeDOS totally and completely compatible with DOS games, hardware and programs? And can anyone recommend an install method that wouldn't require me to waste one of my few DVDs (not sure if the BIOS can even boot from DVD come to think of it, don't have any CD-Rs)? One idea I had, since I have a fairly nice P4 machine with IDE cables was that I could install to a VM and transfer the VM to the HDD. I read about it a couple months ago, but I'm not entirely sure how to do it, does anyone know?

---

### Post by Spice Weasel on 2010-11-12
FreeDOS is compatible with most DOS programs. :)

If it works in DOSBox, it will work in FreeDOS.

---

### Post by Austin25 on 2010-11-12
You should go for an acrylic case.

What a coincidence that I have migrated hard drives successfully from a Virtual machine to physical machines! I used ssh, Virtualbox, and VBoxManage.
First, you get the image of the physical machine's hard drive. (for size purposes)
```
ssh <physical machine's ip or name.local> 'dd if=/dev/sda' | dd of=harddrive.raw
```
Then you convert it to something usable.(also, in the ~/.Virtualbox/HardDisks directory)
```
VBoxManage convertfromraw harddrive.raw ~/.Virtualbox/HardDisks/vmachine.vdi --format vdi
```
Then you make a machine with it in Virtualbox, I assume you know how to do that. Make all the changes you need, then when you're ready:
```
VBoxManage clonehd ~/.Virtualbox/HardDisks/vmachine.vdi burnable.raw --format raw
dd if=burnable.raw | ssh <physical machine's ip or name.local> 'dd of=/dev/sda'
```
Notes: You probably will want to run the physical machine with a live environment (remember to install ssh), or else it will kernel panic and your drive will be borked. Also, replace /dev/sda with whatever it decides to name your drive.

---

### Post by Dustin2128 on 2010-11-12
> **Austin25 said:**
> ...
EDIT: So after I connect it to my machine, I put in: ```
ssh name.local 'dd if=/drive/name' | dd of=harddrive.raw
```

---

### Post by Austin25 on 2010-11-12
> **Dustin2128 said:**
> EDIT: So after I connect it to my machine, I put in: ```
ssh name.local 'dd if=/drive/name' | dd of=harddrive.raw
```
yep, just make sure it's running from some live environment (cd, usb, etc.) so you don't kernel panic. For copying, you should be fine, but writing you should be careful with.

---

