---
title: "Migrating from OpenSuSE Server to Ubuntu Server, tons of questions"
date: 2016-09-04
forum: Server Platforms
---

### Post by linuxdude1990 on 2016-09-04
I have a 64BIT OpenSuSE server I'm looking to migrate over to Ubuntu.
Dell 7500 Workstation with Intel E5 Xeon processor
64GB of RAM and 20TB of data 
MySQL database to migrate over with it.

First off before going any further, I noticed the only architecture for 64bit is AMD 64, so does this mean having a Dell server based on Intel, I'm dead in the water as is? If so I can just go towards SME Server, but I would rather try Ubuntu as it's a bit unique on it's own/to try something different.

Or is there something unique about the 32bit version that will allow it to use the full 64GB of RAM? This is a domain controller that will also virtualize multiple other servers and other functions. Basically a server with multiple Virtual servers that will at least host 15 VMs total using VirtualBox. So no room for games on it.

---

### Post by volkswagner on 2016-09-04
That wasn't very many questions ;)

The AMD 64 question has been asked many times. I'm not sure why Ubuntu insists on the naming convention. I know it's related to AMD being the first 64bit processor. The AMD64 is 64bit and fully compatible with Intel CPUs.

Regarding virtualization, please consider moving to KVM.

---

### Post by linuxdude1990 on 2016-09-04
> **volkswagner said:**
> That wasn't very many questions ;)

The AMD 64 question has been asked many times. I'm not sure why Ubuntu insists on the naming convention. I know it's related to AMD being the first 64bit processor. The AMD64 is 64bit and fully compatible with Intel CPUs.

Regarding virtualization, please consider moving to KVM.

AMD64 is actually a naming scheme for AMD CPU architecture AMD64. 

If it's really just a composite of the multiple CPU architectures, I wish they would have just said so.

---

### Post by linuxdude1990 on 2016-09-04
It wont let me edit my last post, but I wanted to add, KVM wont work for what is being done server side as KVM is only workable on 32bit VMs when all programs being run on the virtual servers are 64bit.

---

### Post by mastablasta on 2016-09-07
> **volkswagner said:**
> 
The AMD 64 question has been asked many times. I'm not sure why Ubuntu insists on the naming convention. I know it's related to AMD being the first 64bit processor. The AMD64 is 64bit and fully compatible with Intel CPUs.

a bit off topic, but...

...what could be the alternative naming? i686 ? that's the same thing only Intel (intel 686). Would it then work on my AMD64 server?

64bit ? maybe that could be it. not sure what problmes that would bring in.

i guess i am getting too old, but to me it makes perfect sense to name the image AMD64. but that's because i followed the news closely when they revealed a 64 bit desktop AMD CPU. And at the time it looked like AMD might overtake or at least be very competitive to Intel. and they probably would have been if it werent for well known dirty Intel politics. so if nothing else at least we could give them a bit of credit :)

---

### Post by volkswagner on 2016-09-07
> **linuxdude1990 said:**
> It wont let me edit my last post, but I wanted to add, KVM wont work for what is being done server side as KVM is only workable on 32bit VMs when all programs being run on the virtual servers are 64bit.

Why would you say such a thing? I assume you plan to use a 64bit host operating system... 64 bit guests are no problem.

---

### Post by SeijiSensei on 2016-09-07
> **linuxdude1990 said:**
> AMD64 is actually a naming scheme for AMD CPU architecture AMD64. 

If it's really just a composite of the multiple CPU architectures, I wish they would have just said so.

Over in the RedHat world, they use "x86_64" for 64-bit kernels.  Seems much more sensible to me.

---

