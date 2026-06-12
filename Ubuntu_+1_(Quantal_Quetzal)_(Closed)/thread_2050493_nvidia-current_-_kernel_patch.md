---
title: "nvidia-current - kernel patch"
date: 2012-08-31
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-08-31
For those using 3.6 branch kernel and nvidia-current:
do not upgrade to the latest nvidia-current_304-0ubuntu2 from QQ official repos.

The 3.6 kernel patch has been dropped now.
QQ will stay with linux 3.5. branch.

---

### Post by mc4man on 2012-08-31
Maybe 3.6 doesn't need a patch
(the patch couldn't be applied as written
According to a couple of users here 3.6 & nvidia-current-304.43 work ok (they were using the one from xedgers were the patch was commented out (paul_in_london, VinDSL
-PATCH[0]="buildfix_kernel_3.6.patch"
-PATCH_MATCH[0]="^3.6"
+#PATCH[0]="buildfix_kernel_3.6.patch"
+#PATCH_MATCH[0]="^3.6

---

### Post by paul_in_london on 2012-08-31
The other day I had to reinstall the xorg-edgers version of nvidia-current 304.43 after it was upgraded to an official version of 304.43 from the main repos because the repo version failed to build with kernel 3.6-rc3.

Not at home right now so I can't post the exact version details, but last night after another update the main (official) repo version of nvidia-current 304.43 did build ok for me with 3.6-rc3.

---

### Post by VinDSL on 2012-08-31
> **paul_in_london said:**
> The other day I had to reinstall the xorg-edgers version of nvidia-current 304.43 after it was upgraded to an official version of 304.43 from the main repos because the repo version failed to build with kernel 3.6-rc3.[...]
Confirmed... ;)

LINKAGE:  [http://ubuntuforums.org/showpost.php?p=12205855&postcount=58](http://ubuntuforums.org/showpost.php?p=12205855&postcount=58)

---

### Post by Bowmore on 2012-08-31
No problems here, running 
- kernel 3.6.0-030600rc3.201208221735
- nvidia-current 304.43-0ubuntu2

Strange that it works for some people only :confused:

---

### Post by mc4man on 2012-08-31
> **Bowmore said:**
> No problems here, running 
- kernel 3.6.0-030600rc3.201208221735
- nvidia-current 304.43-0ubuntu2

Strange that it works for some people only :confused:

It may be just those that tried ...0ubunt1 (or equivalent from xorg-edgers

---

### Post by Bowmore on 2012-08-31
> **mc4man said:**
> It may be just those that tried ...0ubunt1 (or equivalent from xorg-edgersProbably the case ;)

---

### Post by paul_in_london on 2012-09-01
This version is fine with kernel 3.6-rc3:

```
paul@quantal-64:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 304.43-0ubuntu2
  Candidate: 304.43-0ubuntu2
  Version table:
 *** 304.43-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/restricted amd64 Packages
        100 /var/lib/dpkg/status
     304.43-0ubuntu1~xedgers~quantal2 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main amd64 Packages
paul@quantal-64:~$ 
```

---

### Post by VinDSL on 2012-09-02
> **paul_in_london said:**
> This version is fine with kernel 3.6-rc3

Works fine with 3.6-rc4 too...  ;)
```
indsl@Zuul:~$ apt-cache policy nvidia-current && apt-cache policy linux-image-3.6.0-030600rc4
nvidia-current:
  Installed: 304.43-0ubuntu2
  Candidate: 304.43-0ubuntu2
  Version table:
 *** 304.43-0ubuntu2 0
        500 http://mirrors.se.eu.kernel.org/ubuntu/ quantal/restricted i386 Packages
        100 /var/lib/dpkg/status
     304.43-0ubuntu1~xedgers~quantal2 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main i386 Packages
linux-image-3.6.0-030600rc4-generic:
  Installed: 3.6.0-030600rc4.201209011435
  Candidate: 3.6.0-030600rc4.201209011435
  Version table:
 *** 3.6.0-030600rc4.201209011435 0
        100 /var/lib/dpkg/status
vindsl@Zuul:~$
```

---

### Post by paul_in_london on 2012-09-02
> **VinDSL said:**
> Works fine with 3.6-rc4 too...  ;)
```
indsl@Zuul:~$ apt-cache policy nvidia-current && apt-cache policy linux-image-3.6.0-030600rc4
nvidia-current:
  Installed: 304.43-0ubuntu2
  Candidate: 304.43-0ubuntu2
  Version table:
 *** 304.43-0ubuntu2 0
        500 http://mirrors.se.eu.kernel.org/ubuntu/ quantal/restricted i386 Packages
        100 /var/lib/dpkg/status
     304.43-0ubuntu1~xedgers~quantal2 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main i386 Packages
linux-image-3.6.0-030600rc4-generic:
  Installed: 3.6.0-030600rc4.201209011435
  Candidate: 3.6.0-030600rc4.201209011435
  Version table:
 *** 3.6.0-030600rc4.201209011435 0
        100 /var/lib/dpkg/status
vindsl@Zuul:~$
```

Hi Vin,

Yep - I installed 3.6-rc4 last night.

Cheers,

Paul

---

