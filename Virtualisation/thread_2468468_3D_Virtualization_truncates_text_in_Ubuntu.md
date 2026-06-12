---
title: "3D Virtualization truncates text in Ubuntu"
date: 2021-10-30
forum: Virtualisation
---

### Post by vo-nguyen on 2021-10-30
I need 3D virtualization, but it truncates the text in the system menus and apps. I am running Virtualbox Version 6.1.28 r147628 (Qt5.6.3).

---

### Post by QIII on 2021-10-30
3D acceleration in VirtualBox is currently experimental and you would need a suitable GPU dedicated to the guest to use it without robbing your host of graphics even if it were complete.  In the many-years-old-and-still-unrealized experimental environment, it is not even guaranteed that your VM would be able to take full advantage of any particular GPU's bare metal capabilities.

---

### Post by lammert-nijhof on 2021-11-25
I use 3D acceleration for all my modern Virtualbox VMs and that includes Windows XP till Windows 11 and around 40 modern Linux VMs. Virtualbox 3D acceleration is NOT experimental, that is many years ago. The forum admin seems to confuse 3D acceleration with GPU pass through. 

If you want a more useful reply you have at least to specify, which menu one in the VM or the Virtualbox menu itself. If it is not the virtualbox menu, we also need to know which OS you use in that VM. Is it a Windows VM or a Linux Distro and which release. I don't have your problem with any of my ~70 VMs.

---

### Post by lammert-nijhof on 2021-11-25
?

---

### Post by MAFoElffen on 2021-11-26
> **lammert-nijhof said:**
> ?

By this post... What answer were "you looking for? From who? With the personal experiences you shared, you could have addressed the OP and tried to help him right(?) 

Regardless... I think something got distracted from, and where does leave the OP? Remember?

 > **vo-nguyen said:**
> I need 3D virtualization, but it truncates the  text in the system menus and apps. I am running Virtualbox Version  6.1.28 r147628 (Qt5.6.3).

I see this as somewhat unanswered... I am sort of embarrassed how this was handled and left. It sort of got sidetracked... And now be too late. The OP may have abandoned this and may not be around anymore to get a solution.

Questions remain. Such as:

Is 3D virtualization in VBox working on his system?

If so, is something not working correctly where the display of his guest not displaying correctly, where it is truncating the display of his menus the the text in his applications?

I'm still curious about this...

---

### Post by lammert-nijhof on 2021-11-26
> **MAFoElffen said:**
> By this post... What answer were "you looking for? From who? 
 The post with "?".  I was just looking for a way to delete this post.

> **MAFoElffen said:**
>  Is 3D virtualization in VBox working on his system?
If so, is something not working correctly where the display of his guest  not displaying correctly, where it is truncating the display of his  menus the the text in his applications?
I'm still curious about this...
The whole problem started  with the first bad and uninformed reply. There is no problem with Virtualbox and 3D  acceleration! I know because,  I use Virtualbox since 2010 and I run at least 20 Linux distros and all  Windows releases since Windows 2000 in a VM using 3D acceleration.
There  might be problems if you try to force it on old OS not supporting the  Virtualbox Guest Additions e.g Windows 95 or Ubuntu 6.06. 
But first we have to know, which OS is used in the VM.

---

### Post by MAFoElffen on 2021-11-27
It works for you on your hardware and your VirtualBox configuration. That does not mean it works for all hardware combinations and all configurations. If so, then there would be no need for bug reports, nor updates/release upgrades, right? 'Things' happen when you least expect it. Most usually when Linux Kernel updates vary beyond a certain point.  

There is many combinations where 3D Acceleration will fail. It is not bullet proof. Sometimes it is caused by the User themselves, but 'changing' things... Sometimes with permissions or graphics problems in the Host. Sometimes just out of nowhere apparent. 

That is just life and reality. Things happen.

About deleting posts... I can relate. i have not found any way to delete a post here. Only to edit it to something like "Post Content Deleted"... or similar. LOL. Or "OOP's"... Especially sometimes when it hiccup's and sometimes generates a double/duplicate post.

---

### Post by lammert-nijhof on 2021-11-29
The problem has not been the experimental state of 3D acceleration as stated in the first reply. That experimental state was years ago! So one of the first things I had to do, was proofing that 3D acceleration was mature and did work.
Of course it does not work everywhere under all circumstances, that is why you have to ask for more specific information and that is what I did.

---

