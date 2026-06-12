---
title: "Recording Studio Setup issues"
date: 2010-01-23
forum: Ubuntu Studio
---

### Post by Mars92 on 2010-01-23
Im trying to set up a recording studio on my computer, dual booting with windows 7. I installed Ubuntu 9.10 with Wubi then installed the linux-rt kernal along with all of the Ubuntu Studio packages excluding the design and animation packages. After all this is done I tried to boot Ubuntu with the Realtime kernal  from the GRUB boot menu and got this screen:
[IMG]http://img686.imageshack.us/img686/6567/sdc10153modified.jpg[/IMG]


After that I figured Id just try running the JACK server and see how low I could get the latency. After much fiddling with the settings this is what I got every time:
[IMG]http://img693.imageshack.us/img693/7913/screenshotey.png[/IMG]

So now Im at a loss. Anything that might help is much appreciated.

---

### Post by rogue_0111 on 2010-01-23
try this thread:

[http://ubuntuforums.org/showthread.php?t=1319086](http://ubuntuforums.org/showthread.php?t=1319086)

---

### Post by AutoStatic on 2010-01-24
Hello rogue_0111, regarding your JACK issue, you could either try unticking the 'Realtime' option in QjackCtl or configure your system with the help of this page: [https://help.ubuntu.com/community/UbuntuStudioPreparation#Real%20Time%20Kernel%20&%20Xruns](https://help.ubuntu.com/community/UbuntuStudioPreparation#Real%20Time%20Kernel%20&%20Xruns)

And that kernel panic error, maybe you could ask that in another forum (General or Installation & Upgrades), you'll probably get more helpful replies there.

---

