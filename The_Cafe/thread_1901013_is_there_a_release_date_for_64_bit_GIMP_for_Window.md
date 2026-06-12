---
title: "is there a release date for 64 bit GIMP for Windows?"
date: 2011-12-27
forum: The Cafe
---

### Post by todd500 on 2011-12-27
does anyone know when GIMP will work for windows 7 64 bit?

---

### Post by crazy bird on 2011-12-27
[Check on this site]("http://gimp-win.sourceforge.net/stable.html") @ the bottom: additional packages.

---

### Post by todd500 on 2011-12-27
> **crazy bird said:**
> [Check on this site]("http://gimp-win.sourceforge.net/stable.html") @ the bottom: additional packages.
it says unstable :(
does it work well?
I'm just afraid its going to give me a bunch of problems

---

### Post by undecim on 2011-12-27
I thought you could just run the 32-bit version... Am I missing something?

---

### Post by JRV on 2011-12-27
It says that it is 64 bit, if I interpret this correctly.
```
jack@manx:~$ which gimp
/usr/bin/gimp
jack@manx:~$ file /usr/bin/gimp
/usr/bin/gimp: symbolic link to `gimp-2.6'
jack@manx:~$ which gimp-2.6
/usr/bin/gimp-2.6
jack@manx:~$ file /usr/bin/gimp-2.\6
/usr/bin/gimp-2.6: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped

```

This is a standard installation of gimp from the repositories in Ubuntu 10.04. (Lucid)

---

### Post by Lucradia on 2011-12-27
The 64-bit version for Windows is more unstable than the one for Linux. For instance, on the Win64 version, the menus will sometimes have all of its text disappear, it cannot be fixed unless you close it and re-open, the text disappearing will happen at random, and sometimes immediately when you open Win64 gimp.

> **JRV said:**
> It says that it is 64 bit, if I interpret this correctly.
```
jack@manx:~$ which gimp
/usr/bin/gimp
jack@manx:~$ file /usr/bin/gimp
/usr/bin/gimp: symbolic link to `gimp-2.6'
jack@manx:~$ which gimp-2.6
/usr/bin/gimp-2.6
jack@manx:~$ file /usr/bin/gimp-2.\6
/usr/bin/gimp-2.6: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped

```

This is a standard installation of gimp from the repositories in Ubuntu 10.04. (Lucid)

Read the OP, they're asking for Windows 7 64-Bit.

> **undecim said:**
> I thought you could just run the 32-bit version... Am I missing something?

Yes, you can, but then Windows has to force it to use more than one core if it has to. Since 32-bit isn't coded to handle more properly, even with the hacking of PAE.

---

### Post by undecim on 2011-12-27
> **JRV said:**
> It says that it is 64 bit, if I interpret this correctly.
```
jack@manx:~$ which gimp
/usr/bin/gimp
jack@manx:~$ file /usr/bin/gimp
/usr/bin/gimp: symbolic link to `gimp-2.6'
jack@manx:~$ which gimp-2.6
/usr/bin/gimp-2.6
jack@manx:~$ file /usr/bin/gimp-2.\6
/usr/bin/gimp-2.6: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped

```

This is a standard installation of gimp from the repositories in Ubuntu 10.04. (Lucid)

[witty comment about reading only the title]

---

### Post by oldos2er on 2011-12-27
Title changed.

---

### Post by JRV on 2011-12-27
> **undecim said:**
> [witty comment about reading only reading the title]

Sorry, I just don't think Windows.

---

### Post by Lucradia on 2011-12-27
> **JRV said:**
> Sorry, I just don't think Windows.

It wouldn't be here if it wasn't for Windows anyway. There is a GIMP Community. Several actually: [https://www.google.com/search?q=gimp+forums](https://www.google.com/search?q=gimp+forums)

---

### Post by thatguruguy on 2011-12-27
> **Lucradia said:**
> It wouldn't be here if it wasn't for Windows anyway.[]("https://www.google.com/search?q=gimp+forums")

I don't understand what you mean by that statement.  Could you elaborate?

---

### Post by 3rdalbum on 2011-12-28
> **Lucradia said:**
> Yes, you can, but then Windows has to force it to use more than one core if it has to. Since 32-bit isn't coded to handle more properly, even with the hacking of PAE.

How does the bit-width affect threading? A multi-threaded 32-bit program running on 64-bit Windows will use the same number of threads as on 32-bit Windows. Windows will distribute the threads among the available cores just as it would with a native 64-bit program.

---

### Post by Lucradia on 2011-12-28
> **3rdalbum said:**
> How does the bit-width affect threading? A multi-threaded 32-bit program running on 64-bit Windows will use the same number of threads as on 32-bit Windows. Windows will distribute the threads among the available cores just as it would with a native 64-bit program.

But it isn't optimized for that.

---

