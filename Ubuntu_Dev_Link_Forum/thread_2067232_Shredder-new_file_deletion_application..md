---
title: "Shredder-new file deletion application."
date: 2012-10-06
forum: Ubuntu Dev Link Forum
---

### Post by MG&amp;TL on 2012-10-06
I've been working on this project for a while with a friend, but it's just about ready for a first release, so I thought I'd post it here and get some response/critique. Mods: feel free to move this!

**Shredder**

Premise:

You need to securely delete some files, but you know (if you don't, you jolly well should!) that the data is still on the disk until it is overwritten. You don't really want to overwrite the entire disk, however.

Solution:

Overwrite files with random data again and again, so no data is left. This is what programs like *shred* and *srm* do. However, you're not really a CLI person. So we came up with shredder, which scrubs files with random data, then removes them from the filesystem table if wished, all through a nice GUI frontend.


Sound good? Well, there is a zipped 64-bit .deb installer attached (sorry to those on 32-bit, I haven't got a 32-bit box to build on), as well as a source tarball (*typical installation: make, then sudo make install)*

Limitations/Disclaimer:

Many filesystems can and do keep fragments, copies, and  snapshots of files, so we can't guarantee that your file will be gone. If you really want something gone forever, I suggest something along the lines of Darik's Boot And Nuke, to completely wipe the disk.


If you want to help with this project, drop me a [EMAIL="michael.rawson@ubuntu.com"]line,[/EMAIL] and I'll give you instructions and/or encouragement. You'll also get a line in the about box. :)

---

### Post by SuperFreak on 2012-10-06
Thanks, It looks useful.
I tried to shred some hidden files but I am not sure how to use your program to add hidden files. Would it be possible to have Shredder as an option when you right click files?

---

### Post by hakermania on 2012-10-06
Nice :) It works fine here. Pardon me for taking action and compiling it for 32-bit version (quite improvised because I was missing your debian folder, but the deb installs and runs just fine)

32-bit Deb attached.

---

### Post by SuperFreak on 2012-10-06
I see it is possible to drag files into Shredder which solves my issue with Hidden files.

---

### Post by MG&amp;TL on 2012-10-06
> **SuperFreak said:**
> Thanks, It looks useful.
I tried to shred some hidden files but I am not sure how to use your program to add hidden files. Would it be possible to have Shredder as an option when you right click files?

Well, you solved it for yourself, but you can press Ctrl-H while in the file browser. :)

> **hakermania said:**
> Nice :) It works fine here. Pardon me for taking action and compiling it for 32-bit version (quite improvised because I was missing your debian folder, but the deb installs and runs just fine)

32-bit Deb attached.

Thanks! Duh, I should have attached the zipped debian folder, but you seem to have managed okay. :)

> **SuperFreak said:**
> I see it is possible to drag files into Shredder which solves my issue with Hidden files.

:)

---

### Post by glad581 on 2012-10-08
I have a copy file shredder tool called Kernel for File Shredder, It completely delete files so that even a data recovery tool is not able to find a trace of the file. You can choose the algorithm according to which you want to shred files.

---

### Post by MG&amp;TL on 2012-10-08
> **glad581 said:**
> I have a copy file shredder tool called Kernel for File Shredder, It completely delete files so that even a data recovery tool is not able to find a trace of the file. You can choose the algorithm according to which you want to shred files.

Maybe we can collaborate?

I find it unlikely that "even a data recovery tool" can't find the data-shredder makes it extremely difficult, but if you use a filesystem like Btrfs, it takes snapshots anyway. Are you using the kernel to directly manipulate the filesystem?

EDIT: Unless mistaken, you're referring to this one: [http://www.nucleustechnologies.com/kernel-file-shredder.html]("http://www.nucleustechnologies.com/kernel-file-shredder.html")  -  it's a Windows application. :(

---

