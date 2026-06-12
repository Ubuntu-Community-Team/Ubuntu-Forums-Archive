---
title: "move back to regular kernel?"
date: 2010-09-20
forum: Ubuntu Studio
---

### Post by extendedping on 2010-09-20
well my sound keeps crashing. on firefox, skype, youtube, every few minute I must close the app to reenable sound. I have the real time kernel and a bunch of studio packages (on top of the regular distro). I have an external sound card and a built in one and it happens on both so I am pretty sure it is not hardware.

simple question...what is the default (regular) ubuntu kernel? I don't wnat to install the wrong one. also will I then have the option at boot of using the rt kernel if I choose for recording? thanks...

---

### Post by Pablo_F on 2010-09-20
> simple question...what is the default (regular) ubuntu kernel? 

Today is... I don't know. The complete version number changes form time to time. You'd better install the metapackage "linux-generic". Description:

"This package will always depend on the latest complete generic Linux kernel available".

>  also will I then have the option at boot of using the rt kernel if I choose for recording? 

You should, unless grub is not correctly configured or not updated after configuring /etc/default/grub. But normally, it is done automagically.

If something goes wrong (i.e., you can't see both kernels at least as boot options even if you have installed them), see:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

That said, 

1. You need to set rtprio and memlock for the user to be able to run jack in realtime mode (needed) and jack can run in realtime mode with both generic and rt kernels.

2. For very low latency, you might need the rt kernel and a well configured rtirq script, between other tweaks and facts including software and hardware. The audio configuration wiki at linuxmusicians.com has a lot of useful info.

Cheers! Pablo

---

### Post by extendedping on 2010-09-20
thanks I am going to test sound for a day, so far it has not crashed with the new kernel (well if crashing is sound just stopping in different apps).

---

### Post by Pablo_F on 2010-09-20
Can you give the output of the following informative commands?

lspci | grep -i audio

cat /proc/asound/cards

cat /proc/asound/modules

cat /proc/asound/card0/codec#0 | grep -i codec

Cheers! Pablo

---

