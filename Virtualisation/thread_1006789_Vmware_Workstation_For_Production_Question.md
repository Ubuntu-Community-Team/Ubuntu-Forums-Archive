---
title: "Vmware Workstation For Production Question"
date: 2008-12-09
forum: Virtualisation
---

### Post by dontgvadamn on 2008-12-09
I have been running Ubuntu and Vista Ultimate both on a dual boot system. Currently I have XP setup in a virtual Machine inside Vista, This was just to play around with XP from time to time. However I use Vista For CG animation production. I dont want to get all new software to run everything in Linux it would cost way too much. 

Mainly what I run is 3DS Max, Maya, XSI Zbrush...etc. I really like ubuntu though and Have decided maybe it would be a good idea to run them simultaniously by putting vista in a virtual machine inside Ubuntu. 

My question is though how would running those heavy load applications in a Virtual machine effect performance? Would my renders be slowed down? would the graphics degrade at all?

This is all for production so I cant take a hit on any part of it...also some scenes are pretty heavy with polygons, so I dont want to reduce my render time either....It would be nice because I can take advantage of my dual heads and have one OS on each screen this way.

Any advice would be appreciated...thanks

---

### Post by Dedoimedo on 2008-12-10
Virtualization software does not support 3D that well yet. It's getting better and better, but you might not be able to utilize fully the 3D acceleration in the virtual machines.

VMware Workstation 6.5 does offer some directx support for windows guests, but how well or how much, I don't know.

As to the load, it depends on how much ram you have, how much you dedicate to your virtual machines etc. The more the better all around. A strong, multi-core processor helps. Lots of hard disk space, several hard disks etc.

Dedoimedo

---

### Post by dontgvadamn on 2008-12-10
thanks I am going to give it a try...if I can get it to install...I have been fighting it all night.

I think I should be ok on the ram and hard disk. I have a 1TB SATA drive and 8 GB ram. also I have a quad core processor....If rendering becomes slow I think I will build a older computer and turn it into a render Farm...that should take care of any slow down in rendering I get...if any.


Now On to the Install....all the how to's I have found give a pretty simple install process...but no go for me.....my package is labeledVMware-Workstation-6.5.1-126130.x86_64.bundle...I am running 64 bit OS's

The how to's are all labeled VMware-Workstation-6.5XXXX.i386.bundle dunno if this is what is making the difference. But when I run their install method:
```
gksudo ./Vmware-Workstation-6.5.1-126180.x86_64.bundle
```

Instead of getting confirmation screens like described by the how to's...I get nothing and my terminal path returns to the directory.

---

### Post by scorp123 on 2008-12-10
> **dontgvadamn said:**
>  Instead of getting confirmation screens like described by the how to's...I get nothing and my terminal path returns to the directory. If I had to bet I'd say that that *.bundle file is not executable? Can you try this:
```
chmod 755 ./Vmware-Workstation-6.5.1-126180.x86_64.bundle
gksudo ./Vmware-Workstation-6.5.1-126180.x86_64.bundle

```

---

### Post by dontgvadamn on 2008-12-10
awesome that did the trick...I didnt even think about it not being executablt...I would have thought it would be I got it straight from VMware...thanks for the help

---

### Post by scorp123 on 2008-12-10
> **dontgvadamn said:**
> ..thanks for the help Feel free to hit that "Thank you" button ;)

---

### Post by dontgvadamn on 2008-12-12
Now I have it installed I am having a problem getting Vista to install as a guest OS....It keeps hanging on the install. It gets to the part of the microsoft load screen then hangs....and it really slows down my system...I have assigned it the max amount of RAM, and plenty of virtual drive space. And I assigned it to use 2 cores since I have a 4 core CPU.

Are there some support files I need in Linux that I missed?

---

### Post by scorp123 on 2008-12-17
> **dontgvadamn said:**
> And I assigned it to use 2 cores since I have a 4 core CPU. Don't do that!

Giving more CPU's to a VM actually slows the whole thing down. It's only useful if you e.g. are a programmer and want to test a program in a 1 CPU vs. multiple CPU's scenario. Those CPU's inside any VM (be that VirtualBox, VMware, whatever) are simulated representations of your real CPU. So it takes the system some efforts to simulate that CPU inside your VM. More CPU's mean more efforts required == more overhead == overall slower system.

Besides: your logic is a bit flawed. "I have a 4 core CPU" and you gave "2 cores" to Vista. So you seem to think: "Now Vista is running on two cores, and Linux is running on two cores .... "  Nope. That's not the case. Linux is still in control of all 4 cores. :)

---

### Post by hongri1998 on 2008-12-17
Manually operated **[ball valve](http://www.valvesupplier.net/petro-valve.htm)** can be closed quickly and thus there is a danger of water hammer. Some ball valves are equipped with an actuator that may be pneumatically or motor (electric) operated. These [ball valves]("http://www.valvesupplier.net/petro-valve.htm") can be used either for on/off or flow control.

---

