---
title: "Bumblebee and kernel 3,8"
date: 2013-02-21
forum: Ubuntu Development Version
---

### Post by ZootNerper on 2013-02-21
Hi.

I run Ubuntu 12.10 with all the updates and standard set up on an Acer Aspire laptop with NVidia Optimus. I have installed Bumblebee which works most of the time.

I would just like to know if Bumblebee works with the latest 3.8 kernel.

I tried installing the kernel 3.8 and my computer booted normally with no problems. But after installing Bumblebee, I couldn't get Bumblebee to work (couldn't access the GPU).

I have since re-installed Ubuntu 12.10 and Bumblebee so I am back at a known starting point.

I would just like to know a yes or no answer. If you know of a link that might help, I would appriciate it. (I think if it works I have to edit some config files)

-- Zoot

---

### Post by Budovi on 2013-02-21
I'm running bumblebee on 13.04 just fine, with Raring updated kernel (Linux ubuntu 3.8.0-7-generic). I also had mainline stable 3.8 kernel but I haven't tried, if you mean this version. Later I purged it, because it did not solve my actual problem.

Difference is, that I'm using ppa:bumblebee/testing (which is also for Raring) and I have Nvidia 304 version driver, so I had to edit bumblebee.conf to get it work. So check your configuration file or you can try development version of bumblebee.

---

### Post by ZootNerper on 2013-02-21
Thanks Budovi. That is just the information I needed. I will try again with the Bumblebee/testing and edit the config. I have some information on the latter.

I will post any results for others to follow.

:)

---

