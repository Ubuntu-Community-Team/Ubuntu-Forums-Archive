---
title: "Missing memory - is it indicating a virus?"
date: 2007-06-16
forum: Server Platforms
---

### Post by laltopi on 2007-06-16
I have a machine with 512MB memory. The kernel shows a slightly smaller amount
```

dmesg | grep Memory
[  305.152184] Memory: 508728k/524224k available (1992k kernel code, 14976k reserved, 900k data, 328k init, 0k highmem)

```

The gnome system monitor shows even lower 503.8MB.

What could be the reason for the missing 8M memory? Is there a virus hiding?

---

### Post by Daisybobs on 2007-06-16
No, it isn't a virus hiding. And you'll probably find that everything is OK.

Sometimes RAM comes in 'wonky' sizes, but the kernel may have detected the wrong amount.
There used to be an option for the kernel startup "mem=512MB" but this shouldn't be needed anymore.

---

### Post by dmizer on 2007-06-16
no, it's all there.

524 224 kilobytes = 511.9375 megabytes

i would suggest taking gnome system monitor with a grain of salt.

further, if you have a laptop ... your bios will reserve a portion of the ram to use for video ram.  there will always be a small portion of ram reserved for system processes.  you will never get full use of 100% of your ram.

---

### Post by ubuntu27 on 2007-11-04
Maybe this webpage could be helpful

[Memory Management in GNU/Linux]("http://northco.net/chenke/project/linuxmm.html")

---

### Post by HermanAB on 2007-11-04
The answer to the question:
$ free

Cheers,

Herman

---

