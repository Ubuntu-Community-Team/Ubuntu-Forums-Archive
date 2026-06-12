---
title: "[Idea] Multiple Linux installations on one partition"
date: 2011-05-25
forum: The Cafe
---

### Post by Blutkoete on 2011-05-25
Hello!

I don't know where to put this (it's not a support question), it's just an idea.

Why can't every Linux distribution I use install itself with kind of a folder name space? E.g. for "/"
[INDENT]/boot
/Ubuntu10.10
/Ubuntu11.04
/Lubuntu11.04
/Fedora14
[/INDENT]That should - of course or if not stated otherwise for systems that know they can share kernels - also apply for the kernels in the boot folder.

Allowing this won't hurt multi-partition-booters (they could still do that), but it'll allow others much more flexibility regarding the sharing of programs. Or make repairs easier. The only problem I see is a corrupted file system (which would kill every OS on that partition), which never happened to me. The advantages would be:
[INDENT]- No need for partition resizing when you realize you use system x more than system y
- No need for mounting to access files and programs
- Uninstall an OS with the "rm" command
...
[/INDENT]This is just an idea and I don't know how many problems something like that might produce, so what do you think?

---

### Post by Barrucadu on 2011-05-25
The obvious disadvantage is that programs from one distro can mess with the files from another. If you run a malicious script, it could do significantly more damage (ie: break every OS you have installed) than if you used separate partitions (assuming they're not all mounted permanently).

---

### Post by 3Miro on 2011-05-25
This can be done, but I am not sure it will be practical. It is a lot of work to add the prefixes for everything.

What I do is I have a large HDD (500GB) divided into 8 partitions and I use 6 of them for various Linux installations. I can delete an installation with a simple format command. Adding an installation is also easy, just point the installer to the desired partition. Also, I can have special scripts that know something is always in /media/wine and not /Ubuntu1010/media/wine or /Fedora14/media/wine.

---

### Post by aeiah on 2011-05-25
you could do this with openvz if you wanted [http://wiki.openvz.org/X_inside_VE#Desktop](http://wiki.openvz.org/X_inside_VE#Desktop)

but that would of course require a hypervisor.

---

