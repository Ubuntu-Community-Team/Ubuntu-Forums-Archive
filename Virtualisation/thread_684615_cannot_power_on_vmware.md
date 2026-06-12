---
title: "cannot power on vmware"
date: 2008-02-01
forum: Virtualisation
---

### Post by almoravid on 2008-02-01
I want to install windows using vmware. I create a virtual hd n then I want to power on the machine so that I can run the windows setup but then the machine cannot be power on.

---

### Post by emarkd on 2008-02-01
You'll have to make VMWare boot your XP CD, not your new, empty virtual disk.  Do you get an error message that would point us in a direction?

---

### Post by almoravid on 2008-02-01
I didnt get any error message. It just I click on power on but nothing happen

---

### Post by santiump on 2008-02-01
I'm having the same problem. I installed vmware, created a VM, but when start it, it just shuts down. The only time it showed an error message it was: 
```
Unable to connect to the MKS: Pipe: Read failed.
```


But that was just once, all the other times it powered off silently.

---

### Post by Mach1US on 2008-02-16
I'm actually even more puzzeled, i have created vmware machines in feisty ,they have been working great and they work withot a problem in XP but when i try to open it in newly installed gutsy it just dies, even before the VMware logo appears just closees.
I too getting this message:
```
Unable to connect to the MKS: Pipe: Read failed.
``` 
Hope someone knows what is happening with gutsy.

---

### Post by nymusicman on 2008-02-17
I'm having this problem too. Are there any answers out there for it?

---

### Post by Mach1US on 2008-02-17
Update.
So far i found out that it must have something to do wiyh file systems because i was finally able to boot VM-machine (the one that was giving me that message before) after i formatted one of my external HD's to Ext3 file system and copied this VM-machine from my NTFS partition to this external HD.
Works as designed, i can move it between different Linux boxes but i havn't tried to power it on from XP machine being  the host OS.
If you'll find any more on the subject please post it here too.

---

### Post by zhangxi1982 on 2008-02-18
I have the same problem, and solve it the same way.
when the guest system is on an ntfs Hd partition, it can't be powered on
I move it to a fat32 partition,  it works OK

---

### Post by viktara on 2008-02-20
According to the ntfs-3g website this problem is caused by the way vmware uses ntfs:

Fortunately there is a workaround:
Set "mainMem.useNamedFile=FALSE" in the .vmx file

See here for more info:
[http://www.ntfs-3g.org/support.html#vmware](http://www.ntfs-3g.org/support.html#vmware)

My VM boots fine from the NTFS partition after doing this.

---

### Post by benizi on 2008-02-28
This also worked for me while running VMWare on a ZFS partition. (for the benefit of anyone googling this.)

Thanks,
benizi

---

### Post by fjgaude on 2008-02-28
> **viktara said:**
> According to the ntfs-3g website this problem is caused by the way vmware uses ntfs:

Fortunately there is a workaround:
Set "mainMem.useNamedFile=FALSE" in the .vmx file

See here for more info:
[http://www.ntfs-3g.org/support.html#vmware](http://www.ntfs-3g.org/support.html#vmware)

My VM boots fine from the NTFS partition after doing this.

This addition to the .vmx in a WinXP guest situation seems to improve the overall quickness. Thanks viktara for pointing this out to us.

---

### Post by gabr10 on 2008-04-22
Confirmed working after adding the line "mainMem.useNamedFile=FALSE" (without the quotes) to the vmx file.

Thanks for the workaround!

---

### Post by fjgaude on 2008-04-22
It's amazing how little things help. Each day we learn something new, eh?

---

### Post by rthiengo on 2009-08-08
Adding this line to the .vmx file makes everything works fine.
Well, I had to fix some configurations about each vm but everything is ok now.
 
Thanks a lot!

---

