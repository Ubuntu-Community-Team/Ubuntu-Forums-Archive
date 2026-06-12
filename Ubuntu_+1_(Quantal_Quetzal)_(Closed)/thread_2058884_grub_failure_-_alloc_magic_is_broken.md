---
title: "grub failure - alloc magic is broken"
date: 2012-09-16
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by scradock on 2012-09-16
Any ideas for getting around this stumbling block, anyone? I'm testing quantal, and running several other Ubuntu installs, some on the main HD (sda) and others on a USB external drive (sdb). Since the update to grub2I've been having increasing problems with grub, not accessing some installs, etc. 

The latest manifestation is that booting from Precise, on my main HD, I get the error message:

```
alloc magic is broken at 0xb5b4aeb0. 
Aborted. Press any key to exit.
```

Of course, pressing any key returns the same message, indefinitely.

There is no grub> prompt, no grub rescue> prompt; simply an error message before I see the list of installed options.

Any ideas?

---

### Post by dino99 on 2012-09-17
hope you does not get the same issue than me: bug #1050774   
  ):P

---

### Post by YannBuntu on 2012-09-17
> **dino99 said:**
> @yann
[http://ubuntuforums.org/showthread.php?t=2058884](http://ubuntuforums.org/showthread.php?t=2058884)

mine is: paste.ubuntu.com/1202088

grub-install returns:
```
Embedding-error-in-sdb detected. You may want to retry after activating the [Separate /boot partition:] option.
```

Please try creating a little boot partition at the start of your Quantal disk ( sdb). See [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)

---

### Post by dino99 on 2012-09-17
> **YannBuntu said:**
> grub-install returns:
```
Embedding-error-in-sdb detected. You may want to retry after activating the [Separate /boot partition:] option.
```

Please try creating a little boot partition at the start of your Quantal disk ( sdb). See [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)

Thanks yann, is that specific to the new grub 2.00 ? Why is that needed now ?
(actually i can boot on sata as ahci, but pata still refuse on that old hardware with a bios)

---

### Post by QIII on 2012-09-17
Same problem here.  To get around it for the moment, I changed my boot order and updated GRUB in Quantal so I can boot into my Precise from there.  That works on a multi disk multi boot - but not a single disk environment.

Unacceptable, of course.  For those experimenting with a distro with GRUB2 in multiboot environments, having that distro botch their boot process will be unwelcome.

Haven't had much time to go through Launchpad yet.

---

### Post by YannBuntu on 2012-09-17
> **dino99 said:**
> Thanks yann, is that specific to the new grub 2.00 ?

See [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1030887](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1030887)
(I'm not sure if this will your problem, but it costs nothing trying)

Furthermore, Quantal comes with a brand new version of GRUB, and it seems quite buggy...

---

