---
title: "Upgrade from Lubuntu to Studio"
date: 2012-10-09
forum: Ubuntu Studio
---

### Post by furtom on 2012-10-09
I had Lubuntu 12.04 installed and I installed the Studio meta packages following [this guide]("https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu").

It all went fine and without a hitch. Going through the rest of the procedure, it seemed that all I needed to do is to include my user in the audio and video groups. All the rest of the instructions seemed to have been for older versions and was not necessary to do in 12.04.

Basic testing seems to go well and I have no problems, I'd just like to make sure I'm not missing something obvious.

Thanks!

---

### Post by jejeman on 2012-10-10
Just make shure that you have RT priority set.
```
cat /etc/security/limits.d/audio.conf
```

---

### Post by smartboyhw on 2012-10-11
> **jejeman said:**
> Just make shure that you have RT priority set.
```
cat /etc/security/limits.d/audio.conf
```

furtom: Make sure you install the linux-lowlatency package :D

---

### Post by furtom on 2012-10-11
Thanks guys. I haven't had a chance to do anything yet, but I'll be sure to post the result of 

```
cat /etc/security/limits.d/audio.conf
```

soon.

What I can tell you so far is that I certainly installed the lowlatency package along with the rest of the studio stuff, but the funny thing is, grub still only offers to boot the generic kernel. I even checked the older kernels on the menu to be sure. Not there.

I know I installed it and the install seemed to work fine as I got the RT dialog when dpkg was installing it. Shouldn't there be a lowlatency kernel to boot now in grub or am I missing something?

---

### Post by furtom on 2012-10-12
Here's cat /etc/security/limits.d/audio.conf

I admit, It's not what I expected.

```
# Provided by the jackd package.
#
# Changes to this file will be preserved.
#
# If you want to enable/disable realtime permissions, run
#
#    dpkg-reconfigure -p high jackd

@audio   -  rtprio     95
@audio   -  memlock    unlimited
#@audio   -  nice      -19

```

---

### Post by jejeman on 2012-10-12
Limits are set ok.

Try updateing GRUB again. It should list all kernels.
```
sudo update-grub
```
Give us output from
```
ls /boot
```
```
cat /boot/grub/grub.cfg | grep menuentry
```

---

### Post by furtom on 2012-10-14
Well, I finally had a chance to take a look. Odd thing was, no rt or lowlatency kernel was installed. I could have sworn I installed it!

Stranger still, I found the latest lowlatency headers, but no image. Did I install the headers only? I'll chalk it up to old age... :) I would have thought the headers depend on the image, but perhaps not.

I installed the meta package and all is good to go.

In any case, everything is working as it should, pending detailed testing. Thanks for the advice.

---

