---
title: "intel-microcode no longer required?"
date: 2018-12-26
forum: Ubuntu Development Version
---

### Post by corradoventu on 2018-12-26
On my Disco Dingo with Kernel: 4.20.0-042000-generic x86_64 and proposed enabled doing upgrade i received this message:```
corrado@corrado-p13-dd-1107-x:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  amd64-microcode intel-microcode iucode-tool libbind9-160 libdns-export1102 libdns1102 libgail-3-0
  libhunspell-1.6-0 libicu60 libirs160 libisc-export169 libisc169 libisccc160 libisccfg160 liblwres160
  libopencv-core3.2 libopencv-imgproc3.2 liborcus-0.13-0 libpoppler79 libprotobuf10 libraw16 libssl1.0.0
  libtbb2 libx264-152 libx265-160 linux-headers-4.18.0-10 linux-headers-4.18.0-10-generic
  linux-headers-generic linux-image-4.18.0-10-generic linux-modules-4.18.0-10-generic
  linux-modules-extra-4.18.0-10-generic thermald
Use 'sudo apt autoremove' to remove them.
```
I have these microcode installed ```
corrado@corrado-p13-dd-1107-x:~$ apt policy *-microcode
intel-microcode:
  Installed: 3.20180807a.2
  Candidate: 3.20180807a.2
  Version table:
 *** 3.20180807a.2 500
        500 http://archive.ubuntu.com/ubuntu disco/main amd64 Packages
        100 /var/lib/dpkg/status
amd64-microcode:
  Installed: 3.20180524.1ubuntu1
  Candidate: 3.20180524.1ubuntu1
  Version table:
 *** 3.20180524.1ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu disco/main amd64 Packages
        100 /var/lib/dpkg/status
corrado@corrado-p13-dd-1107-x:~$ 


```

---

### Post by dino99 on 2018-12-26
Using synaptic to check these microcode files, they are listed as 'dependants' of linux-image-generic at least for the genuine 4.19 kernel.
But for the latest 4.20 kernel, we can imagine it manage itself all the addons provided by the microcode files (which are several months old now).

---

### Post by zika on 2018-12-26
> **dino99 said:**
> Using synaptic to check these microcode files, they are listed as 'dependants' of linux-image-generic at least for the genuine 4.19 kernel.
But for the latest 4.20 kernel, we can imagine **it manage itself all the addons provided by the microcode files** (which are several months old now).Not the lowlatency branch, only generic one...

---

### Post by corradoventu on 2019-01-04
Received a reply: [https://answers.launchpad.net/ubuntu/+source/intel-microcode/+question/677313](https://answers.launchpad.net/ubuntu/+source/intel-microcode/+question/677313)

---

