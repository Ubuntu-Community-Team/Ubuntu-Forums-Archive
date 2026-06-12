---
title: "Virtualisation for videogames"
date: 2014-02-14
forum: Virtualisation
---

### Post by terereforus on 2014-02-14
Hi everybody,

I am a Linux user since 8 months. Although I have made some progress during this time I still consider myself a beginner (would be glad if you can help me).

I have a multiboot system, and I used to have 2 partitions for Ubuntu 11 (home and /) just for gaming (mostly Genesis and N64 emulators, but also some linux games like Tuxkart), and it worked perfectly (almost like playing the real N64, no configuration issues, the gamepad works right out of the box). Last week I removed those partitions (Ubuntu 11) to upgrade to Ubuntu 13, and it doesn't work properly with games (I think it is an issue that has something to do with 32bits libraries). After doing some research looks like many people have this very problem.

I don't want to install Ubuntu 11 again, so I was thinking that I could try to use a **virtual machine for gaming purposes** (booting to Ubuntu 11 with the virtual machine, for playing the games). Now, my questions: 

- Is a good idea to use a virtual machine for playing games? Do they perform good?
- What kind of virtual machine should I use? I know some names like Virtual Box, KVM, Openvz, but really don't know one from the other and pros-cons of each one

Thanks for your time, hopefully this question will help other users too.

---

### Post by TheFu on 2014-02-19
Gaming inside a VM is a great idea for Scrabble and board games.
If you need high-end graphics, then virtualization is a terrible idea.

If you like pain and have a CPU/MB that supports VT-d (Core i7 or Xeon) then it might be possible to get video card passthru working to a VM. Less than 1% of all VM users do it, so it is unstable and highly experimental.

The best option for VM and graphics is probably VMware Workstation. After that, VirtualBox ... the others really aren't designed for desktop-on-desktop virtualization. They are meant for server-on-server VMs without a GPU installed. Does that make sense?

Ubuntu 11.04 and 11.10 were out of support in 2012.
Ubuntu 13.04 support ended last month and 13.10 support ends in April. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) People like you and I need to use LTS releases only.

---

### Post by CharlesA on 2014-02-19
+1 to TheFu.

I have run Diablo 2 in a Windows XP VM before, but the graphics were a bit slow. It's not worth it unless you like painfully low fps.

---

### Post by andrew.46 on 2014-02-22
> **terereforus said:**
> Is a good idea to use a virtual machine for playing games? Do they perform good?


I think that really good 3d support for gaming would be one of the holy grails of VMs. While the current situation is  better than the older days for decent gaming you will still need direct access to your hardware. Thus VMs are not the answer...

---

### Post by brokenhachi on 2014-02-24
This is definitely something that vmware is working on, though i can't speak for the other camps (VB, etc). The good thing is that it isn't only about gaming, you can use high graphics performance VMs for CAD or other graphic design applications. If vmware can get this properly sorted, it would be great to run CAD servers on top of ESXi with a big-daddy quadro or something.

check this out: [http://www.infoworld.com/t/virtual-desktop/vmware-promises-better-3d-graphics-virtualized-desktops-228991](http://www.infoworld.com/t/virtual-desktop/vmware-promises-better-3d-graphics-virtualized-desktops-228991)

To answer your question more directly though, like TheFu said it is possible with VT-d (or any amd cpu) however support is lacking and vmdirectpath is sometimes iffy. Unless you have a high end Intel CPU or AMD CPU you most likely dont have vt-d functionality though.

---

