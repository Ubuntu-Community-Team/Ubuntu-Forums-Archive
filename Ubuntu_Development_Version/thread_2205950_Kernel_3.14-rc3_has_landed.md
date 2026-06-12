---
title: "Kernel 3.14-rc3 has landed"
date: 2014-02-16
forum: Ubuntu Development Version
---

### Post by paul_in_london on 2014-02-16
```
paul@trusty-64:~$ uname -a
Linux trusty-64 3.14.0-rc3-custom-low-latency #1 SMP PREEMPT Sun Feb 16 22:32:02 GMT 2014 x86_64 x86_64 x86_64 GNU/Linux
paul@trusty-64:~$
```

The debs should be in ppa mainline shortly.

---

### Post by VinDSL on 2014-02-16
Hi Paul,

How do you like low-latency?

I've been thinking about installing it on my 'road warrior' but I don't want to kill the performance.

---

### Post by jorren on 2014-02-17
Is it me or are the 64-bit versions really missing on [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-rc3-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-rc3-trusty/)

---

### Post by zika on 2014-02-17
> **jorren said:**
> Is it me or are the 64-bit versions really missing on [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-rc3-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-rc3-trusty/)It is missing from daily (999) for some time now... Some journalists (as they often do) might even conclude that 64-bit is being depreciated... ;)

---

### Post by zika on 2014-02-17
> **VinDSL said:**
> Hi Paul,

How do you like low-latency?

I've been thinking about installing it on my 'road warrior' but I don't want to kill the performance.Sorry for answering to the question that was not &#8222;mine&#8220;... Because I do use my machine for HiFi I like it very much... ;) I do not see any significant performance degradation...

---

### Post by jorren on 2014-02-17
This is not a daily build I was referring to, but the 3.14-rc3 build.
There should be 64-bit packages for that one.

---

### Post by zika on 2014-02-17
> **jorren said:**
> This is not a daily build I was referring to, but the 3.14-rc3 build.
There should be 64-bit packages for that one.I was not refering to daily (999) build either... There are not 64-bit .debs for rc3 but that is due to the same reason because for days there are not 64-bit .debs for daily (999). That was all I wanted to say... ;)

---

### Post by jorren on 2014-02-17
I've seen 64-bit .debs on daily until last Thursday and also the rc2 last Friday was having 64-bit .debs
What went wrong this weekend?

---

### Post by zika on 2014-02-17
> **jorren said:**
> I've seen 64-bit .debs on daily until last Thursday and also the rc2 last Friday was having 64-bit .debs
What went wrong this weekend?Look at BUILD.LOG...
Last usable is 3.14.0-999-lowlatency #201402130457 ...
Cross-check 999 997 994 ...

---

### Post by Jhongy on 2014-02-17
I've been wondering about amd64 builds. I guess their amd64 build system is down for some days now.

Managed to compile 3.14-rc3 without problem.

---

### Post by jorren on 2014-02-17
I got this reply from the kernel team:

[I]Indeed they did not.  Seems the upstream code does not build for that
architecture:

ERROR: "__aeabi_uldivmod" [drivers/scsi/megaraid/megaraid_sas.ko] undefined!
ERROR: "__bad_udelay" [drivers/scsi/bfa/bfa.ko] undefined!
ERROR: "__bad_udelay" [drivers/net/ethernet/brocade/bna/bna.ko] undefined!

-apw[/I]

---

### Post by zika on 2014-02-17
> **jorren said:**
> I got this reply from the kernel team:

[I]Indeed they did not.  Seems the upstream code does not build for that
architecture:

ERROR: "__aeabi_uldivmod" [drivers/scsi/megaraid/megaraid_sas.ko] undefined!
ERROR: "__bad_udelay" [drivers/scsi/bfa/bfa.ko] undefined!
ERROR: "__bad_udelay" [drivers/net/ethernet/brocade/bna/bna.ko] undefined!

-apw[/I]...> **zika said:**
> Look at BUILD.LOG...

---

### Post by mrfelker on 2014-02-17
Yes the 64-bit headers   aand image are missing from the mainline.  Hope they show upl shortly

---

### Post by zika on 2014-02-18
There were at least two attempts today to build amd_64 packages...
Still waiting, .log shows the same place of failure...

---

### Post by jorren on 2014-02-18
Another try at 19.28 today...
Last errors to smash :)

cat BUILD.LOG | grep Error

make: *** [/home/apw/COD/linux/debian/stamps/stamp-build-perarch] Error 1
make[6]: *** [drivers/gpu/drm/msm/msm.o] Error 1
make[5]: *** [drivers/gpu/drm/msm] Error 2
make[4]: *** [drivers/gpu/drm] Error 2
make[3]: *** [drivers/gpu] Error 2
make[2]: *** [drivers] Error 2
make[1]: *** [sub-make] Error 2
make: *** [/home/apw/COD/linux/debian/stamps/stamp-build-generic] Error 2
make[6]: *** [drivers/gpu/drm/msm/msm.o] Error 1
make[5]: *** [drivers/gpu/drm/msm] Error 2
make[4]: *** [drivers/gpu/drm] Error 2
make[3]: *** [drivers/gpu] Error 2
make[2]: *** [drivers] Error 2
make[1]: *** [sub-make] Error 2
make: *** [/home/apw/COD/linux/debian/stamps/stamp-build-generic] Error 2

Hope to see new 64bit .debs soon :)

---

### Post by zika on 2014-02-19
999 (daily) is complete again... So, in short time, rc3 will be complete too I hope...

---

### Post by jorren on 2014-02-19
Yes, complete, but showing linux-...-3.1**3** not linux-...-3.1**4**
This should be 3.14 I would say or am I wrong?

---

### Post by slickymaster on 2014-02-19
> **jorren said:**
> Yes, complete, but showing linux-...-3.1**3** not linux-...-3.1**4**
This should be 3.14 I would say or am I wrong?

Yes, there's something wrong there. Presently, the folder content of v3.14-rc3-trusty, at [kernel-ppa/mainline]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-rc3-trusty/") are, apparently, the ones corresponding to v3.13-rc3-trusty.
[ATTACH=CONFIG]250483[/ATTACH]

---

### Post by zika on 2014-02-19
[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2014-02-19-trusty/BUILT](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2014-02-19-trusty/BUILT)
```
Release: precise 
Host: gomeisa 
Start: 1392800702 
Debian: trusty 
Configs: Ubuntu-3.14.0-0.1 
End: 1392803535
```
A bit of everything... ;)

---

### Post by zika on 2014-02-20
Now it has landed for real... ;)

---

### Post by slickymaster on 2014-02-20
It has indeed. :P

```
~$ lsb_release -a && uname -r

Distributor ID:    Ubuntu
Description:    Ubuntu Trusty Tahr (development branch)
Release:    14.04
Codename:    trusty
3.14.0-031400rc3-generic

```

Still using the pre-release VBoxGuestAdditions 4.3.7 though.

---

