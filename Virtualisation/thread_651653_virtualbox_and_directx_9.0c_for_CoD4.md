---
title: "virtualbox and directx 9.0c for CoD4"
date: 2007-12-27
forum: Virtualisation
---

### Post by rbprogrammer on 2007-12-27
ok, i installed virtualbox, and i wanted to install Call of Duty 4 so i dont have to switch into windows to play, and i installed that without a problem, but then when i go to run multiplayer mode, i get the error in the attachment.  some stupid directx 9.0c problem.  i installed CoD4 on windows and it works, but it wont work on virtualbox.

i'm a little baffled because the on the VM, everything is working.  graphics, sound, the internet, i just dont know why virtualbox has a problem with directx 9.0c.

does anyone know why this is happening? any help is appreciated.... :guitar:

---

### Post by oedipuss on 2007-12-27
I could be wrong, cause I haven't checked it in a while, but afaik virtualbox doesn't do 3d acceleration yet. I think vmware has some experimental support for direct 3d but it's only for up to version 8.

---

### Post by rbprogrammer on 2007-12-27
i'm no expert as well, but is it possible for virtualbox to allow the VM direct access to the graphics card??  i set the video memory to 128MB, so i dont know if it already accesses the graphics card or just uses memory from my main memory.

---

### Post by oedipuss on 2007-12-28
No I don't think it is allowed to access the card directly... see here : [http://www.virtualbox.org/discussion/1/615](http://www.virtualbox.org/discussion/1/615)

Your best bet would be trying to run Call of Duty with wine or cedega. From a quick look it seems to work with wine 0.9.49 and nvidia drivers 100.x (not newer) : [http://appdb.winehq.org/objectManager.php?sClass=version&iId=9699](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9699)

---

### Post by ahaslam on 2007-12-30
> **rbprogrammer said:**
> ok, i installed virtualbox, and i wanted to install Call of Duty 4 so i dont have to switch into windows to play, and i installed that without a problem, but then when i go to run multiplayer mode, i get the error in the attachment.  some stupid directx 9.0c problem.  i installed CoD4 on windows and it works, but it wont work on virtualbox.

i'm a little baffled because the on the VM, everything is working.  graphics, sound, the internet, i just dont know why virtualbox has a problem with directx 9.0c.

does anyone know why this is happening? any help is appreciated.... :guitar:

Sp works in VB :-k
It certainly works in wine, though PunkBuster can't be installed & the 1.4 patch wont apply. This obviously limits your multiplayer experience ;)

---

### Post by cmat on 2007-12-30
There is no support for 3D accelerated graphics on VirtualBox and its BETA still on VMWare. Its very difficult to do as this article explains [http://www.virtualbox.org/discussion/1/615](http://www.virtualbox.org/discussion/1/615). It was posted above but needs to be emphasized.

---

### Post by rbprogrammer on 2007-12-31
crap :( ... a virtual machine is much more complicated than what i had originally thought..

---

### Post by ahaslam on 2008-01-01
> **ahaslam said:**
> Sp works in VB :-k
It certainly works in wine, though PunkBuster can't be installed & the 1.4 patch wont apply. This obviously limits your multiplayer experience ;)

Seems irrelevant, MP still works ;)

---

### Post by rbprogrammer on 2008-01-01
> **ahaslam said:**
> Seems irrelevant, MP still works ;)
what do you mean multiplayer still works?? mine doesnt :confused:

---

### Post by rcmn on 2008-01-01
try Playonlinux [http://www.playonlinux.com/en/](http://www.playonlinux.com/en/) .
Very good to deal with scripts wroe for wine and the differente version of wine.
In the program you can pic the version of wine that fit the best your needs by using Tools=> mange wine version => install  then tools => manage wine version => assigned

---

### Post by rbprogrammer on 2008-01-01
at the risk of getting scolded for possibly posting in the wrong section.. would cedega work with directx 9.0c and 3D acceleration??

oh and
> **rcmn said:**
> try Playonlinux [http://www.playonlinux.com/en/](http://www.playonlinux.com/en/) .
Very good to deal with scripts wroe for wine and the differente version of wine.
In the program you can pic the version of wine that fit the best your needs by using Tools=> mange wine version => install  then tools => manage wine version => assigned
i did not try wine b/c CoD4 was not in their repository of apps that work.  and for some reason, i have never gotten any windows program to work in wine except for notepad and minesweeper..

---

### Post by ahaslam on 2008-01-02
This'll help: [http://ubuntuforums.org/showpost.php?p=4047498&postcount=13](http://ubuntuforums.org/showpost.php?p=4047498&postcount=13)

It really works a treat in Wine ;)

---

### Post by zekopeko on 2008-01-02
somewhere in 2008/2009(?) AMD is planing to bring direct hardware virtualization. that means that the VM will have direct access to the hardware so playing games on VM's will be possible.

---

### Post by jaygo on 2008-01-03
Good to hear. As I understand it, virtualization was developed in the server market and was not very interested in 3d graphics. Now that we desktop users are getting into it, the interest (read pressure) will build until we get it. 

I *believe* that right now, one can use Xen on a linux host, and create a windows guest to get 3d acceleration *if* they have an ATI card. To get 3d acceleration with nvidia's closed drivers you have to recompile your kernel with it, and apparently it's not easy to recompile your kernel for both Xen & nvidia at the same time. With ATI's open source drivers, we might be able to (more easily) compile for Xen and 3d acceleration. Ya think?

---

### Post by cmat on 2008-01-04
For DirectX 9.0c on WINE you can try this. [http://wine-review.blogspot.com/2007/11/directx-90c-on-linux-with-wine.html](http://wine-review.blogspot.com/2007/11/directx-90c-on-linux-with-wine.html)

It works for me and I was able to run most games perfectly. However you need to still use the D3D8 and D3D9 provided with WINE for certain applications.

As for 3D on VMs, who knows maybe Microsoft will come out with a version of DirectX for VMs or video card developers will drivers developed to be run from inside VMs.

---

### Post by rbprogrammer on 2008-01-06
> **cmat said:**
> 
...
As for 3D on VMs, who knows maybe Microsoft will come out with a version of DirectX for VMs ...

lol, thats funny...

---

### Post by RobertMillan on 2009-02-04
> **rbprogrammer said:**
> i'm a little baffled because the on the VM, everything is working.  graphics, sound, the internet, i just dont know why virtualbox has a problem with directx 9.0c.

This is still very experimental, but you can get Direct3D support on VirtualBox now, using WineD3D. See:

[http://aybabtu.com/rmh/wined3d/](http://aybabtu.com/rmh/wined3d/)

[http://www.virtualbox.org/ticket/2940](http://www.virtualbox.org/ticket/2940)

However it's only known to work for testcases and simple apps so far.

---

