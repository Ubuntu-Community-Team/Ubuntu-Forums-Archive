---
title: "linux kernel 3.15-rc8 .deb files are ready..."
date: 2014-06-02
forum: Ubuntu Development Version
---

### Post by zika on 2014-06-02
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-rc8-utopic/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-rc8-utopic/)

---

### Post by Ian_Worrall on 2014-06-02
Phoronix is reporting that Linus is pretty happy with this one but wants it testing before calling it final. Also due to his family holidays coming up shortly, the 3.16 merge window is already open.

---

### Post by slickymaster on 2014-06-02
> **Ian_Worrall said:**
> Phoronix is reporting that Linus is pretty happy with this one but wants it testing before calling it final<...snip...>.

And so am I. Been running it for a couple of hours now, and so far everything is cruising along nicely```
~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Utopic Unicorn (development branch)
Release:	14.10
Codename:	utopic
3.15.0-031500rc8-generic
```

---

### Post by Mateusz Stachowski on 2014-06-03
If you want to be on latest kernel in Utopic than there is so far no point in using Mainline Kernel PPA because the kernels provided in repository are already based on latest RC releases of 3.15.

[https://launchpad.net/ubuntu/utopic/+source/linux/3.15.0-5.10](https://launchpad.net/ubuntu/utopic/+source/linux/3.15.0-5.10)

> linux (3.15.0-5.10) utopic; urgency=low

  [ Tim Gardner ]


  * Release Tracking Bug
    - LP: #1325596
  * [Config] CONFIG_POWERNV_CPUFREQ=y for ppc64el
  * **rebase to v3.15-rc8**


  [ Upstream Kernel Changes ]


  * **rebase to v3.15-rc8**
 -- Tim Gardner <tim.gardner@canonical.com>   Mon, 02 Jun 2014 12:59:34 +0000

---

### Post by craig10x on 2014-06-08
I installed this kernel the other day on my ubuntu 14.04 to hopefully solve the multimedia instability problems i have discussed in another thread here which was originally solved with the 3.13 kernel but got messed up again on a recent kernel update on 14.04....when i ran a live session of 14.10 using the 3.15 kernel i noticed that it took care of those problems on my particular hardware, so i took a chance and installed 3.15 RC8 on my 14.04 install and i am pleased to report it worked beautifully :D

The 3.15 RC8 seems to work great, gives me the stability again that i needed and seems to have other benefits too (very snappy performance and lower ram usage to name two of them)...

Just wondering...i know LTS will get the utopic kernel also (which will probably be 3.16 when released) does that happen in 14.04.1 or not until 14.04.2?  Anyone know?
Also, this is the mainline kernel i installed of course...what are the differences between the mainline and the ubuntu version of it (if any)?

Thanks ;)

---

### Post by rrnbtter on 2014-06-08
Greetings,
The 3.15RC kernels actually started with Trusty. We had the 3.13 default and the 3.14RC and 3.15RC all going at the same time. The repositories completely jumped the 3.14 kernel for both Trusty and Utopic. This kernel thing for me is sometimes a problem solver and sometimes a toy [something to test].  The minumum point that I can decern is that I'm not waiting on the repositories for the update. But to say that the repos are consistant with the RC Releases isn't true [all of the time]. This link [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) tells the tale. We had three kernels running in April of 2014 all for Trusty while the repositories stayed with 3.13.

---

### Post by pqwoerituytrueiwoq on 2014-06-08
3.15 has been released ( [https://www.kernel.org/](https://www.kernel.org/) ), [s]not in the mainline just yet[/s]
[http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)

---

