---
title: "VirtualBox: How to recover HDD space?"
date: 2013-11-12
forum: Virtualisation
---

### Post by Jeff_Berrian on 2013-11-12
My VM's are saved in /home and take up several GB's per VM from about 1Gb to 4Gb on avg. My /home partition is a minimal fixed size so available space is scarce. I've deleted some extraneous VM's (Move to Trash) and the space in /home is not freed up as if the file still exists and is taking up space. I figure the 4Gb VM went into the trash but the trash can is empty (?)

I check my available disc space using df -h in terminal and can see that the expected available HDD space % of /home is still the same as if (again) the file has not been properly deleted.

Question: How do I recover the available space when deleted large files like a 4Gb VM?

---

### Post by ayenack on 2013-11-13
Did you use Virtual Box to delete the virtual Hard Drives of the VM's you deleted?

---

### Post by ajeebkp23 on 2013-11-13
Usually Virtual HDD file with extensions *.vhd, *.vmdk, *.vdi etc. have higher sizes..

:P

---

### Post by TheFu on 2013-11-15
Did you use a file manager?  If so, could it have moved the file to the "trash" and not really deleted it?

---

