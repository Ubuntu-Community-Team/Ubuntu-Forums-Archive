---
title: "Linux kernel 3.8"
date: 2013-02-01
forum: Ubuntu Development Version
---

### Post by Harry33 on 2013-02-01
Now we have rc-5 rebased linux kernel 3.8 in official RR repos.

Here:
[https://launchpad.net/ubuntu/raring/+source/linux/3.8.0-3.7](https://launchpad.net/ubuntu/raring/+source/linux/3.8.0-3.7)

---

### Post by tad1073 on 2013-02-01
My wireless laser keyboard and mouse doesn't work on that kernel.

Microsoft wireless laser keyboard and mouse 5000.

---

### Post by meteorrock on 2013-02-01
How is that new kernel working out for you guys? I am interested in updating my kernel base.

Any outstanding bugs? Besides the poster above?

---

### Post by ft_ on 2013-02-01
I've seen no bugs, except the no-ethernet bug still here.

---

### Post by screaminj3sus on 2013-02-01
This is the first kernel where my system76's brightness keys work out of the box :)

No problems with this kernel so far, works great.

---

### Post by IanW on 2013-02-01
I think rc5 has the "brick your UEFI Samsung laptop" problem.
rc6 has now been released which fixes this.

---

### Post by dino99 on 2013-02-01
cant get nvidia-310 loaded  :(

---

### Post by Harry33 on 2013-02-01
> **dino99 said:**
> cant get nvidia-310 loaded  :(

Try Nvidia-313 from xorg-edgers.
That one will work, and fine.

---

### Post by tad1073 on 2013-02-01
> **tad1073 said:**
> My wireless laser keyboard and mouse doesn't work on that kernel.

Microsoft wireless laser keyboard and mouse 5000.

I forgot to download and install linux-image-extra, it works fine now.

---

### Post by pqwoerituytrueiwoq on 2013-02-01
Seems to boot faster :D

---

### Post by Harry33 on 2013-02-02
There is the rc-6 now in RR repos.

Here:
[https://launchpad.net/ubuntu/raring/+source/linux/3.8.0-4.8](https://launchpad.net/ubuntu/raring/+source/linux/3.8.0-4.8)

---

### Post by kurt18947 on 2013-02-02
The RTL-8188CUS driver from Realtek would not build using the install.sh script.  Result was 'error 2'.  Notified RealTek.

---

### Post by VinDSL on 2013-02-03
> **dino99 said:**
> cant get nvidia-310 loaded  :(
This one :confused:

```
vindsl@Zuul:~$ apt-cache policy nvidia-304
nvidia-304:
  Installed: 304.64-0ubuntu4
  Candidate: 304.64-0ubuntu4

```

It's the only legacy driver that loads (with Linux 3.8) on this machine...

---

### Post by VinDSL on 2013-02-03
> **meteorrock said:**
> How is that new kernel working out for you guys? I am interested in updating my kernel base.
3.8-rc6 is working fine on this ancient Intel-based machine (see sig).

Not so sure about AMD-based machines. Been reading some horror stories lately.

For the life of me, I cannot figure out why it works.  Every time I upgrade my kernel, it complains about not finding the dkms.conf file and aborts.  Then it continues and I get a KMOD failure and abort.  But, the upgrades always work, when I restart.  

Go figure... :)

---

### Post by dino99 on 2013-02-03
> **VinDSL said:**
> This one :confused:


It's the only legacy driver that loads (with Linux 3.8) on this machine...

Problem solved with rc6  & nvidia-310  :D

---

### Post by VinDSL on 2013-02-03
> **dino99 said:**
> Problem solved with rc6  & nvidia-310
nVidia rulez!  :D


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-2-feb-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-2-feb-2013-1.png")[/INDENT]

---

### Post by meteorrock on 2013-02-03
Thanks everyone :) ):P

Take care kernel maintainers and debuggers.

---

### Post by zika on 2013-03-21
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.4-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.4-raring/)

---

### Post by tjeremiah on 2013-03-24
> **kurt18947 said:**
> The RTL-8188CUS driver from Realtek would not build using the install.sh script.  Result was 'error 2'.  Notified RealTek.

any update on this? I just installed 13.04 and having the same problem with this kernel.

---

