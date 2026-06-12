---
title: "Ubuntu in a virtual machine"
date: 2007-11-30
forum: The Cafe
---

### Post by manu456 on 2007-11-30
I'm sure this question has been brought up before but I need some advice based on my situation.

I have an HP tx1000 laptop which is known to have a lot of problems with ubuntu. I mean i have been using ubuntu on it for 5 months but I've had to re-install Ubuntu many times due to some problem or the other. SOmetimes I get the 100% CPU problem. Sometimes random lockups etc. USB hot plug, touchscreen etc etc.

Now I don't want to give up on Ubuntu its my favourite linux distribution so I'm thinking of running it inside a virtual machine. Guys please suggest what's the best option.

I have opensuse running and it runs quite well on my machine. So first option is runnning ubuntu inside openSuse. I haven't tried any virtualization softwares like Xen , Qemu etc. Which one do you recommend?

ANother option is running inside windows vista. Vista came with my laptop and it might be a crappy OS but the thing is that it is very STABLE on my mahcine. And I have a touchscreen which works flawlessly in Vista. I have been able to run the touchscreen in Ubuntu after A LOT of effort but its still very unresponsive and slow. 

I use vmware in vista at work and it seems to work well. For the moment I seemt to be more inclined to go for this option because of the stability factor unless you guys convinvce me otherwise ;)

Thanks and Cheers
Manu

---

### Post by aysiu on 2007-11-30
I would recommend VirtualBox.

More details (including screenshots) here:
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by Macintosh Sauce on 2007-11-30
I have VMware Fusion on my Mac Pro and Ubuntu and most other Linux distributions run quite nicely. I can allocate any amount of RAM desired (I use 5 GB) and the speed is full as it is using one of my two dual core Xeon processors.

---

### Post by Tux Aubrey on 2007-11-30
+1 for VirtualBox in SUSE

I run several Ubuntu VMs (inside Ubuntu!) for testing purposes and I find VirtualBox to be very Ubuntu-friendly (some other distros have given me problems, especially with the LinuxAdditions which you will need to get the most of a VM)

Do you have enough RAM to allocate 512Mb to the VM?  

I doubt you will touchscreen in a VM anyway.  Inputs and outputs are pretty generic and limited.

---

### Post by manu456 on 2007-11-30
Thanks everyone for your replies. Virtualbox seems like a good option. Has anybody used it with vista as the host OS? Their site hints they have some compatibility  problems...

I have 2GB of RAM which should be enough for running 2 OSes

And Macintosh Sauce you have some cool specs for your machine!:cool: But over here I'm talking about a conservative lil laptop.

> **Tux Aubrey said:**
> 
I doubt you will touchscreen in a VM anyway.  Inputs and outputs are pretty generic and limited.

I agree but if I start using vista as my primary OS with all my development work inside a VM then I can at least use that capability when i want to watch a movie or jot down some notes or something... I will have that option...

I will try virtual box on suse first. Do I have to assign RAM to the virtual machine in the beginning? Can I reallocate RAM at a later stage?

---

### Post by popch on 2007-11-30
> **manu456 said:**
> Do I have to assign RAM to the virtual machine in the beginning? Can I reallocate RAM at a later stage?

The amount of RAM given to a virtual machine is just one of the properties you set for that machine. You can change that amount any time, provided the virtual machine is shut down.

---

