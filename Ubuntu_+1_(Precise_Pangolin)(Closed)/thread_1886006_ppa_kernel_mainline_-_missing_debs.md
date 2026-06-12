---
title: "ppa kernel mainline - missing debs"
date: 2011-11-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by paul_in_london on 2011-11-24
kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc3-oneiric/ and
kernel.ubuntu.com/~kernel-ppa/mainline/daily/2011-11-24-oneiric/

only have the *all.deb so we have to wait for 3.2-rc4 or for a daily to turn up with al the debs I suppose.

---

### Post by JMB74 on 2011-11-24
Looks like the build.log ended with an error, so those debs weren't made.

Has happened before that those mainline builds fail, but the rebased ubuntu kernel doesn't, so hopefully that will be available once the kernel team get around to it for the RC3?

---

### Post by paul_in_london on 2011-11-24
Yes, I've seen it happen before. The dailies sort themselves out, but the rcN directories seem to remain incomplete until rcN+1.

---

### Post by JMB74 on 2011-11-25
> **JMB74 said:**
> Has happened before that those mainline builds fail, but the rebased ubuntu kernel doesn't, so hopefully that will be available once the kernel team get around to it for the RC3?

A RC3 now building for the PP repos. :)

[https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-2.4](https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-2.4)

> linux (3.2.0-2.4) precise; urgency=low    

[ Andy Whitcroft ]    

* rebase to v3.2-rc3

---

### Post by paul_in_london on 2011-11-25
> **JMB74 said:**
> A RC3 now building for the PP repos. :)

[https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-2.4](https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-2.4)

That's good to know. Thanks for the heads-up. :)

---

### Post by VinDSL on 2011-11-26
> **JMB74 said:**
> A RC3 now building for the PP repos. :)

[https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-2.4](https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-2.4)
Hrm...

Just tried it, on this machine.

Same problem(s) as before - no network service - hangs on shutdown - blah, blah, blah.

Oh, well, I'll try it again when 3.2.0-2.5 arrives...  ;)

---

### Post by Harry33 on 2011-11-26
> **VinDSL said:**
> Hrm...

Just tried it, on this machine.

Same problem(s) as before - no network service - hangs on shutdown - blah, blah, blah.

Oh, well, I'll try it again when 3.2.0-2.5 arrives...  ;)

I am also going to test this 3.2-2.4 version (rc3) on my AMD setup.
Like I have said elsewhere, all these 3.2 versions work just fine on my Intel and Nvidia setups.
To be accurate (as this may be a mobo issue), I have an AMD chipset system (NB 790X, SB 750), on my Nvidia setup.

---

### Post by VinDSL on 2011-11-26
> **Harry33 said:**
> I am also going to test this 3.2-2.4 version (rc3) on my AMD setup.
Like I have said elsewhere, all these 3.2 versions work just fine on my Intel and Nvidia setups.
To be accurate (as this may be a mobo issue), I have an AMD chipset system (NB 790X, SB 750), on my Nvidia setup.
My rig is in my sig.  Hey, that almost rhythms... at least you could rap to it. :D

Never had these problems with any other kernel.  3.1.0-2-generic runs without a hiccup.

They'll get it, sooner or later.  They always do...  ;)

---

### Post by zika on 2011-11-26
The answer, my friend, is blowing with the wind... [http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-next/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-next/current/) :)

---

### Post by Harry33 on 2011-11-26
OK, tested this kernel 3.2-2.4 (rc 3) and it works with my AMD setup too.
Rebooting and shutting down is OK.

That desktop is this one:

Acer Aspire M5100
AMD Athlon 64 X2 Dual-Core 6000+ 3.0GHz
ATI Radeon HD 2600 Pro 256MB
Realtek ALC888
Gigabit Ethernet, Marvell

---

### Post by paul_in_london on 2011-11-26
Ok, I was a bit confused at first until I realised I had to get **linux-headers-3.2.0-2_3.2.0-2.4_all.deb** from the i386 page:

[https://launchpad.net/ubuntu/precise/i386/linux-headers-3.2.0-2/3.2.0-2.4](https://launchpad.net/ubuntu/precise/i386/linux-headers-3.2.0-2/3.2.0-2.4)

and then **linux-headers-3.2.0-2-generic_3.2.0-2.4_amd64.deb** and **linux-image-3.2.0-2-generic_3.2.0-2.4_amd64.deb** from here:

[https://launchpad.net/ubuntu/+source/linux/3.2.0-2.4/+build/2952345](https://launchpad.net/ubuntu/+source/linux/3.2.0-2.4/+build/2952345)

---

### Post by paul_in_london on 2011-11-26
> **zika said:**
> The answer, my friend, is blowing with the wind... [http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-next/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-next/current/) :)

Please forgive my ignorance about DRI/DRM, but I assume I might want to use the drm-next kernel version if, for example, I was using the open source nouveau graphics driver instead of the proprietary nvidia driver?

---

### Post by zika on 2011-11-26
> **paul_in_london said:**
> Please forgive my ignorance about DRI/DRM, but I assume I might want to use the drm-next kernel version if, for example, I was using the open source nouveau graphics driver instead of the proprietary nvidia driver?I did not suggest that anybody should use kernel from that location. I do, but that is another story. I just pointed into a direction of possible answer what is brewing and what is causing unsuccessful compilations of kernels in mainline...
I do not have experience with NVidia, so I can not answer Your question properly. Sorry...

---

### Post by paul_in_london on 2011-11-26
> **zika said:**
> I did not suggest that anybody should use kernel from that location. I do, but that is another story. I just pointed into a direction of possible answer what is brewing and what is causing unsuccessful compilations of kernels in mainline...
I do not have experience with NVidia, so I can not answer Your question properly. Sorry...

Ok, thanks zika. No problem. I'll have to do some reading!

---

### Post by zika on 2011-11-27
Mainline is back on &#8222;full steam ahead&#8220;...

---

### Post by JMB74 on 2011-11-28
> **paul_in_london said:**
> That's good to know. Thanks for the heads-up. :)

Working nicely here. :)

---

### Post by paul_in_london on 2011-11-28
Was back on the daily again, but another PP kernel update has just arrived via the repos:

```
paul@precise-64:~$ uname -a
Linux precise-64 3.2.0-2-generic #5-Ubuntu SMP Mon Nov 28 18:10:23 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
paul@precise-64:~$
```

---

### Post by VinDSL on 2011-11-29
> **paul_in_london said:**
> [...] another PP kernel update has just arrived via the repos [...]
I see that... Thanks!

I'll give it a try.

Wish me luck.  ;)

**EDIT**

n/m

Same ol'... same ol'

No network connection, and hangs on shutdown.

Wish I could say they're getting closer, but...

Oh, well, I'll try again, on the next go 'round.  :)

---

