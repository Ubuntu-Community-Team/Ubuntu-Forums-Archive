---
title: "Default settings for &quot;whole drive encrypted lvm&quot; setup"
date: 2008-12-09
forum: Security
---

### Post by tornadof3 on 2008-12-09
Hi

I have used the 8.10 alternate CD to install encrypted root filesystem (using lvm) on my laptop, and it appears to work great.

My question is what crypto setup did it use (it must have been the 'default' because no options were offered). I'm assuming it's using LUKS, does anyone know what the default cipher, hash algorithm, and key size is in this setup? Anyway to check/change it?

Thanks

---

### Post by bp1509 on 2008-12-09
d

---

### Post by tornadof3 on 2008-12-09
OK thanks, that's great. I've looked into the defaults, and the man page also says I can use the luksDump option to get the header info (which would contain this)

the command

```
cryptsetup luksDump /dev/mapper/sda1_crypt
```

returns error "can't open device".

the contents of /dev/mapper is:

```
pmreid@hp-laptop:~$ ls /dev/mapper
control  hp--laptop-root  hp--laptop-swap_1  sda1_crypt

```
and similarly for the other devices.
Anyone any ideas how to get the info out of it?

---

### Post by hyper_ch on 2008-12-09
by default it uses aes 256bit.

Here's a screenshot I made:

[IMG]http://www.sjau.ch/cryptosetup/26_home_properties.png[/IMG]

---

### Post by tornadof3 on 2008-12-09
Thank you so much. Curious how you got to that screen. Coyuldn't get there with the 'normal' disk, had to use the 8.10 x64 "alternate" disc which didn't give me any customisation options?!

---

### Post by hyper_ch on 2008-12-09
use the alternate cd, select manual partitioning.... you have a step-by-step guide for manual encryption: [http://ubuntuforums.org/showthread.php?t=848691](http://ubuntuforums.org/showthread.php?t=848691)

In Ibex I think you can now also encrypt the swap partition. Just change in the according screen the encryption key from passphrase to random.

---

