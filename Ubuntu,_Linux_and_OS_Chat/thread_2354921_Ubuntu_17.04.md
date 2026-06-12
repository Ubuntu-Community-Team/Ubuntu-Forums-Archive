---
title: "Ubuntu 17.04"
date: 2017-03-07
forum: Ubuntu, Linux and OS Chat
---

### Post by neu5eeCh on 2017-03-07
My apologies if this thread is already out there.

I've had nothing but troubles with any Ubuntu Distro based on 16.04. I'm thinking of trying out 17.04, returning to Unity, and am wondering if 17.04 will come with Unity 8? --- as primary DE or as an option? Anyone using 17.04 Beta? How's it going?

---

### Post by lysander6662 on 2017-03-07
I'm curious as to *what kind of troubles *you've had with 16.04 [or distros based on it] since many, myself included, have had few. Yes, there are issues, but minor ones, all things considered.

---

### Post by neu5eeCh on 2017-03-07
> **lysander6662 said:**
> I'm curious as to *what kind of troubles *you've had with 16.04 [or distros based on it] since many, myself included, have had few. Yes, there are issues, but minor ones, all things considered.

Well, I don't want to get too far into it because ragging on 16.04 isn't the point of my post (and I'm not looking for support), but I'll be brief and leave it at that:

1.) All kinds of video problems involving Intel drivers: Flickering, missing fonts, artifacts, etc. As far as I can discern, and fairly reliably because there are many bug reports concerning these issues, the 4.4x Kernels are partly to blame; but also Ubuntu.

2.) Inability to access virtual terminals. Any of them. This too appears to be Kernel related.

3.) Needless regressions in Bluetooth functionality --- inability to use A2DP with bluetooth headsets for example (without a workaround script).

[https://gist.github.com/pylover/d68be364adac5f946887b85e6ed6e7ae](https://gist.github.com/pylover/d68be364adac5f946887b85e6ed6e7ae)

That still haven't been fixed.

4.) And rather than give you the grand tour: [http://www.dedoimedo.com/computers/ubuntu-xerus.html](http://www.dedoimedo.com/computers/ubuntu-xerus.html)

5.) [http://www.dedoimedo.com/computers/ubuntu-xerus-six-months-later.html](http://www.dedoimedo.com/computers/ubuntu-xerus-six-months-later.html)

Really frustrating stuff -- unstable, slow, full of regressions. But 16.04 works great for others. They'll be happy with another several years of support. Not me though. I've resigned myself to getting back on the 6 month release treadmill. Fortunately, I've pretty much got it down. I keep my Home folder in a separate partition, use Aptik and have a folder of scripts ready for easy reinstalls.

---

### Post by grahammechanical on 2017-03-08
> am wondering if 17.04 will come with Unity 8? --- as primary DE or as an option? Anyone using 17.04 Beta? How's it going?

As far as I know Unity 7 should be the primary DE with Unity 8 as a login option in the same way as Gnome Flashback or another DE would be presented as an option.

I have not tried the latest ISO image so I cannot say if Unity 8 is installed as part of the installation process or if we have a choice or if we still install Unity 8 afterwards. But I have been using 17.04 since the start of the development process and except for one very trying issue it has been fine. So, what is the problem? 17.04 no longer has Internet access and all the diagnostics that I run report that nothing is wrong and in fact it does have Internet access.

Two days ago I did an online upgrade of a 16.10 install that had Internet access and after 17.04 was installed and I rebooted this upgraded 17.04 also lost Internet access. So, I have 2 very usable 17.04 installations that cannot be online updated. 

Well, you did ask 'How is it going.' As far as Unity 8 is concerned I cannot get the desktop to load. After selecting Unity 8 and logging in it opens to frozen desktop without any app indicators in the top panel. This has been the situation for me since the start of 16.10 or even earlier. There have been the odd occasion when I did get a working Unity 8 desktop and it has promise and it should soon be possible to launch X apps such as Libreoffice which will run on an Xmir session in a window. 

I am beginning to think that Unity 8 needs more than the 1GB of RAM that I have in my machine.

Regards

---

### Post by night_sky2 on 2017-03-12
> **VTPoet said:**
> 1.) All kinds of video problems involving Intel drivers: Flickering, missing fonts, artifacts, etc. As far as I can discern, and fairly reliably because there are many bug reports concerning these issues,** the 4.4x Kernels are partly to blame**; but also Ubuntu.

AFAIK, Ubuntu 16.04.2 now ships with linux kernel 4.8. as part of the HWE.

You should try this release and see if it fixes you Intel drivers issues.

---

### Post by norafaithrainbow on 2017-03-15
> **grahammechanical said:**
> As far as I know Unity 7 should be the primary DE with Unity 8 as a login option in the same way as Gnome Flashback or another DE would be presented as an option.

I have not tried the latest ISO image so I cannot say if Unity 8 is installed as part of the installation process or if we have a choice or if we still install Unity 8 afterwards. But I have been using 17.04 since the start of the development process and except for one very trying issue it has been fine. So, what is the problem? 17.04 no longer has Internet access and all the diagnostics that I run report that nothing is wrong and in fact it does have Internet access.

Two days ago I did an online upgrade of a 16.10 install that had Internet access and after 17.04 was installed and I rebooted this upgraded 17.04 also lost Internet access. So, I have 2 very usable 17.04 installations that cannot be online updated. 

Well, you did ask 'How is it going.' As far as Unity 8 is concerned I cannot get the desktop to load. After selecting Unity 8 and logging in it opens to frozen desktop without any app indicators in the top panel. This has been the situation for me since the start of 16.10 or even earlier. There have been the odd occasion when I did get a working Unity 8 desktop and it has promise and it should soon be possible to launch X apps such as Libreoffice which will run on an Xmir session in a window. 

I am beginning to think that Unity 8 needs more than the 1GB of RAM that I have in my machine.

Regards

From what I've seen, Unity is a bit of a resource hog. I would suggest lxde or xfce, and maybe trying lubuntu or xubuntu instead.

---

