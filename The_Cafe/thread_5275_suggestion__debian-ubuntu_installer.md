---
title: "suggestion : debian-ubuntu installer"
date: 2004-11-17
forum: The Cafe
---

### Post by ljoris on 2004-11-17
Would it be possible to add a main-menu option to re-install one of the kernel-images without having to pass by the whole installation sequence. In itself it might sound trivial but it would be a great way to make a quick-n-dirty rescue of a system. 

Also, an option to do a filesystem-checkup on non-mounted filesystem is more then missing (also a recueish thing).

Moreover, when using 2 cdrom drives it is not possible to use just any drive, the installer only uses the first drive on the primary-ide-bus.

I hope this was the right forum to post this.



Joris

---

### Post by TravisNewman on 2004-11-17
[QUOTE=ljoris]Would it be possible to add a main-menu option to re-install one of the kernel-images without having to pass by the whole installation sequence. In itself it might sound trivial but it would be a great way to make a quick-n-dirty rescue of a system. 

Also, an option to do a filesystem-checkup on non-mounted filesystem is more then missing (also a recueish thing).

Moreover, when using 2 cdrom drives it is not possible to use just any drive, the installer only uses the first drive on the primary-ide-bus.

I hope this was the right forum to post this.



Joris[/QUOTE]
 Last night wasn't weird for me, but that one most closely represented the way I feel. I'd like to see a rescue boot option that lets you do things like that, though only if it didn't drive it over the 1 cd limit.

BTW, moved this to Community Chat since it's not a support request.

---

### Post by zenwhen on 2004-11-17
I think it would be nice to be able to install grub and a kernel from the disk without doing the rest as well. It would make the install disk a perfect rescue disk.

---

### Post by ljoris on 2004-11-18
[QUOTE=zenwhen]I think it would be nice to be able to install grub and a kernel from the disk without doing the rest as well. It would make the install disk a perfect rescue disk.[/QUOTE]


Well, i'm happy this idea seems to catch on allready :-)

Indeed : just the option of re-installing one of the boot-kernels supplied on the ubuntu cd would be such a rescue allready. In fact it does concern me quite a lot, the rescue-part has been mostly abandoned since debian-sarge/sid or especially the new debian-installer project. I've been on-and-off with Debian since 0.99b was realesed on ct magazine very long years ago, i often use woody-cd-s as rescue disk just because they supply this option, wich is a viable promotional reason as well ...

Furthermore : being able to chroot your harddisk filesystem would also be so great. At least a couple of time I've ran into the stupifying experience of building a new kernel and installing it just to see it's not working and lilo doesn't wait to boot it.

Both option seem to be both diserable and usable.


Best Regards,

Joris

---

