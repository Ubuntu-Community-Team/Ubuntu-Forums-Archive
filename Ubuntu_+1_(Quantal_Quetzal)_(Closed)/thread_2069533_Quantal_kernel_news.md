---
title: "Quantal kernel news"
date: 2012-10-11
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by cariboo on 2012-10-11
This just show up in my inbox:

> Hi All,

Now that we are past the Ubuntu Quantal Quetzal 12.10 Kernel Freeze, the Ubuntu Kernel Team felt this would be an appropriate time to officially confirm and announce that the Ubuntu 12.10 kernel will be based on the upstream v3.5 Linux kernel [1].  Going forward, we'll continue to update the Ubuntu 12.10 kernel with the latest upstream v3.5.y Linux stable kernel releases.  For those seeking the specific details of all the changes provided in the Ubuntu 12.10 kernel, please refer to the ubuntu-quantal git repository [2].  We've also categorized the Ubuntu specific changes in our QKernelDeltaReview wiki for anyone interested [3].

Thanks,
The Ubuntu Kernel Team

[1] [http://www.kernel.org/pub/linux/kernel/v3.x/linux-3.5.tar.gz](http://www.kernel.org/pub/linux/kernel/v3.x/linux-3.5.tar.gz)
[2] [http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-quantal.git;a=summary](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-quantal.git;a=summary)
[3] [https://wiki.ubuntu.com/KernelTeam/Specs/QKernelDeltaReview](https://wiki.ubuntu.com/KernelTeam/Specs/QKernelDeltaReview)

---

### Post by dino99 on 2012-10-11
its really a bad news, 3.6 is way better than 3.5

---

### Post by pqwoerituytrueiwoq on 2012-10-11
> **dino99 said:**
> its really a bad news, 3.6 is way better than 3.5
personally i did not see much of a difference, maybe i would have if i knew what i was looking for before i switched to 3.6.1, i have my mom on 3.5.X, so maybe i will eventually
easy enough to upgrade
i even made a short script to do it
**edit: attachment 2 is the working one, it fixes a 404 error**

---

### Post by fyfe54 on 2012-10-11
I'm using 3.6.1 too, and it seems solid and snappy.

---

### Post by HansKisaragi on 2012-10-11
I can't say iv noticed a difference but then again I haven not tried it much.

any idea when the RC will be out today?

---

### Post by AlexGogolev on 2012-10-11
There is a problem with the 3.5 kernel. Here is the link [https://lkml.org/lkml/2012/8/20/675](https://lkml.org/lkml/2012/8/20/675)

And since 3.6.1 is out 4 days ago we got the unsupported kenel in 12.10, so it's a canonical fail.

---

### Post by pompel9 on 2012-10-11
> **AlexGogolev said:**
> There is a problem with the 3.5 kernel. Here is the link [https://lkml.org/lkml/2012/8/20/675](https://lkml.org/lkml/2012/8/20/675)

And since 3.6.1 is out 4 days ago we got the unsupported kenel in 12.10, so it's a canonical fail.


That page doesn't mention anything wrong with kernel 3.5.

It only lists the support plan for kernel 3.4, 3.5 and 3.6.

---

### Post by thotz on 2012-10-11
> **AlexGogolev said:**
> There is a problem with the 3.5 kernel. Here is the link [https://lkml.org/lkml/2012/8/20/675](https://lkml.org/lkml/2012/8/20/675)

And since 3.6.1 is out 4 days ago we got the unsupported kenel in 12.10, so it's a canonical fail.

Yeah I read this. But I don't think Canonical failed. They will provide support for the 3.5 kernel the next 18 months.

---

### Post by ronacc on 2012-10-11
I guess 12.10 testing cycle is going to be as much a disaster for me as quantal was . The 3.5 kernel really hates my box .

OOPS misread the  OP , too early . disregard , I confused 12.10 with  the upcomming 13.04 .

---

### Post by grahammechanical on 2012-10-11
@ pqwoerituytrueiwoq

Thanks for that script. I was wondering how to install 3.6.

Regards.

---

### Post by mc4man on 2012-10-11
> **pqwoerituytrueiwoq said:**
> 
i even made a short script to do it

```
wget $WHERE/linux-headers-$VER_A"_$VER_A"."$VER_B"_all.deb
```
would be the only way it would work here

---

### Post by AlexGogolev on 2012-10-11
> **thotz said:**
> Yeah I read this. But I don't think Canonical failed. They will provide support for the 3.5 kernel the next 18 months.

How they can provide support if the kernel is not maintained by the maintainer? And here is another Greg's post [https://lkml.org/lkml/2012/10/7/110](https://lkml.org/lkml/2012/10/7/110) saying the will be probably one more 3.5.x kernel release and asks everybody to move to 3.6 branch.

---

### Post by jrog on 2012-10-11
> **AlexGogolev said:**
> How they can provide support if the kernel is not maintained by the maintainer? And here is another Greg's post [https://lkml.org/lkml/2012/10/7/110](https://lkml.org/lkml/2012/10/7/110) saying the will be probably one more 3.5.x kernel release and asks everybody to move to 3.6 branch.
I'm with you on this one. Even if they could provide support for it, why support an otherwise unsupported kernel?

---

### Post by philinux on 2012-10-11
Has anyone raised a bug report on this.

> **AlexGogolev said:**
> How they can provide support if the kernel is not maintained by the maintainer? And here is another Greg's post [https://lkml.org/lkml/2012/10/7/110](https://lkml.org/lkml/2012/10/7/110) saying the will be probably one more 3.5.x kernel release and asks everybody to move to 3.6 branch.

---

### Post by pqwoerituytrueiwoq on 2012-10-11
> **grahammechanical said:**
> @ pqwoerituytrueiwoq

Thanks for that script. I was wondering how to install 3.6.

Regards.
it is based on VinDSL's instructions
> **mc4man said:**
> ```
wget  $WHERE/linux-headers-$VER_A"_$VER_A"."$VER_B"_all.deb
```would be the  only way it would work here
opps *makes new attachment for [my other post](http://ubuntuforums.org/showpost.php?p=12289480&postcount=3)*

---

### Post by lemming465 on 2012-10-11
In answer to dino99, if you or your hardware hate 3.5, then either run a newer kernel, switch to the 13.04 alpha when that comes out, or stick on 12.04.  No one is going to force anyone to install 12.10, which admittedly is looking like one of the buggier releases from Ubuntu, at least to me.  At the beta1 stage 5 of 6 systems I tried it on had either nasty video artifacts or complete failures, on a mixture of intel, ATI/AMD/Radeon and Nvidia chips.  Beta two was a lot better, but still had major problems for me on 2 of 6.

Between the KMS churn in the kernel and the forthcoming wayland churn in the video stack, we are probably another 2 years away from having reliable, well performing video on Linux.

In answer to pompel9 and AlexGogolev, and following thotz, Canonical supports kernels the same way as Redhat or SuSE or Slackware or any distribution does: they cherry-pick useful looking fixes from upstream and backport them.

The upstream kernel community has scores of kernel trees, some ahead of the official Linus Torvalds tree, some behind.  This week, when kernel 3.N is released, the upstream community stops backporting security and bug fixes to 3.(N-2), unless that was blessed as a multiyear stable kernel. (New functionality is never backported by upstream, only simple bug fixes).  Downstream, distributions continue backporting fixes during their own support lifecycles, regardless of what version the upstream kernel has crept to.  Redhat enterprise kernels, for example, are notorious for being hundreds or thousands of patches different from their nominal base version.  Read some of the back articles on LWN.NET or anywhere that reports on kernel summits such as [this 2010 article]("https://lwn.net/Articles/407525/") to get a better feel for the historical relationships between real-time, embedded, development, official, and stable variants.   But expect to have to keep reading; it's a rare year where something doesn't change in the kernel development process somewhere.

Currently Linus is releasing about 4 kernels per year, and Canonical likes to stabilize for at least two months or so before shipping, so typically an Ubuntu kernel will be off upstream support by the time it ships, and the next Ubuntu release will jump at least 3 kernel versions from the previous one, e.g. Precise used 3.2, Quantal is using 3.5, and 13.04 will probably ship with 3.8 (3.6 *just* shipped, and the 3.7 merge window is still open).  This is all very normal.

---

