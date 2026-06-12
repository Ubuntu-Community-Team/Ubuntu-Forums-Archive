---
title: "Crouton or Chrubuntu for VirtualBox?"
date: 2014-08-03
forum: Virtualisation
---

### Post by Domgoa on 2014-08-03
I am having difficulties starting virtualbox, when i try this error pops up.

'/etc/init.d/vboxdrv setup'

Could this be attributed to running Crouton on a Chromebook? 

Should i install Chrubuntu instead to fix this problem?

I have Googled the error to no avail so far.

I am running distribution 12.04 LTS Xfce on Acer C710.

I have installed Linux header 3.4 and dkms.

These videos show someone running Windows through Virtualbox on an Acer C7 Chromebook, so it is possible.

[Windows XP]("https://www.youtube.com/watch?v=yZpMHnHve5g&list=FL-IPouSLg_b9fyLVc-XFvhg&index=1")

[Windows 7]("https://www.youtube.com/watch?v=ykfQVqQsFfU&list=FL-IPouSLg_b9fyLVc-XFvhg&index=2")

---

### Post by Domgoa on 2014-08-03
Okay, i have been doing some research and it seems I've made progress in figuring this out. But i still need some more input on following the steps and executing them correctly.

It turns out that it is possible to run Crouton and virtualbox together without startup errors. [According to this person.]("http://www.reddit.com/r/chromeos/comments/2bz2e5/i_like_my_chromebook_acer_c720_better_than_my/")

[I am following these instructions.]("https://github.com/dnschneid/crouton/wiki/Build-kernel-headers-and-install-Virtualbox-(x86)") 

I'm stuck on how to move forward in the command line after I've ran the codes.

Code:
$ cd kernel
$ vi chromeos/config/base.config

I have changed, [COLOR=#333333][FONT=Helvetica]CONFIG_ERROR_ON_WARNING=y and made it CONFIG_ERROR_ON_WARNING=n

Now i need to know how to proceed forward in the command line to the next step.

Which is. I dont know how to get the command going to :~$ so i may enter the code.

Code:
[/FONT][/COLOR]$ ./chromeos/scripts/prepareconfig chromeos-intel-pineview
$ make oldconfig

---

