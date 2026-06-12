---
title: "ubuntu VM not working"
date: 2024-05-20
forum: Virtualisation
---

### Post by sreejith522 on 2024-05-20
Hi 

Ubuntu VM disk full after that i increase the size after reboot the VM 

Now its showing like 

error : no such partition 

entering the rescue mode

grub rescue > 


What i will no next

---

### Post by TheFu on 2024-05-20
What information do you think someone trying to help would need?  How about providing that?   

Don't make it hard for people to help, forcing them to be archeologists. 
We aren't there. 
We cannot read your mind.
We don't know your computer, OS, release, hypervisor, storage setup, for the host computer AND the VM.  Without that information, it is doubtful anyone can help.  Be exact. Don't be vague. Don't say "latest", since that isn't exact and has multiple meanings.

---

### Post by ajgreeny on 2024-05-20
Moved to Virtualisation which is a more appropriate site.

---

### Post by MAFoElffen on 2024-05-20
"Show Me The Data!"

Meaning-- Things you might add as info:

[LIST]
[*]What is the Host machine, with it's specs?
[*]What is the virtualization hosting software?
[*]What was the config of the Virtual Machine?
[*]What was the type of vDisk for that VM, and it's original size?
[*]How (exactly) did you try to resize the vDisk?
[*]Did you take snapshots or a backup before you tried to resize the vDisk?
[*]How was the Ubuntu VM setup?
[/LIST]

That last question, please expand on if it was BIOS Legacy or UEFI boot, normal OS partitions with ext4, with LVM2, or ZFS.

Just saying what you did say, there are so many variables of what it could be, saying anything would be a guess.

An easy way to do a quick fallback point for a vDisk, it to just make a copy of it, before you try to resize it, or when making changes to partitions. Things happen, when you least expect them. A vDisk (Virtual Disk) is just a file.

---

