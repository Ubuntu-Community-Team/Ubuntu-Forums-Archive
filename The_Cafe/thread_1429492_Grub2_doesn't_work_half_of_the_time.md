---
title: "Grub2 doesn't work half of the time"
date: 2010-03-14
forum: The Cafe
---

### Post by perham on 2010-03-14
I've seen like 20 threads about failure to boot or incompatibility of grub2 with windows 7, vista or even XP. it seems that it crashes most of the times, making the system unusable. I had to revert my brother's boot loader to grub legacy, and I myself am using grub legacy too. what was wrong with grub legacy that Ubuntu developers chose grub2 over grub when it doesn't work well?

---

### Post by Bachstelze on 2010-03-14
GRUB .97 is not maintained anymore, which means that if a security vulnerability is discovered, it will not be fixed by the developers.

*EDIT:* also, GRUB 2 Works For Me&#8482;.

---

### Post by Psumi on 2010-03-14
Protip: Don't #ofOSes-boot.

I only use one distro on a machine, and that's fine with me.

---

### Post by alanjackson on 2010-03-14
I have a netbook with XP, Karmic Ubuntu, and Karmic Kubuntu on it. Grub never fails.

---

### Post by dmizer on 2010-03-14
> **perham said:**
> what was wrong with grub legacy that Ubuntu developers chose grub2 over grub [snip]?

Legacy grub can't boot ext4 partitions.

---

### Post by Regenweald on 2010-03-14
> **Bachstelze said:**
> <snip>

GRUB 2 Works For Me™.

Same here. Worked dual booting Win7, works dual booting Vista. You guys are doing something wrong.;)

---

### Post by CharlesA on 2010-03-14
> **dmizer said:**
> Legacy grub can't boot ext4 partitions.

Didn't know that, thanks.

> **Regenweald said:**
> Same here. Worked dual booting Win7, works dual booting Vista. You guys are doing something wrong.;)

I'm tribooting XP, Backtrack4 and Ubuntu 9.10 with no problems. *shrug*

---

### Post by RATM_Owns on 2010-03-14
> **dmizer said:**
> Legacy grub can't boot ext4 partitions.
[http://repos.archlinux.org/wsvn/packages/grub/repos/core-i686/ext4.patch](http://repos.archlinux.org/wsvn/packages/grub/repos/core-i686/ext4.patch)
[http://repos.archlinux.org/wsvn/packages/grub/repos/core-x86_64/ext4.patch](http://repos.archlinux.org/wsvn/packages/grub/repos/core-x86_64/ext4.patch)

?

---

### Post by dmizer on 2010-03-14
> **RATM_Owns said:**
> [http://repos.archlinux.org/wsvn/packages/grub/repos/core-i686/ext4.patch](http://repos.archlinux.org/wsvn/packages/grub/repos/core-i686/ext4.patch)
[http://repos.archlinux.org/wsvn/packages/grub/repos/core-x86_64/ext4.patch](http://repos.archlinux.org/wsvn/packages/grub/repos/core-x86_64/ext4.patch)

?

Right. It has to be patched because:
> **Bachstelze said:**
> GRUB .97 is not maintained anymore

---

### Post by dragos240 on 2010-03-14
I have grub legacy and I didn't need a patch for my system running on an ext4 system.

---

### Post by chriswyatt on 2010-03-14
GRUB2 boots every time for me, 100%.

---

### Post by dmizer on 2010-03-14
> **dragos240 said:**
> I have grub legacy and I didn't need a patch for my system running on an ext4 system.

Is the boot partition also ext4?

---

### Post by dragos240 on 2010-03-14
> **dmizer said:**
> Is the boot partition also ext4?

Uhhh..... no. That's probably why. But why would you use ext4 for a boot partition anyway?

---

