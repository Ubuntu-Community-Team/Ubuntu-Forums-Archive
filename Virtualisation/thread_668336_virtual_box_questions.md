---
title: "virtual box questions"
date: 2008-01-15
forum: Virtualisation
---

### Post by Falc7 on 2008-01-15
I am trying to start up a virtual box, and i have some questions, i made up a hard drive image that i don't need, i worry that it is just a waste of hard drive space, how can i delete it?

Why does VB only let me allocate at most 128mb of video memory when my graphics card has 512mb?

---

### Post by bodhi.zazen on 2008-01-15
You do not need a HD unless you plan to install an OS to it or store data.

You need to detach the virtual disk from the machine , then you should be able to delete it. If not, just delete the whole machine.

Virtualization (qemu / VBox / VMWare) does not directly use your hardware. It uses software emulated hardware. This is a common misconception about virtuilization.

---

### Post by Falc7 on 2008-01-17
Really, then i am very confused about virtualisation, forgive my ignorance:
Isen't the point of virtualisation to install another OS as part of ubuntu?
The point of my experimenting with virtual box is just to get games working, if its relevant.

If i install another OS in virtual box, will it keep all of the files i have in the other OS as part of where i choose the HD to be, so i can just load it up, sort of like a dual boot without rebooting, the other OS using some of ubuntu's disk space, is that how it works?

---

### Post by bodhi.zazen on 2008-01-17
No problem, it is confusing at first.

VirtualBox / VMWare / qemu are virtual computers. They are software wmulated videocards, motherboards, ethernet cards, RAM, etc all within you ubuntu partition.

So, yes, you can make a virtual hard drive. The drive is a file stored on your Ubuntu partition. The drive is associated with a virtual computer. You can either run an iso as a live desktop or install onto the virtual hard dirve.

The data is kept separate between the two operating systems.

---

### Post by freymann on 2008-01-18
> **Falc7 said:**
> I am trying to start up a virtual box, and i have some questions, i made up a hard drive image that i don't need, i worry that it is just a waste of hard drive space, how can i delete it?


 Open up VirtualBox.

 Click on File 

 Click on Virtual Disk Manager.

 It will show you the hard drive images that belong to your virtual OS's. Delete what you want.

---

### Post by paul.matthijsse on 2008-01-18
> **Falc7 said:**
> If i install another OS in virtual box, will it keep all of the files i have in the other OS as part of where i choose the HD to be, so i can just load it up, sort of like a dual boot without rebooting, the other OS using some of ubuntu's disk space, is that how it works?Yes, it works exactly like that. 

Cheers, Paul.

---

### Post by sistoviejo on 2008-01-18
Sorry... A virtual PC won't use your 3D video card.
The virtual machine will have a card named VirtualBoxVideo card which doesn't have 3D capabilities I think (I might be wrong). Even if it does have 3D capabilities it won't be good enaugh to run games.
To run windows games you have to install Windows natively on a separate partition.
AFAIK Virtual PCs are fast enaugh for everything except for 3D games.

---

### Post by sistoviejo on 2008-01-18
> **Falc7 said:**
> If i install another OS in virtual box, will it keep all of the files i have in the other OS as part of where i choose the HD to be, so i can just load it up, sort of like a dual boot without rebooting, the other OS using some of ubuntu's disk space, is that how it works?

The only gripe is that when you start the virtual machine you'll have two computers running at the same time sharing the computer's resources (cpu, memory...).

---

### Post by tatrefthekiller on 2008-01-18
Some emulators can use directly your graphic card, but it's still beta.
I think the better way to play games... is to boot on Windows, or to use Wine if your game is supported.
Usually, supported games are based on OpenGL (Warcraft works perfectly fine), even though some DirectX games are working.

---

### Post by Falc7 on 2008-01-25
thanks for the help guys, if it won't let me play games i will give it a miss until i find another reason i need to use it.

What exactly is OpenGL, is it like an open source DirectX, allowing games to be played under WINE, is that right?

---

### Post by rosegarden78 on 2008-01-25
My two cents is I couldn't get VMware working.  Am I still a n00b?  I dunno but I got Compiz Fusion working just install Ubuntu first.  Anyway I kind of liked QEMU because I could make QCOW virtual partitions and install operating systems.  I think Windows 3.1 worked.  I'm not sure I got WIndows 98 all through installation I think it stopped.  I got XP installed as a clean install on QCOW.  You still have to activate it by phone, though I think you can copy sn.txt or a similiar sn.??? file to preserve your activation.  Articles exist for preserving activation code for backups but never tried on a qcow.  It's cool but I don't think QEMU ran all programs perfectly.  I visited the VMware website six months ago, but it was so confusing to me I didn't know what to download and couldn't find simple instructions.

---

### Post by rosegarden78 on 2008-01-25
:)

---

### Post by sistoviejo on 2008-01-25
OpenGL is a 3D API like Direct X. The difference is that OpenGL works on linux, windows and other platforms whereas Direct X is only for Windows.
I don't think OpenGL works with Wine though.

---

