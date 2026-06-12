---
title: "Question with 3.3rc7 kernel"
date: 2012-03-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by DougieFresh4U on 2012-03-12
Just wondering why I am getting this message when trying to install the 
3.3rc7 kernel from the kernel main. 64 bit
Been getting it for about a week now. Have never had any issues with the kernel main before

---

### Post by dino99 on 2012-03-12
there is a new nux package actually built, maybe it will help, but 3.3 is not a Precise kernel anyway.

---

### Post by DougieFresh4U on 2012-03-12
> **dino99 said:**
>  but 3.3 is not a Precise kernel anyway.
I just wanted to give it a try, I know that the 3.3rc7 is not an 'official' kernal but it is listed as:**[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-rc7-precise/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-rc7-precise/")**

---

### Post by cariboo on 2012-03-12
You also need the header packages, breaking linux-image, only means that the kernel will not be updated automagically, when a new version comes out.

---

### Post by DougieFresh4U on 2012-03-14
> **cariboo907 said:**
> You also need the header packages
 Not sure if this is what you mean, but when I install kernels I always do the 
headers-all
headers-64amd
image-64amd
that order.
And the failure is when I am trying to install the image, as the headers 'appear' to install, correctly.

---

### Post by xebian on 2012-03-14
> **cariboo907 said:**
> You also need the header packages, breaking linux-image, only means that the kernel will not be updated automagically, when a new version comes out.

If you are not compiling anything like kernel modules, headers are not necessary.

---

### Post by cariboo on 2012-03-14
> **xebian said:**
> If you are not compiling anything like kernel modules, headers are not necessary.

That's true for some distro's, but the headers are dependencies of linux-image, and it won't install without them.

---

### Post by VinDSL on 2012-03-14
> **DougieFresh4U said:**
> Not sure if this is what you mean, but when I install kernels I always do the 
headers-all
headers-64amd
image-64amd
that order.
And the failure is when I am trying to install the image, as the headers'appear' to install, correctly.
I *know* that a lot of ppl prefer to install kernels in this-or-that order.

Personally, I simply download the 3 .debs to a folder, open a terminal window, cd to the folder, and let dpkg choose the order, e.g.

```
sudo dpkg -i *.deb
```

Just for giggles, you might want to try that...

---

### Post by xebian on 2012-03-17
> **cariboo907 said:**
> That's true for some distro's, but the headers are dependencies of linux-image, and it won't install without them.

Sorry but this is NOT TRUE.  I have no headers installed but don't tell me I have no linux-image.

```
root@kubu1:~# ac show linux-image
Package: linux-image
Priority: optional
Section: metapackages
Installed-Size: 31
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux-meta
Version: 3.2.0.19.21
[COLOR="Red"]**Depends: linux-image-generic (= 3.2.0.19.21)**[/COLOR]
Filename: pool/main/l/linux-meta/linux-image_3.2.0.19.21_amd64.deb
Size: 1704
MD5sum: 3b045e2e49f1eef03189564d98e2069e
SHA1: 3155ba82fbb5233541eaa853355f488d2f777661
SHA256: 4686a21ae1a56299a53f33e0cce0303a6b2be9acba92832b0773e496caa06e84
Description-en: Generic Linux kernel image.
 This package will always depend on the latest generic Linux kernel image
 available.
Description-md5: bbb651153b198d4cc1090132ccf7582b
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y

root@kubu1:~# ac show linux-image-generic
Package: linux-image-generic
Priority: optional
Section: metapackages
Installed-Size: 31
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux-meta
Version: 3.2.0.19.21
[COLOR="Red"]**Depends: linux-image-3.2.0-19-generic, linux-firmware**[/COLOR]
Filename: pool/main/l/linux-meta/linux-image-generic_3.2.0.19.21_amd64.deb
Size: 2448
MD5sum: 1e2eea524c217b7989c8b5a2a08f3396
SHA1: 720b9d1776a79f172e38f5b5b7348b5c670be0c8
SHA256: 8e8f9a0591aa6e4be3143b5775b416241be52c4d777e6a25affde94c94ab6b3f
Description-en: Generic Linux kernel image
 This package will always depend on the latest generic kernel image
 available.
Description-md5: 6d632579c673704f44b290b16e7dbfd1
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y

```

---

### Post by grandtoubab on 2012-03-18
Hello
+1 for sudo dpkg -i *.deb
Always proceed like this with no problem

---

