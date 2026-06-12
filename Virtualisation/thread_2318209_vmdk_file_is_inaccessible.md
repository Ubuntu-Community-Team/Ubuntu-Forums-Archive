---
title: "vmdk file is inaccessible"
date: 2016-03-23
forum: Virtualisation
---

### Post by josip6 on 2016-03-23
Hello . Pls can u help. We use on board ubuntu vb and since yesterday the vmdk file is inaccessible. There are 3 errors :
1.Could not open the medium (vmdk)
2. Error reading the magic nubmer (same vmkd file )
3.error VERR_VD_VMDK_INVALID_HEADER opening image file.

There are 4 partitions on our laptops bit this one is most important as all ships docs are stored here. Is there any way to solve thisnor at least ger the files from the inaccessible disk ??

---

### Post by deadflowr on 2016-03-23
Moved to the **Virtualisation** sub-forum.
(Forum feedback is for feedback on how the forum is working)

---

### Post by josip6 on 2016-03-24
Sorry for that :/ hoping someone will help us as we are in the middle of the ocean and all ships data is lost :(

---

### Post by MAFoElffen on 2016-03-24
Your description of the specifics of that image is a bit vague...

What format is the file system within that image file? 

What was on the VM disk image file? An OS with that data? If so, what OS? If data is what you are trying to access, stored in what format?

What Virtual Machine Hypervisor originally created it? That format was used by MS Virtual PC, VM Player, VirtualBox, etc... If originally created in VMware Player... then there are more options.

Have you ever successfully ran that disk image and when was the last time you ran it? Include details on what might have happened on the last VM shutdown... Fore instance if that shutdown was a save or suspend state... then there may be external conditions that may be affecting it's start.

Please explain your last post... which has got my curiosity going as being somewhat suspicious. Are you serious or kidding? Ship does not need data to float. navigation can be done by other means... Then what is the problem? Or is this from some crimal intent? That last post just raises a lot of flags.

If that was true, then you should have been taking snapshots and/or backups... Does the last copy of your backup of that file work? If you have no backup, then make a copy of that file before trying to recover it. 

*** That error message usually has to do with file corruption and the integrity of that image.

First check for errors on the physical disk that the image is located on. Then boot a VM without that disk mounted and test the filesystem of that unmounted VM disk to check for errors. That would required that you create a VM with that disk included, but not mounted.

---

