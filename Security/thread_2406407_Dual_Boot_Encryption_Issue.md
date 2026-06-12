---
title: "Dual Boot Encryption Issue"
date: 2018-11-20
forum: Security
---

### Post by lksjfnvljnfdv on 2018-11-20
So i have 3 SSDs in my laptop. 2x m2.ssd (A,B) and 1x normal ssd used for storage(C)
lets call them A, B and C
SSD B already has windows 10 pro installed with bitlocker, taking up the whole SSD, disable bitlocker so i can install Ubuntu LUKS on the other SSD.
I removed SSD B and C from the laptop and installed Ubuntu on SSD A with LUKS, all is good and boots fine.
Put SSD 2 back in and sort out the boot options and stuff and get GRUB to detect everything, all is still ok and i can boot into the Windows OS.
Now i enabled bitlocker and encrypted , choose Windows from the GRUB menu , but it keeps asking for the recover key on each boot. I put the recovery key in and windows loads, but i dont want to have to use the recovery key each time.
Tried suspending bitlocker and it boots into GRUB lets me choose the OS, i choose Linux i can boot into LUKS screen on, when i try with bitlocker suspended it work again without issue.
When bitlocker is enabled again it asks for recovery key again.
How can i get the GRUB to let me choose the OS at boot time and stop windows from throwing a fit about the recovery key on each boot?
What have i missed here?

---

