---
title: "pw protected external HDD cant open"
date: 2011-10-16
forum: Security
---

### Post by ubuntolover2000 on 2011-10-16
Hello Guys,

I have an WD external HDD (1TB capacity)in which I saved many movies.  I keep this drive password protected.

After installation of ubuntu in my new pc, when I connect this HDD to the pc, an icon named 'unblocker' comes in the desktop.  clicking it opens the 'unblocker' folder, but not the hdd itself. after many attempts i cannot understand how and where to write the pw so that i can open the drive and access the movies in it.

any light on this will be greatly appreciated. 

ubuntolover

---

### Post by Monery on 2011-10-16
I've not seen this problem not with Linux, If its the same problem but with moving one of thse HDD's to a Mac. 
 
What your most likely experiencing is the 'password' program is designed to work with the Windows OS. To my knowledge, the only way to fix this and make the external drive work across platforms would be to first back up your data, delete the all the partitions on the drive (there should be two of them) and create a regular a single NTFS partition, format it, and then copy your data back over.
 
This of course will forever delete the password protection features of the software on the drive. As as far as I know its the only way to solve your problem.
 
Might want to wait for some more replies before taking this action cause again it is only a guess

---

### Post by lovbuntu on 2011-10-16
> **ubuntolover2000 said:**
> Hello Guys,

I have an WD external HDD (1TB capacity)in which I saved many movies.  I keep this drive password protected.

After installation of ubuntu in my new pc, when I connect this HDD to the pc, an icon named 'unblocker' comes in the desktop.  clicking it opens the 'unblocker' folder, but not the hdd itself. after many attempts i cannot understand how and where to write the pw so that i can open the drive and access the movies in it.

any light on this will be greatly appreciated. 

ubuntolover

When you say password, you mean encryption?

---

### Post by Monery on 2011-10-16
> **lovbuntu said:**
> When you say password, you mean encryption?
 
some WD drives are sold with two partitions. The first to mount has a Windows Autorun that launches a program that requires you to enter a password to mount the actual storage partition. Its not really that secure due to the fact that you do some simple hacking to mount the 2nd partition with a Linux boot disc, UBCD tool that gives you a Windows Pre Enviroment (PE) and a few other tricks
 
This is assuming of course that I am correct about my theory with his problem

---

