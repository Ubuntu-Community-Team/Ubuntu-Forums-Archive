---
title: "what's with kernel-generic from the netboot dir"
date: 2006-10-11
forum: Server Platforms
---

### Post by rampant on 2006-10-11
The netboot kernel/initrd from the Alternate CD seem to be using kernel-generic, at least after checking out the contents of the initrd.

I'd like to know more about the kernel 'linux' contained in netboot.

1. The kernel-generic looks different from the normal kernel-generic that there are .debs for.
2. Know where I can find the .config for the kernel they used?  It Doesn't support config.gz, and doesn't seem to provide a kernel config (at least that I can find anywhere).
3. Trying to use a normal kernel-generic or kernel-server (and associated initrd) results in a /dev/rd/0 does not exist.  My guess is that this has something to do with devfs/udev.
4. I have no idea why the netboot is so desktop/ltsp-oriented.  It doesn't seem to support a lot of things servers should, like the -server CD install.

Basically, we're trying to customize this for our arch.  Any help is appreciated.  My guess is this will be easy to fix.

A .config or pointer to where I can find it would make my day! ](*,)

---

### Post by rampant on 2006-10-12
Bump - just need a .config for the netboot kernel.

---

