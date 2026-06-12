---
title: "The GNU C Library Missing Sources"
date: 2014-04-27
forum: Ubuntu Application Development
---

### Post by falven on 2014-04-27
Hi,
I'm trying to write a Semaphore implementation so I thought of looking at the current semaphore implementation from the GNU C Library.
I couldn't find the source files, only the headers semaphore.h, semaphoreP.h, semaphore.h-data. A lot of these semaphore.h headers were repeated too. Strange.
I think the reason there was no source file is because the semaphore itself is probably OS/kernel implemented.
So my question stands. If Ubuntu is supposed to be "open", and the source, "readily available" how could I get my hands on the current source for the semaphore?
Thanks,
-Falven

---

### Post by lisati on 2014-04-27
Sometimes looking at the header files can be more confusing than helpful.

[Here]("http://www.amparo.net/ce155/sem-ex.html")'s an example of a program which uses semaphore.h

---

### Post by falven on 2014-04-27
lisati,
Thanks for your reponse and help so far :)
Unfortunately, however, this is not what I am looking for. I am actually attempting to write the semaphore itself. Not use it.
-Falven

---

### Post by steeldriver on 2014-04-27
The semaphore implementation is part of the kernel source - you'd need to download the kernel source tree (either using apt-get source or from the git repo)

```

$ find linux-3.2.0/ -name 'semaphore.c'
linux-3.2.0/kernel/semaphore.c

```

See [https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)

---

### Post by falven on 2014-04-27
> **steeldriver said:**
> The semaphore implementation is part of the kernel source - you'd need to download the kernel source tree (either using apt-get source or from the git repo)

```

$ find linux-3.2.0/ -name 'semaphore.c'
linux-3.2.0/kernel/semaphore.c

```

See [https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)

Perfect!
Thanks,
-Falven

---

