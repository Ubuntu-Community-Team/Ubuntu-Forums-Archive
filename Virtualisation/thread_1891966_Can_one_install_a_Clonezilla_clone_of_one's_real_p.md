---
title: "Can one install a Clonezilla clone of one's real partions' in a .vdi in VBox?"
date: 2011-12-06
forum: Virtualisation
---

### Post by mikodo on 2011-12-06
I am just learning about cloning with Clonezilla. If one were to mount VBox to /mnt on the tree, could one use Clonezilla, to clone all the drives' live partitions, I guess except the MBR, as a .vdi? Or, would it need everything including the /boot partition too?

Is anything like this possible?

Please, don't hesitate to tell me, if that's a stupid question; but it would be cool! Then, when I inevitably broke it beyond repair (at least for me), I could just start over!

Thanks.

---

### Post by jerrrys on 2011-12-08
I use clonezilla to clone HDD to HDD (vBox installed) and it works fine.

If you want to copy a guest:

[https://www.google.com/search?client=ubuntu&channel=fs&q=copy+clone+guest+vbox&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=copy+clone+guest+vbox&ie=utf-8&oe=utf-8)

also the vBox forum is a good source of info.

[https://forums.virtualbox.org/](https://forums.virtualbox.org/)

and there documentation is excellent

[https://www.virtualbox.org/wiki/Documentation](https://www.virtualbox.org/wiki/Documentation)

---

### Post by mikodo on 2011-12-08
> **jerrrys said:**
> I use clonezilla to clone HDD to HDD (vBox installed) and it works fine.

If you want to copy a guest:

[https://www.google.com/search?client=ubuntu&channel=fs&q=copy+clone+guest+vbox&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=copy+clone+guest+vbox&ie=utf-8&oe=utf-8)

also the vBox forum is a good source of info.

[https://forums.virtualbox.org/](https://forums.virtualbox.org/)

and there documentation is excellent

[https://www.virtualbox.org/wiki/Documentation](https://www.virtualbox.org/wiki/Documentation)
Thank you, for taking the time to look up the links and posting them in your response. I will use the forum for VirtualBox you gave in a link for further inquires; also use the documentation page for info.

:)

---

### Post by jerrrys on 2011-12-09
your welcome

I overlooked one

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=clone+copy+virtualbox+vbox&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=clone+copy+virtualbox+vbox&sa=Search&cof=FORID:9)

---

### Post by JKyleOKC on 2011-12-11
> **mikodo said:**
> Please, don't hesitate to tell me, if that's a stupid question; but it would be cool! Then, when I inevitably broke it beyond repair (at least for me), I could just start over!It's not at all stupid, but there's a much simpler solution that has worked for me in the past.

I simply copied the *.vdi files (which are the virtual disks) to an external drive. To restore to a different machine, I first copied the VDI files to the new box, added them to vbox's virtual disk manager, then created a new VM with all the same characteristics as the old one, and assigned the copied VDI files as its drives rather than creating new ones.

I discovered this backup technique purely by accident; the hard drive of my main system appeared to go bad, so I replaced it and re-installed Xubuntu and vbox. I then hooked up the original drive as an external, and was able to copy the VDI files for all eight VMs over to the new drive. Since the VMs themselves didn't have any special configurations, they were easy to create again, and the copied virtual drives worked perfectly right from the start.

---

### Post by haqking on 2011-12-11
> **JKyleOKC said:**
> It's not at all stupid, but there's a much simpler solution that has worked for me in the past.

I simply copied the *.vdi files (which are the virtual disks) to an external drive. To restore to a different machine, I first copied the VDI files to the new box, added them to vbox's virtual disk manager, then created a new VM with all the same characteristics as the old one, and assigned the copied VDI files as its drives rather than creating new ones.

I discovered this backup technique purely by accident; the hard drive of my main system appeared to go bad, so I replaced it and re-installed Xubuntu and vbox. I then hooked up the original drive as an external, and was able to copy the VDI files for all eight VMs over to the new drive. Since the VMs themselves didn't have any special configurations, they were easy to create again, and the copied virtual drives worked perfectly right from the start.

That has nothing to do with the OP question.

to the OP yes you can clone your existing HDD and into a VM.

Create a VM with the settings you want, create a .vdi the same size or larger than the source and then boot the machine to a clonezilla.iso or real CD and then clone it in (remember to enable your USB HDD or device that your clone is on from the devices menu)

cheers

---

### Post by JKyleOKC on 2011-12-11
I realized that shortly after posting!

However does the difference between the real hardware of the host and the virtual hardware of the VM enter into the picture at all? For instance, when configuring a new VM one can select from at least two different kinds of disk controller, around four kinds of network adapters, and so on. The host system's configuration of loadable modules was determined during its original installation, and it's not very likely that a guest will need that same set of modules.

My point is that I would expect a true clone of the host to require considerable tweaking after being installed as a guest, and in the worst case, not to work at all. Is it really as simple as this thread makes it appear?

---

### Post by haqking on 2011-12-11
> **JKyleOKC said:**
> I realized that shortly after posting!

However does the difference between the real hardware of the host and the virtual hardware of the VM enter into the picture at all? For instance, when configuring a new VM one can select from at least two different kinds of disk controller, around four kinds of network adapters, and so on. The host system's configuration of loadable modules was determined during its original installation, and it's not very likely that a guest will need that same set of modules.

My point is that I would expect a true clone of the host to require considerable tweaking after being installed as a guest, and in the worst case, not to work at all. Is it really as simple as this thread makes it appear?


not really, the main thing that needs tweaking if any if a Linux system is the persistent udev rules.

everything is virtualised and so always makes it easy for me.

It is a real effortless task to be honest.

i am not saying some wont encounter some issues, but in my experience it has been minimal or non-existant.

I can imagine more issues with raid type devices for example but i would never clone a raid device into a VM to be honest, if it is a simple setup then 

should be no issues

Edit: thinking back the only issue i ever had was when i wanted to clone an existing dual boot backtrack 4 and 5 system from another machine into a VM on my main machine and the issue was with the drive controller which is an easy change and with a grub update

---

### Post by JKyleOKC on 2011-12-11
I was actually more concerned with video driver issues, since they are so prevalent even in upgrades from one version to the next. I'd be especially suspicious of proprietary drivers such as nVidia and ATI, when cloned into the virtual monitor. The other tricky part would be network adapters, especially those for wireless.

However it's nice to know that things mostly "just work" and it does offer an excellent quick full backup, by copying off the VDI file of the clone to an external (which does tie back to the original question, though in a roundabout way)...

---

### Post by haqking on 2011-12-11
> **JKyleOKC said:**
> I was actually more concerned with video driver issues, since they are so prevalent even in upgrades from one version to the next. I'd be especially suspicious of proprietary drivers such as nVidia and ATI, when cloned into the virtual monitor. The other tricky part would be network adapters, especially those for wireless.

However it's nice to know that things mostly "just work" and it does offer an excellent quick full backup, by copying off the VDI file of the clone to an external (which does tie back to the original question, though in a roundabout way)...

neither are an issue, seeing as wireless doesnt work in a VM anyways unless you use a USB adapter.

As for Video, it is virtualised so again it doesnt matter.

As for backups, use clonezilla to clone your machine and thats it, or for vdi backups i keep mine on a external HDD anyways which i have a mirror of

---

### Post by mikodo on 2011-12-12
Thanks everyone, for the thoughts and responses. I will be doing some experimenting then, since it is possible.

:)

---

### Post by mikodo on 2011-12-13
> **haqking said:**
> 

to the OP yes you can clone your existing HDD and into a VM.

Create a VM with the settings you want, create a .vdi the same size or larger than the source and then boot the machine to a clonezilla.iso or real CD and then clone it in (remember to enable your USB HDD or device that your clone is on from the devices menu)

cheers
So, if I understand correctly, I should do something like this:


1) Partition my internal HDD, to allow lots of space for the VM.

2) Mount VBox on the tree at /media, using a new partition of larger space, than my internal OS uses, or will be using.

3) Create a .vdi larger than my present OS.

