---
title: "identify installed OS"
date: 2009-09-17
forum: Server Platforms
---

### Post by shahansudu on 2009-09-17
hi,

   I'm working with a Ubuntu Server 8.04 but I do not know whether the OS is 32 bit or 64 bit installation. Is there a way to quickly find whats the installed OS in Ubuntu? Thanx in advance

---

### Post by ainsworth_t on 2009-09-17
From the terminal, run the command:
```
uname -a
```

You will get an output like this:
> username@hostname:~$ uname -a
Linux hostname 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux


As you can see, my system returns "i686" towards the end of the line, which means I'm running a 32-bit system. A 64-bit system will return "x64" or "AMD64", I don't remember which because it's been a while since I've run that command on a 64-bit system.

---

### Post by fjgaude on 2009-09-17
Linux sunshine 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux

That's it for a 64-bit system.

---

### Post by shahansudu on 2009-09-17
thank you

---

