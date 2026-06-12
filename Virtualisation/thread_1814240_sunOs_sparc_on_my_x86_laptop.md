---
title: "sunOs sparc on my x86 laptop"
date: 2011-07-29
forum: Virtualisation
---

### Post by lain80 on 2011-07-29
Hi,

I want to install sunOs sparc on my x86 laptop. I'm reading on internet  and I could do it with qemu (and custom bios for sparc) but I don't find  any howto or tutorial.

Have anyone experience with qemu and sparc?

Cheers,
Lain

```

mauri@mauri-laptop:~$ qemu-system-sparc -cdrom /media/Ext640ntfs/Programmi/sol-10-u9-ga-sparc-dvd.iso 
qemu: could not load prom 'openbios-sparc32'
mauri@mauri-laptop:~$ uname -a
Linux mauri-laptop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

---