4) Clone my internal HDD OS, onto my USB HDD.

5) Boot from the USB HDD.

6) Clone the USB HDD OS and put into my .vdi.

7) Reboot from my internal HDD.

8)  Open VBox and the .vdi and there is the OS as a .vdi; to use, experiment with and break!

---

### Post by haqking on 2011-12-13
> **mikodo said:**
> So, if I understand correctly, I should do something like this:


1) Partition my internal HDD, to allow lots of space for the VM.

2) Mount VBox on the tree at /media, using a new partition of larger space, than my internal OS uses, or will be using.

3) Create a .vdi larger than my present OS.

4) Clone my internal HDD OS, onto my USB HDD.

5) Boot from the USB HDD.

6) Clone the USB HDD OS and put into my .vdi.

7) Reboot from my internal HDD.

8)  Open VBox and the .vdi and there is the OS as a .vdi; to use, experiment with and break!

not sure what you mean by mount on the tree at /media...anyways

Boot your machine to a clonezilla CD

Clone your existing OS to a destination ( i prefer external HDD, dont do it disk to disk unless you want to, just clone it to a file)

Create a VM with  settings to suit (.vdi larger than original preferable and i put my .vdi's on external too)

Boot VM to a CD or .iso of Clonezilla (enable HDD where clone file is from the devices menu)

And clone your clone into the VM

Done

---

### Post by JKyleOKC on 2011-12-13
> **mikodo said:**
> 1) Partition my internal HDD, to allow lots of space for the VM.

2) Mount VBox on the tree at /media, using a new partition of larger space, than my internal OS uses, or will be using.Just to make things a bit more clear, these two steps are not only unnecessary but would be counter-productive. The virtual disk is just that: virtual. It's actually a file inside of your host filesystem, not a separate partition.

The default installation of VirtualBox will create its VDI files in a subdirectory of your home directory. However it's not quite possible to create a virtual disk larger than your real disk if it's located inside of the real disk itself, so you need to modify the default creation point to be on a larger external drive. I'll leave the step-by-step instructions for doing that up to haqking, since I've never done it.

From step 3 on, it looks as if you have the idea.

The difference between a virtual disk (that's really just another file) and the real thing is a bit difficult to grok, initially, but you'll get used to it in a hurry.

---

### Post by mikodo on 2011-12-13
Thank you guys. 

I'll skip the first two steps.

Your hand-holding, is enough now, for this noobish-casual user hobbyist.

You have been great!

:D

[Reference Thread]("http://ubuntuforums.org/showthread.php?t=1892103")
[Reference Thread]("http://ubuntuforums.org/showthread.php?t=1891633")

---

### Post by haqking on 2011-12-13
> **mikodo said:**
> Thank you guys. 

I'll skip the first two steps.

Your hand-holding, is enough now, for this noobish-casual user hobbyist.

You have been great!

:D

you are welcome, good luck

---

