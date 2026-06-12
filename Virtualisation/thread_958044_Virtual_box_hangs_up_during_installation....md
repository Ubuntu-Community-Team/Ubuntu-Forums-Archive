---
title: "Virtual box hangs up during installation...??"
date: 2008-10-25
forum: Virtualisation
---

### Post by faraz_k86 on 2008-10-25
I installed VB and then tried to install Win XP.

I gave a ram size of 512 and Virtual disk space of 8 GB. 

I then started the machine, setup went fine till it reaches the partitioner option.

the place where it tells u that partition 1 of 8GB is raw and you must format it to another file system like FAT or NTFS.

this is where it hangs up. during formatting the system just freezes.

i tried both FAT and NTFS, same results.

any help r ideas will be greatly appreciated

---

### Post by faraz_k86 on 2008-10-25
bump :)

---

### Post by faraz_k86 on 2008-10-25
and.....another bump.

sorry.. :)

---

### Post by Duck2006 on 2008-10-25
This may help.

[http://ubuntuforums.org/showthread.php?t=690713&page=2](http://ubuntuforums.org/showthread.php?t=690713&page=2)

---

### Post by bodhi.zazen on 2008-10-25
The virtual drive is very much a raw drive, it has no partition table, like a new clean hard drive.

Easiest is to boot the system with an Ubuntu iso and use gparted to make a NTFS partition. Then re-boot to and install Windows.

---

### Post by faraz_k86 on 2008-10-25
Thanks but i dont see how that link you provided can help me. 

Creating an NTFS partition with GPARTED? then that wont be a virtual drive and i dont think VB will be able to pick it up.

---

### Post by faraz_k86 on 2008-10-25
k i found the answer.

this guy had the same problem: [http://www.virtualbox.org/ticket/589](http://www.virtualbox.org/ticket/589)

I was assigning more virtual memory than my actual ram. That is why my partitioner got an error

---

### Post by bodhi.zazen on 2008-10-25
> **faraz_k86 said:**
> Thanks but i dont see how that link you provided can help me. 

Creating an NTFS partition with GPARTED? then that wont be a virtual drive and i dont think VB will be able to pick it up.

LOL

Yes you boot your virtual machine with the Ubuntu iso as a cdrom and format the virtual drive as NTFS.

Anyways, I am glad you found a solution.

---

