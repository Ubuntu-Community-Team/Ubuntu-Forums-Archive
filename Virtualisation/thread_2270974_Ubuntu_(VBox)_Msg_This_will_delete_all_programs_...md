---
title: "Ubuntu (VBox) Msg: This will delete all programs ... in all other operating systems"
date: 2015-03-26
forum: Virtualisation
---

### Post by steve199 on 2015-03-26
I am installing Ububtu in VirtualBox on Windows 7 and I get the message after clicking Install Now button:


This computer has detected no other operating systems.
Erase disk and Install Ubuntu; (checked)
Warning: This will delete all your programs, documents, photos, music, and any other files in any operating system.

I am running VirtualBox and Ubuntu in a Windows 7 environment.

Does the above msg apply only to other operating systems in VirtualBox? 0r will it harm my underlying W7 system?

Thanks
Steve

---

### Post by ajgreeny on 2015-03-26
It is probably telling you that the whole of the virtual disk you have just made in VBox will be erased and used for Ubuntu, just as you want, I would imagine, though without more info it is difficult to know exactly what you saw.  It should not have any effect on the hard disk of the host OS, only on the newly made virtual disk, neither should it do anything to any other virtually installed OSs, if you have others

When I install an OS in VBox, and I have six separate VMs installed in my Xubuntu host, that message you are querying has always said how big the virtual disk is, ie 8GB if you have accepted the defaults,  which should give you a clue about whether or not it is the correct disk being mentioned.

---

### Post by oldos2er on 2015-03-26
Moved to Virtualisation.

---

### Post by slickymaster on 2015-03-26
> **ajgreeny said:**
> It is probably telling you that the whole of the virtual disk you have just made in VBox will be erased and used for Ubuntu, just as you want, I would imagine, though without more info it is difficult to know exactly what you saw.  It should not have any effect on the hard disk of the host OS, only on the newly made virtual disk, neither should it do anything to any other virtually installed OSs, if you have others

<---snip--->

This ^^^

---

### Post by TheFu on 2015-03-28
> **slickymaster said:**
> This ^^^

That ^^^^  
Aj nailed it.  Relax.  It is only about the virtual disk and it is impossible for someone new to accidentally connect to the real Win7 hard disk. 

BTW - since it only takes 10-15 min to load Ubuntu - practice doing the install a few times.  Each install only needs 10G of disk - not really a big commitment for 1-6TB disks these days.

---

