---
title: "looking for rebootless kernel patch solution"
date: 2012-05-14
forum: Server Platforms
---

### Post by buffchick on 2012-05-14
I'm looking for a rebootless kernel patch solution for ubuntu server 10.04. I can't get ksplice to work now that they're only supporting ubuntu desktop. I've been through about 3 dozen articles and can't find any way to do. Is there any other viable option?

---

### Post by Gyokuro on 2012-05-14
With kexec you should get what you want ([http://manpages.ubuntu.com/manpages/precise/man8/kexec.8.html](http://manpages.ubuntu.com/manpages/precise/man8/kexec.8.html)) - ksplice is an good example why someone should avoid non in-kernel extensions (thanks goes to Oracle).

---

### Post by roelforg on 2012-05-14
> **Gyokuro said:**
> With kexec you should get what you want ([http://manpages.ubuntu.com/manpages/precise/man8/kexec.8.html](http://manpages.ubuntu.com/manpages/precise/man8/kexec.8.html)) - ksplice is an good example why someone should avoid non in-kernel extensions (thanks goes to Oracle).

+1

Once made a cd that boots a linux kernel with initrd, loads kmods to read cd and aufs, mounted an aufs consisting of 1 base image, 1 extension image and 1 tmpfs and used kexec to boot it!
It was kinda like a multi-ubuntu-system cd and it worked!
So kernelpatching should be no problem (my cd reloaded the kernel from the base image on the fly thanks to kexec).

---

