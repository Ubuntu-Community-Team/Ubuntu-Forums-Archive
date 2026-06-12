---
title: "libguestfs-winsupport"
date: 2022-03-22
forum: Virtualisation
---

### Post by snagara-07 on 2022-03-22
Hi, 

I don't see any package related to libguestfs-winsupport supported on ubuntu 21.10 impish.
 apt search libguestfs lists , all related to libguestfs other then winsupport, I wanted to know if ubuntu is supporting libguestfs-winsupport package ?

Kindly provide the input.

Regards,
Savitha

---

### Post by guiverc on 2022-03-22
No release of Debian/Ubuntu has that package - that name is a RedHat/CentOS package name as far as I can see.

Maybe try the Debian/Ubuntu package name

```
guiverc@d960-ubu2:/de2900/lubuntu_64$   rmadison libguestfs-tools
 libguestfs-tools | 1:1.24.5-1           | trusty/universe         | amd64, i386
 libguestfs-tools | 1:1.24.5-1ubuntu0.1  | trusty-updates/universe | amd64, arm64, armhf, i386, powerpc, ppc64el
 libguestfs-tools | 1:1.32.2-4ubuntu2    | xenial/universe         | amd64, arm64, armhf, i386, powerpc, ppc64el, s390x
 libguestfs-tools | 1:1.32.2-4ubuntu2.2  | xenial-updates/universe | amd64, arm64, armhf, i386, powerpc, ppc64el, s390x
 libguestfs-tools | 1:1.36.13-1ubuntu3   | bionic/universe         | amd64, arm64, armhf, i386, ppc64el, s390x
 libguestfs-tools | 1:1.36.13-1ubuntu3.3 | bionic-updates/universe | amd64, arm64, armhf, i386, ppc64el, s390x
 libguestfs-tools | 1:1.40.2-7ubuntu5    | focal/universe          | amd64, arm64, armhf, ppc64el, riscv64, s390x
 libguestfs-tools | 1:1.44.1-1ubuntu6    | impish/universe         | amd64, arm64, armhf, ppc64el, riscv64, s390x
 libguestfs-tools | 1:1.46.2-10ubuntu3   | jammy/universe          | amd64, arm64, armhf, ppc64el, riscv64, s390x

```

Checking [upstream]("https://libguestfs.org/") would have told you that.

---

### Post by deadflowr on 2022-03-22
*Thread moved to **Virtualization***

---

### Post by snagara-07 on 2022-03-22
Yes, I explored all the options of apt search on cli, requirement sections in man pages to build libguestfs -> [http://manpages.ubuntu.com/manpages/impish/man1/guestfs-faq.1.html](http://manpages.ubuntu.com/manpages/impish/man1/guestfs-faq.1.html) 
I see only in Redhat/Centos distribution. So my questions is, doesnt it need on ubuntu ?

---

