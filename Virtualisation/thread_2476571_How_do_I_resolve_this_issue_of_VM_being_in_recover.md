---
title: "How do I resolve this issue of VM being in recovery mode and clearing orphaned nodes"
date: 2022-06-29
forum: Virtualisation
---

### Post by jthedev on 2022-06-29
I recently exported my ubuntu 20.04 to import into a different machine. when starting up it loads ubuntu 22.04 and then says recovering journal, clearing orphaned inode 3028979. Sometimes the vm loads up, but then it freezes, Sometimes it freezes after I enter the pw, sometimes it works and pulls up my GUI but then once I start working in the VM environment it freezes. It cannot sustain any work I try to perform. I am a VERY NEW developer, still figuring this out and teaching myself. It is difficult to figure this out, there is so much information on the internet. I opened up the Grub menu and went to advance options. Here there are two recovery modes. Which one do I pick? Am I even going in the right direction. This is what my advanced options have for recovery mode: *ubuntu, with linux 5.15.0-33-generic ubuntu, with linux 5.15.0-33-generic (recovery mode) ubuntu, with linux 5.15.0-30-generic ubuntu, with linux 5.15.0-30-generic (recovery mode)
This is what my startup screen says before it prompts me to enter password: recovering journal clearing orphaned inode 3028979 (uid=127, gid=133, mode=0100600, size =64) clean, 301456/6569984 files, 5096693/26266624 blocks
FYI: In regards to my host machine, I am using a 11th gen i7, 64-bit operating system.

[https://ubuntuforums.org/attachment.php?attachmentid=290677&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=290677&stc=1)
[https://ubuntuforums.org/attachment.php?attachmentid=290678&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=290678&stc=1)

---

### Post by TheFu on 2022-06-30
Please avoid posting pictures of text when possible. The grub boot screen is one you probably couldn't get any other way.

It appears, with no extra information provided, that the VM file system wasn't copied cleanly.  This could be due to 50 different issues and may have happened on either side of the copy.

Which hypervisor is being used?  What management layer?
How is the storage setup on both sides?
If you are typing in a password, is the storage encrypted, somehow?  If so, what encryption is being used?

How is starting a 20.04 system running 22.04?  You've lost me there, completely.  Perhaps the storage the hypervisor is configured to use is wrong?  If the hypervisor expects 20.04 and you've provide 22.04, then underlying virtual hardware can be configured different and may be breaking.


BTW, I expect a moderator will relocate this thread to the Virtualization sub-forum, since it is clear that is the primary issue.  Most users here don't really use virtualization.

---

### Post by ajgreeny on 2022-06-30
*Thread moved to **Virtualisation**.* which is more appropriate and a better fit.

Please give as much detail as you can; which hypervisor and also exactly what you mean when you say 
"I recently exported my ubuntu 20.04 to import into a different machine. when starting up it loads ubuntu 22.04 and then says recovering journal, clearing orphaned inode 3028979."
which makes no real sense.

If you exported and then imported 20.04 how can it possibly boot to 22.04?

---

