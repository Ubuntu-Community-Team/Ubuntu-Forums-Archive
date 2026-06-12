---
title: "Kernel Source Package"
date: 2004-12-03
forum: Repositories &amp; Backports
---

### Post by brainchill on 2004-12-03
First I will preface this by saying I love ubuntu. I'm just having one little question/problem.

I have used apt to update my system and am running the most current kernel
the problem is that I am looking to build a few things that require that I have the configured source for my running kernel. This is the hitch that I ran into ... the kernel source package is only listed at version 2.5.7 or something not the same version that the system is running. (2.6.x)

Obviously I could build a new kernel from fresh source and have everything that I need but for what I am trying to do it's a bit extreme.

---

### Post by adbak on 2004-12-03
Perhaps you can upgrade to Hoary, I'm pretty sure it would use a newer kernel.

---

### Post by BravoCharlie on 2004-12-03
apt-get install linux-source-2.6.8.1

or if you just need the headers:

apt-get install linux-headers-2.6.8.1-386

(just do a "uname -r" first to check your exact version)

---

### Post by abazimi on 2007-09-22
in ubuntu 7.04  (feisty fawn) you should just enter this command
sudo apt-get install linux-source
or
sudo aptitude install linux-source

---

