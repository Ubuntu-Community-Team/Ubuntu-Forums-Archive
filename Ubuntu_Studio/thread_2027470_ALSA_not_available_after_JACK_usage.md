---
title: "ALSA not available after JACK usage"
date: 2012-07-16
forum: Ubuntu Studio
---

### Post by adam933 on 2012-07-16
I start jackd with the following terminal command:

```
/usr/bin/jackd -dalsa -r44100 -p1024 -n2 -D -Chw
:0,0 -Phw:0,0
```
Then I start QjackCtl, and JACK works just fine.

The trouble occurs when I quit JACK, and want to use ALSA for other applications.  ALSA is not available, and I must reboot to get it started again.

Is there a command I can use to restart ALSA without rebooting?

Thanks for your help.

---

### Post by jejeman on 2012-07-16
Check if jackd is really terminated. If not, kill it.

---

### Post by sgx on 2012-07-16
> **adam933 said:**
> I start jackd with the following terminal command:

```
/usr/bin/jackd -dalsa -r44100 -p1024 -n2 -D -Chw
:0,0 -Phw:0,0
```
Then I start QjackCtl, and JACK works just fine.

The trouble occurs when I quit JACK, and want to use ALSA for other applications.  ALSA is not available, and I must reboot to get it started again.

Is there a command I can use to restart ALSA without rebooting?

Thanks for your help.
killall jackd

you can see whats running using htop

It monitors cpu distribution/use, memory use, and other things.
You can select a running process, and stop it using a function key.
Cheers

---

### Post by adam933 on 2012-07-16
Thanks all.
Just installed htop - looks good!

---

