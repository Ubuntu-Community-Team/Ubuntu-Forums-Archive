---
title: "Real Time Kernel"
date: 2010-05-03
forum: Ubuntu Studio
---

### Post by Chtfn on 2010-05-03
Hello everyone.

I installed Ubuntu Studio 10.04 a few days ago, and I installed the real time kernel today via the Software Center.
Now, how can I use it? It always uses the generic kernel, and Grub is installed but doesn't ask me which one I want to use when I boot the computer...

Thanks for your help.

---

### Post by trulan on 2010-05-03
Ubuntu must be your only OS.  That's OK, you just need to manually change grub2's hidden timeout setting.

```
sudo gedit /etc/default/grub
```
Find the line (near the top) that says:
```
GRUB_HIDDEN_TIMEOUT=0
```
And delete the zero, so it looks like this:
```
GRUB_HIDDEN_TIMEOUT=
```
Then check the GRUB_TIMEOUT line, which is the time the grub menu will show, in seconds.
```
GRUB_TIMEOUT=10
```
Almost done!  Save the file and close gedit.  Then, run this:
```
sudo update-grub
```to write your changes to the grub menu settings.

You should now be able to reboot and select your new kernel.

---

### Post by Chtfn on 2010-05-04
Thank you very much for your answer! It is very easy to understand. But, actually, just before I read it, I found Startup-manager and installed it, it was really easy to change from generic to rt.

Thanks for your help!

---

### Post by WestCoastSuccess on 2010-05-17
Does real time pre-emption work in 10.04? It's been broken, as far as we know, since 8.04 - all our studio machines use 8.04 for that reason.

---

### Post by trulan on 2010-05-17
What do you mean by broken?  There are often issues with permissions settings, but they are easily corrected.  Some of the kernels have had problems, that's a much more serious issue.

Here's a brief summary of Real Time preemption in Ubuntu:
8.04 Hardy Heron - excellent rt kernel.
8.10 Intrepid Ibex - rt kernel was removed due to serious problems in this release.
9.04 Jaunty Jackalope - rt kernel works on some machines, locks up on others.
9.10 Karmic Koala - excellent rt kernel - a few complaints of problems.
10.04 Lucid Lynx - no rt patch exists for the 2.6.32 kernel series (Lucid's generic kernel).  The kernel from Karmic is available in the repositories and 2.6.33-rt is available in a ppa.

So real time preemption can be gotten to work in 10.04, but it's not quite as simple as we wish it would be.

---

### Post by thorgal on 2010-05-17
don't want to confuse ppl but you should first give a try at SCHED_FF scheduling (aka "RT") with the vanilla kernel (2.6.32) before jumping on the RT patched one. Lots of the "RT" patch has been merged to the kernel baseline. I experience no issue at all on my system with a vanilla kernel. Not that it should be the same for everyone because of this but a first try with the vanilla kernel is no big deal, so you can see for yourself whether it cuts it.
If not, then the RT patched one should be the next step. 

Of course, you need a "preemptable" kernel so the vanilla kernel needs to have been compiled with this option. Another thing, no sure how the "cgroup" feature interferes with RT operations, but I saw in another forum some boot log that showed that "cgroup" was enabled in the packaged kernel. IIRC, it had some influence on the RT priviledges configuration but I am not 100% sure.

---

### Post by WestCoastSuccess on 2010-05-17
Trulan: you've answered your own question - your summary of the problems with rt kernels is precisely why we haven't upgraded any of our machines. We use 8.04 with a latency of 0.7ms when recording using Ardour, and won't sacrifice the latency. 

We were hoping to see:

10.04 Lucid Lynx - excellent rt kernel, full stop.

---

### Post by svenskmand on 2010-05-17
> **trulan said:**
> Ubuntu must be your only OS. ...
This does not make any sense to me, why would this be necessary? You are simply loading another kernel than the generic right?, please explain :)

---

### Post by sgx on 2010-05-18
> **svenskmand said:**
> This does not make any sense to me, why would this be necessary? You are simply loading another kernel than the generic right?, please explain :)
Hi, if I read it right, the problem was the second kernel that was installed was not available to choose, because the choice screen was
open for 0 seconds, meaning the default kernel loaded immediately.
Changing the timeout to 10 seconds, gives the user time to ponder
the choices. The default would still load at 10 seconds, in the absence of a users choice. 

Cheers

---

### Post by eric71 on 2010-05-18
> **svenskmand said:**
> This does not make any sense to me, why would this be necessary? You are simply loading another kernel than the generic right?, please explain :)

It's a weird default setting in the last few releases of Ubuntu - if you are not dual booting with another operating system, Grub2 does not show the menu by default. Even if the timeout is set to 10 seconds. You need to comment out the /etc/default/grub GRUB_HIDDEN_TIMEOUT as explained above by trulan.

This setting annoys me because it assumes that you won't be using multiple kernels, but I suppose in the majority of cases people aren't. But for those of us using the RT kernel, it would be nice to not have to edit configuration files. I installed the ppa 2.6.33-rt kernel last night, and it became the default. Which is fine, but for times when I'm not using my laptop for recording I'd prefer to select the regular kernel, for better battery life, suspend and hibernation.

---

### Post by falkTX on 2010-05-18
> **eric71 said:**
> It's a weird default setting in the last few releases of Ubuntu - if you are not dual booting with another operating system, Grub2 does not show the menu by default. Even if the timeout is set to 10 seconds. You need to comment out the /etc/default/grub GRUB_HIDDEN_TIMEOUT as explained above by trulan.

This setting annoys me because it assumes that you won't be using multiple kernels, but I suppose in the majority of cases people aren't. But for those of us using the RT kernel, it would be nice to not have to edit configuration files. I installed the ppa 2.6.33-rt kernel last night, and it became the default. Which is fine, but for times when I'm not using my laptop for recording I'd prefer to select the regular kernel, for better battery life, suspend and hibernation.

You just have to hold "Shift" before grub loads (right after the BIOS screen), and it will show the menu.
Do not forget that

---

### Post by svenskmand on 2010-05-18
Ok thanks for explaining, because I did think that it was a weird claim. Although I see now that you can also read the statement otherwise.

---

### Post by eric71 on 2010-05-18
> **falkTX said:**
> You just have to hold "Shift" before grub loads (right after the BIOS screen), and it will show the menu.
Do not forget that

Thanks, I had forgotten that :)

---

