---
title: "Possible to boot native windows 7 from within virtualbox?"
date: 2010-01-07
forum: Virtualisation
---

### Post by josephellengar on 2010-01-07
Sorry if this question has been asked before.  I've done some googling around and wasn't able to find the answer.  I have a dual boot system, with Windows 7 and Ubuntu.  I was wondering if it is possible to boot that Windows 7 installation via virtualbox from within Ubuntu.  You know, for convenience and all.  Thank you!

---

### Post by lmarmisa on 2010-01-07
I have serious doubts but I propose a procedure to try it. 

Try to make a backup of your W7 partitions (probably 2) using, for example, the program [http://www.clonezilla.org](http://www.clonezilla.org). 

Next steps are run in VirtualBox. 

Create a dinamically expanding virtual disk greater that the sum of the W7 partitions (maybe you will need an Ubuntu additional OS; if so, add 10G to the size of the W7 partitions). 

Start the VM with an Ubuntu Live CD iso file and define with GParted the W7 partitions for your virtual disk. Then restore the backups using Clonezilla.

Now, you will have the two partitions of Windows 7 cloned in your virtual disk but you will be unable to start W7 because you will need a grub loader for that purpose (remember that grub is the loader in your dual boot system). 

So, you can install a new Ubuntu in the virtual disk in order to add a grub loader to the disk. 

Other possibility is to use the virtual disk as second disk of other VM with Ubuntu (you will need to update grub for the recognition of Windows 7).

The final result could be a failure (quite probable), but you can try it if you wish.

A simpler solution would be to backup the whole physical hard drive (Ubuntu + Windows 7) and restore it in a dynamic virtual disk using Clonezilla.

Best regards,

Luis

---

### Post by meierfra. on 2010-01-07
[http://ubuntuforums.org/showthread.php?t=984437]("http://ubuntuforums.org/showthread.php?t=984437")

---

### Post by josephellengar on 2010-01-08
> **meierfra. said:**
> [http://ubuntuforums.org/showthread.php?t=984437]("http://ubuntuforums.org/showthread.php?t=984437")

Thanks!

And to the person who suggested the method above.

---

