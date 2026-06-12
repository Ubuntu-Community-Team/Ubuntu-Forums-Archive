---
title: "Ubuntu JeOS - glibc 2.8"
date: 2008-11-22
forum: Server Platforms
---

### Post by prickly on 2008-11-22
I am following instructions that say I need glibc 2.8.

I have issued the following command and it insalls glibc 2.7:

sudo apt-get install glibc-source

A google search for glibc 2.8 takes me to some ubuntu / intrepid bug pages, so my question is should I try to install a version of glibc 2.8 onto Ubuntu JeOS? Will it work or should I wait for the respositories to be updated with glibc 2.8?

Many thanks!

---

### Post by Thirtysixway on 2008-11-22
Try installing either libc6 or libc6-dev

sudo apt-get install libc6
sudo apt-get install libc6-dev

---

### Post by prickly on 2008-11-23
> **Thirtysixway said:**
> Try installing either libc6 or libc6-dev

Thanks very much for the reply - libc6 is already installed on JeOS and was not enough to get the job done (nor was libc6-dev).

So I have proceeded with a minimal virtual machine install of Ubuntu Server 8.1 (Intrepid Ibex) which has glibc 2.8 in the repos. 

:grin:

---

