---
title: "Ubuntu touch iso?"
date: 2016-03-24
forum: Ubuntu Phone and Tablet
---

### Post by chrhelling on 2016-03-24
Hi, is it possible to get the Ubuntu touch iso? gonne try to install it on my Surface and play around With it. would be Nice to get the Surface the way the New tablet is working :D

---

### Post by howefield on 2016-03-24
Not an iso but image files are available for compatible devices..

[http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/)
[http://cdimage.ubuntu.com/ubuntu-touch/daily-preinstalled/current/](http://cdimage.ubuntu.com/ubuntu-touch/daily-preinstalled/current/)
[https://wiki.ubuntu.com/Touch/Devices](https://wiki.ubuntu.com/Touch/Devices)
[http://developer.ubuntu.com/en/start/ubuntu-for-devices/devices/](http://developer.ubuntu.com/en/start/ubuntu-for-devices/devices/)

---

### Post by chrhelling on 2016-03-24
after some searhing i found out that ubuntu desktop Next was somthing i had a long time ago...
any Place to get this iso?

---

### Post by grahammechanical on 2016-03-24
I believe I explained the situation a little bit in this post

[http://ubuntuforums.org/showthread.php?t=2318132](http://ubuntuforums.org/showthread.php?t=2318132)

As far as I understand Ubuntu for Devices is still based on 15.04 (vivid) code. It was not re-based on 15.10 (wily) code. I expect that over the coming months it will be re-based on 16.04 (xenial) code as that is Long Term Support.

There are other factors involve in this development such as the change over from Click packaging to Snap packaging and the re-basing of Ubuntu on Snappy Ubuntu Core.

A some months ago a couple of us were experimenting with Ubuntu Personal or Snappy Ubuntu Desktop Next as it was called by the printout we got when we logged in at tty1.

That did not come as an ISO image but an image file which could be put on a USB stick using the Disks utility's Restore Image function. That was built on wily code. It had transactional updates. It was Snappy Ubuntu core with the Unity 8 desktop and running on Mir. It worked quiet well. I even used the restore image function to put it on a 250 GB hard disk. It was impossible to install any apps. I think that was because Ubuntu Personal was an x86 image and the apps in the phone app store are built to run on ARM CPUs.

But new images were not created once the development of xenial began. So, the experiment came to an end. It was a useful proof of concept. I am hoping that this line of development will restart as a build on xenial code once 16.04 is released. I am hoping to get access to a development version image for testing purposes. An ISO image would be nice. This has to be tested by real users after all before a general release.

But when it comes to general release, the decision has been made that a Unity8/Mir version of converged Ubuntu (that is the target) for x86 CPUs will not become default until it is worthy of being released. If we get something by the end of October this year that will be great but no one is promising that. If anything they are talking down that expectation.

Regards.

---

