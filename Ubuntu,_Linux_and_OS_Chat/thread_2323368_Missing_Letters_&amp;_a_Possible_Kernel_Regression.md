---
title: "Missing Letters &amp; a Possible Kernel Regression"
date: 2016-05-04
forum: Ubuntu, Linux and OS Chat
---

### Post by neu5eeCh on 2016-05-04
So, upgrading to 16.04 has been a complete disaster on all my systems, and it seems it might have to do with the latest Kernel (not 16.04 specifically):

[http://askubuntu.com/questions/688306/text-missing-garbled-after-laptop-resumes-from-sleep-mode](http://askubuntu.com/questions/688306/text-missing-garbled-after-laptop-resumes-from-sleep-mode)

[http://www.spinics.net/lists/intel-gfx/msg82135.html](http://www.spinics.net/lists/intel-gfx/msg82135.html)

TTY doesn't work and if I switch to TTY and back, letters will start disappearing, rendering the system completely useless.

I'm not ready to give up on 16.04 yet, but might. Debian maybe? My question is this: Can any of you recommend a good guide to installing a different kernel? -- an earlier one possibly?

-----------------[B]

EDIT:[/B]  Okay, the good news is that I installed GRUB Customizer and now boot to 4.2.0-25-generic x86_64 (64 bit) rather than 4.4. So far, this has magically solved all my problems. This is the first time, since starting with 8.10, that I've ever had to switch out a kernel. 

Nevertheless, I'm still interested in any guides anyone can recommend in the event, let's say, that I wanted to install a Debian Kernel (on which Xenial is based).

---

### Post by buzzingrobot on 2016-05-04
You might also take at look at the mainline kernels, including the 4.6 RC candidates. 

The kernels are here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

and the explanations are here: [https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

Adding them is not difficult.  3 packages total.  Removing them is a matter of removing those three packages and rebooting. I've been using the 4.6 RC kernels with good results on a new Skylake machine.

You can also look up how to exclude a package from being updated, in case you want to stay with a specific kernel.

---

### Post by neu5eeCh on 2016-05-04
Thanks so much buzzing. I'll take a look at those.

I have to say: I'm completely blown away. Reverting back to 4.2 after Kernel 4.4 seems to have solved **_*all*_** these bugs:

1.) Missing mouse cursor after Suspend/Resume
2.) Missing Glyphs/Letters after TTY or Suspend/Resume
3.) Non-Fuctional TTY atter Suspend/Resume or Long Term Inactivity
4.) Graphic Resets
5.) Compositing failures and restarts.
6.) Missing Window Borders after Suspend/Resume or TTY.

---

### Post by neu5eeCh on 2016-05-11
> **buzzingrobot said:**
> You might also take at look at the mainline kernels, including the 4.6 RC candidates. 

Just following up. I installed the 4.6RC candidates and am having good results. No missing letters. No flickering panel. The TTY's continue to function. Thanks for those links.

---

