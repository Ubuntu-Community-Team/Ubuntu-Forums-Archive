---
title: "Kernel Question"
date: 2013-03-24
forum: Ubuntu Development Version
---

### Post by roly33 on 2013-03-24
I'm Running 13.04 from a Daily Build image that I downloaded on Friday and wondered what the Kernel Version is & if there is a newer stable one available, & if it's pretty simple for a newbie to update?

Roland

---

### Post by zika on 2013-03-24
> **roly33 said:**
> I'm Running 13.04 from a Daily Build image that I downloaded on Friday and wondered what the Kernel Version is & if there is a newer stable one available, & if it's pretty simple for a newbie to update?

RolandYou're not running 13.04 since that does not exist yet... You're running (let's say) Beta for future 13.04... Daily edition... There is one that is newer but not surely more stable: tomorrow's daily... If You just do regular update/upgrade You will get to RR(a.k.a. 13.04) and then to rolling one...

---

### Post by roly33 on 2013-03-24
> **zika said:**
> You're not running 13.04 since that does not exist yet... You're running (let's say) Beta for future 13.04... Daily edition... There is one that is newer but not surely more stable: tomorrow's daily... If You just do regular update/upgrade You will get to RR(a.k.a. 13.04) and then to rolling one...

I'm fully up-to-date with all the updates so, in-line with today's  daily build.  My question was related to the Kernel as I was asking if their is a newer Kernel than the one that is in the Dev build of 13.04 & how easy is it to update to the latest stable Kernel?

Roland

---

### Post by dino99 on 2013-03-24
while updating/upgrading, the system take care of all the new packages, including possible new kernel

---

### Post by roly33 on 2013-03-24
> **dino99 said:**
> while updating/upgrading, the system take care of all the new packages, including possible new kernel

Ok thank's.

Roland

---

### Post by spier on 2013-03-24
Accordingly [www.kernel.org](www.kernel.org), the latest stable kernel is 3.8.4, while RR seems freezed on 3.8.0...

---

### Post by dino99 on 2013-03-24
> **spier said:**
> Accordingly [www.kernel.org](www.kernel.org), the latest stable kernel is 3.8.4, while RR seems freezed on 3.8.0...

numbering into ubuntu is different; simply glance at each ubuntu kernel changelog (into synaptic) to know the related vanilla number.

---

### Post by grahammechanical on 2013-03-24
When running the development branch we sometimes find that kernel updates break things and we have to use an older kernel. So, if the kernel that you have at present is not stable on your machine, then I doubt very much if a newer kernel brought in from outside the Ubuntu update sytem will improve things. Here is why.

There is always a delay between the release of kernels through the Linux kernel organization and the merging of them in the Ubuntu development release. Some of these released kernels are beta or release candidates. In other words not to be viewed as stable. Some of us like to install them. Some of us like living on the edge. So, there are newer kernels available, but I would not call them stable from the point of view of Ubuntu.

At the moment on my Raring install I have kernel 3.8.0.14. That is the 3.8 kernel with 14 modifications by the Ubuntu developers. I expect more to come through. But there is a kernel 3.8.4 available which is called stable by the Linux kernel developers and a release candidate for kernel 3.9 which is called mainline. We do not as yet have these in the Ubuntu development branch because the developers what to release a stable 13.04 Ubuntu in a months time.

[https://www.kernel.org/](https://www.kernel.org/)

Regards.

---

### Post by matt_symes on 2013-03-24
If you are interested in the newest kernels...

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
```

matthew-S206:/home/matthew % uname -r
3.9.0-030900rc3-generic
matthew-S206:/home/matthew % 
```

rc stands for release candidate, in this case release candidate 3.

It's been stable on my s206 so far.

---

### Post by zika on 2013-03-24
> **matt_symes said:**
> If you are interested in the newest kernels...

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
```

matthew-S206:/home/matthew % uname -r
3.9.0-030900rc3-generic
matthew-S206:/home/matthew % 
```

rc stands for release candidate, in this case release candidate 3.

It's been stable on my s206 so far.
Or to be in accordance with Daily:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/)
:)
```
:~$ uname -aLinux zika 3.9.0-999-generic #201303240405 SMP Sun Mar 24 08:05:57 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```
I know this post is childish but I could not help it... I hope I will be pardoned... I do use daily for years now...

---

### Post by matt_symes on 2013-03-24
Hi

> I know this post is childish but I could not help it...

It's not a childish post Zika; it's a very relevant post :KS

I don't reboot every day though so i do not use dailys. Most times my laptop is on for a week or more between reboots.

It's another option for the OP though.

Kind regards

---

### Post by spier on 2013-03-24
Got it, thanks, guys.
As about living on the edge, I'll let it to the braves!

---

### Post by roly33 on 2013-03-24
If the Kernel is customized by Ubuntu then I think I'll stick with what came in the Daily build of 13.04 as it is stable.  I just thought that since I'm living with a cutting edge distro I might as well have acutting edge Kernel, but if that'll cause problems I'll stick with and wait until 13.04 is officially released and give the Dev's time to build a stable newer Kernel.

Roland

---

### Post by zika on 2013-03-25
> **spier said:**
> Got it, thanks, guys.
As about living on the edge, I'll let it to the **braves**!Thank You for choosing Your words... ;)
I wouldn't ever use that word addressing myself... Some other come to mind but... I'll stay to that...

---

### Post by zika on 2013-03-25
> **roly33 said:**
> If the Kernel is customized by Ubuntu then I think I'll stick with what came in the Daily build of 13.04 as it is stable.  I just thought that since I'm living with a cutting edge distro I might as well have acutting edge Kernel, but if that'll cause problems I'll stick with and wait until 13.04 is officially released and give the Dev's time to build a stable newer Kernel.

RolandIf that would cause problems or not the only way to know is to try... You could always retreat to „old“ kernel if a new one doesn't work/fit You...

---

