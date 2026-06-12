---
title: "[SOLVED] LVM not installing?"
date: 2008-02-24
forum: Server Platforms
---

### Post by bluepowder7 on 2008-02-24
i just (FINALLY) got 7.10 Server installed and booting, and i was about to set up the 750G drive as the first of a LVM pool.  (the OS is installed on a separate 4G).  i found a guide to installing and setting up LVM here ([http://ubuntuforums.org/showthread.php?t=555638](http://ubuntuforums.org/showthread.php?t=555638)), but after the first step, i get this message:

```
greg@server1:/dev$ sudo apt-get install lvm2 lvm-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package lvm-common is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lvm2
E: Package lvm-common has no installation candidate

```

since i'm only accessing the server box using ssh from my laptop, i have to learn to use the command line.  so, do i need to enable repositories somehow?

---

### Post by faulkes on 2008-02-25
> **bluepowder7 said:**
> 
```
This may mean that the package is missing, has been obsoleted, or
is only available from another source
[B]However the following packages replace it:
  lvm2
[/B]E: Package lvm-common has no installation candidate

```

since i'm only accessing the server box using ssh from my laptop, i have to learn to use the command line.  so, do i need to enable repositories somehow?

Please see the bold highlighted text.

Faulkes

---

### Post by bluepowder7 on 2008-02-25
got it figured out.  just ran the same command but without the "lvm-common" at the end.  the message and part you highlighted wasn't clear to me at first, though, so i wasn't sure if i was supposed to do "lvm2 lvm2" or what.  anyways, seems it's working now!

---

