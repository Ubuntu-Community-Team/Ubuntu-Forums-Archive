---
title: "Jaunty's Real Time Kernel Doesn't Load"
date: 2009-04-23
forum: Ubuntu Studio
---

### Post by bandgeek on 2009-04-23
When Jaunty came out I installed the Ubuntu Studio Audio and Graphics packages using Synaptic.

I restarted and selected the Real Time Kernel from GRUB menu and it didn't load.:( All that happened is the progress bar moved a little bit then switched to text mode. It had stopped at loading restricted modules. After letting the computer sit for about an hour I hard powered down.

So then I restarted in the normal kernel and reinstalled the linux-rt meta-package. It still didn't work.:(

Also none of the audio applications show in the menu except for LMMS :confused:Graphics however show and work.

Dell XPS 400
Pentium D 2.80 Ghz
ATI 300 Video Card
Jaunty Jackalope 9.04

---

### Post by pljones on 2009-04-25
That'll be your ATI card, that will...

There's maybe a workaround, if you don't mind getting your hands dirty, here:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?msg=39;att=0;bug=420842](http://bugs.debian.org/cgi-bin/bugreport.cgi?msg=39;att=0;bug=420842)
(I would suggest taking a back up of the file being edited and restoring it once you've built the module.)

---

### Post by bandgeek on 2009-04-25
Thanks for the help. I'll try what you suggested. One quick question what file am I editing exactly? Also how do I back it up?

Sorry only been using Ubuntu for about 2 months. Total noob.

---

### Post by Stochastic on 2009-04-26
> **pljones said:**
> That'll be your ATI card, that will...

There's maybe a workaround, if you don't mind getting your hands dirty, here:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?msg=39;att=0;bug=420842](http://bugs.debian.org/cgi-bin/bugreport.cgi?msg=39;att=0;bug=420842)
(I would suggest taking a back up of the file being edited and restoring it once you've built the module.)

What????  That bug you're referencing refers specifically to a fglrx of <=8.37
It specifically says > Fixed in version fglrx-driver/8.39.4-1 Jaunty is running an fglrx version 8.600

FURTHERMORE, at no point did the OP mention that they were using the proprietary fglrx driver rather than the opensource driver (which is default and recommended).  Infact since they weren't able to even boot into a working system, it stands to reason that no fglrx is even on their system.  Please don't give beginners instructions to muck about with kernel headers - it's inappropriate behavior on the forums.



NDenny, it sounds like you have a bad install (because the audio section of apps aren't loaded right), you may want to try re-installing.
Also, could you write down the info on the screen when the computer freezes, then report the issue here for the Ubuntu RT kernel team to read: [https://bugs.launchpad.net/ubuntu/+source/linux-rt](https://bugs.launchpad.net/ubuntu/+source/linux-rt)

---

### Post by bandgeek on 2009-04-26
I just restarted several times each time the Real Time Kernel has stopped somewhere differant. Stuck with Floppy Drive light on. Getting to the login screen typing in my password then freezing. Each time it's something differant. I'm going to try reinstalling everything again.

---

### Post by bandgeek on 2009-04-26
Just reinstalled everything again still didn't work](*,)So now I'm going to do the extreme measure. Burn an Ubuntu Studio disk, format my regular Jaunty release and install. Starting from scratch.:(

---

### Post by bandgeek on 2009-04-27
The Ubuntu Studio disk didn't burn right. So I burned a regular Jaunty disk and reinstalled Ubuntu. In my new Ubuntu installation I installed the real time kernel. Was able to boot after three tries. Then it happened, update manager updated Firefox and killed it. Literally, I couldn't even reinstall. So off to install Ubuntu again. After reinstalling Ubuntu again I installed and booted the real time kernel. The same sporadic behavior sometimes letting me boot sometimes not. So to LinuxCD.org I go to buy Fedora and Sabayon disks. Maybe even JAD and Musix:)

Don't get me wrong I like Ubuntu and the people and will still be using the regular version. Just going to wait for Koala Studio and see if that works for me:)

---

### Post by Stochastic on 2009-04-27
NDenny, please help the RT team understand your problem better (maybe even solve it with you) and report the behaviour of the RT kernel at [https://bugs.launchpad.net/ubuntu/+source/linux-rt](https://bugs.launchpad.net/ubuntu/+source/linux-rt)

---

### Post by bandgeek on 2009-04-29
Just filed a bug report.

---

### Post by vivichrist on 2009-05-29
I had to compile my own kernel and use the open source radeon driver to get rt happening. I compiled 2.6.29-4 with ingo's rt patch etc.[https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/290498]("https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/290498")

---

### Post by Areia on 2009-06-01
> **vivichrist said:**
> I had to compile my own kernel and use the open source radeon driver to get rt happening. I compiled 2.6.29-4 with ingo's rt patch etc.[https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/290498]("https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/290498")

Can you send me a link to compile a kernel myself? I`d never find a simple one.
Thanks!

---

### Post by Dave_Connor on 2009-06-02
Kernel Compiling takes a bit of knowledge knowing what hardware runs on your box and then what modules would be the best to work on that hardware. For Kernel compiling there is several guides on Google that will help with explaining how compiling is done under neath.

---

### Post by vivichrist on 2009-06-08
I followed this:
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild") but used different kernel from the link

has links to ready compiled kernels:[https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/290498]("https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/290498")

---

