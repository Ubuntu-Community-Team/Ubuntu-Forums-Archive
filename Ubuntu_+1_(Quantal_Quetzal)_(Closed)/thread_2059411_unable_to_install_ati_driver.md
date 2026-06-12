---
title: "unable to install ati driver"
date: 2012-09-17
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by odror on 2012-09-17
OS: ubuntu 12.10
Video card ati hd 75xx

The repository ait driver will not install because of incompatibility of a pre req package. I get the following error:

> fglrx:
 Depends: xorg-video-abi-11  but it is not installable

I have download the 12.8 and 12.9 installers from ati. Generated deb packages and installed 

then typing: sudo aticonfig --initial -f

I get the following error for 12.8 and for 12.9

> adiconfig: No supported adapters detected

Any other ideas on how to install the ati driver

Thanks

---

### Post by QIII on 2012-09-17
Not likely possible until about the time of the RC.  The driver will not work with Quantal's version of X Server without patching. AMD has been providing the latest driver to Canonical in time for the RC for a number of years -- and Canonical gets the xx.4 and xx.10 drivers before they are even released to the general Linux public.

---

### Post by odror on 2012-09-17
> **QIII said:**
> Not likely possible until about the time of the RC.  The driver will not work with Quantal's version of X Server without patching. AMD has been providing the latest driver to Canonical in time for the RC for a number of years -- and Canonical gets the xx.4 and xx.10 drivers before they are even released to the general Linux public.
When looking at the announce 12.10 release schedule I do not see RC release. There is beta 2 on 9/27 and final on 10/18. Is beta 2 considered to be the RC release. Thanks

---

### Post by cariboo on 2012-09-18
Have you checked out [this]("http://ubuntuforums.org/showthread.php?t=1988444") thread, to see if there is a solution to your problem?

If you look [here]("https://wiki.ubuntu.com/QuantalQuetzal/ReleaseInterlock"), you'll see the RC is scheduled to be released Oct. 11/12

---

### Post by mips on 2012-09-18
Don't have a ati gpu and I know nothing about them but you could always have a look at,

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
[https://launchpad.net/ubuntu/quantal/+source/fglrx-installer/2:8.982-0ubuntu1](https://launchpad.net/ubuntu/quantal/+source/fglrx-installer/2:8.982-0ubuntu1) from the above link.

---

### Post by balloons on 2012-09-18
Are you running into this?

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1032672](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1032672)

---

### Post by odror on 2012-09-18
> **guitara said:**
> Are you running into this?

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1032672](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1032672)

yes

---

### Post by QIII on 2012-09-18
The answer is mentioned in that report and it is the same as I said.

The current driver is not compliant with the version of X Server and we will have to wait until late in the cycle for AMD/ATI to provide it.  This usually happens around the time of the RC.

Otherwise you will have to follow instructions for applying a patch.

AMD/ATI will bend over backwards to support Ubuntu.  It has for years and the rest of the Linux community gripes about it.

Do as is suggested in that bug report:  use the open source driver until the new fglrx driver has been made available by AMD for inclusion in the Ubuntu repo.

That or do the patch.

This is simple:  It ain't going to work unless you patch.  Patience.

---

