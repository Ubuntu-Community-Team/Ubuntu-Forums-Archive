---
title: "Booting Live USB Error (Secure Boot Not Enabled)"
date: 2013-02-08
forum: Ubuntu Studio
---

### Post by CaptainMikeRak on 2013-02-08
I am using a Lenovo Ideapad U400 series notebook that has been upgraded to Windows 8 Pro (64-Bit). I am really sick of Windows 8 so I want to duel boot my system. So what do you suppose happens? I make all backups and get everything ready, just to get a message that says "Secure Boot Not Enabled" and I can't start my USB Live CD for Ubuntu Studio. I know how to install Ubuntu Studio (and most Linux systems) but I can't get there with this error. Somebody please put instructions here so I can finally use something other than Windows 8 (aka The Problem). I looked this issue up and it may have something to do with the Windows 8 Bootloader, but I can't get it to work properly. I have one solution that would fix both my problems at once, but it's very risky. I can use VirtualBox to make a Windows 7 Professioanl Machiene that duel boots with Ubuntu Studio as a second OS. Then I can use Windows to make a system image then write that image to my HDD. would rather not do this as I can't guarantee that it would work. I really need any (within reason) solution that would fix this so I can install Ubuntu Studio.

---

### Post by CaptainMikeRak on 2013-02-11
Also, if there is anyway to ensure that the re-imaging method would work, please leave a comment.

---

### Post by CaptainMikeRak on 2013-02-19
Seriously, I can't be the only on that is having or had this issue.

---

### Post by jejeman on 2013-02-19
Is this issue only related to Ubuntu Studio? Or it affects all Ubuntu variants?
If it does, someone should move this question on more general ubuntu help subforum. Here, we mostly deal with audio and ubuntu studio specific stuff.

---

### Post by CaptainMikeRak on 2013-02-19
This seems to apply to other Ubuntu distributions but I'm not a hundred percent sure. I believe it's a Windows 8 issue or a issue with certain hardware platforms. I don't believe its a BIOS issue but rather the Windows boot-loader intercepting the signal to boot from the USB CD.

---

### Post by CaptainMikeRak on 2013-03-04
I found out the cause: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

