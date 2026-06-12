---
title: "What's the deal with..."
date: 2007-06-04
forum: The Cafe
---

### Post by laxmanb on 2007-06-04
...not including proprietary video drivers (ATi/NVidia) with ubuntu?? Ubuntu won't start/install on my laptop with a Mobility Radeon GPU...

And it's a well known fact that the GPL drivers are inferior... The FOSS philosophy is good, but does it need to extend to things like drivers as well??

---

### Post by aysiu on 2007-06-04
Uh, read this:
[http://www.markshuttleworth.com/archives/84](http://www.markshuttleworth.com/archives/84)

---

### Post by jiminycricket on 2007-06-04
Yes, it does.  [GNU ]("http://www.gnu.org/philosophy/shouldbefree.html")started after Richard Stallman couldn't get a printer driver to work because of restrictive licensing!

The GPL drivers are actually not inferior, as you will see with the many crashes, bugs, suspend, memory, **security**, portability, glitches, dropping support, and other problems that nVidia and especially ATI (or wireless drivers) inflict on GNU/Linux.  Both "ethics" and actual code quality play a role in the high quality of free drivers  (btw-- the video drivers tend to be MIT licensed, since that's what the video server X11 is licensed).

In some cases, the manufacturers have deliberately obfuscated the code, as in the case of nVidia and the "free" 2d nv driver.  

Reverse engineering efforts are underway in both cases, so that it will benefit you now and in the future.  Eg., my Radeon 7200 supports AIGLX because the drivers were free. ATI had no reason to do that, but since the source code was available, people added that support in.  Unfortunately, even fglrx today (the driver that supports your specific ATI card) doesn't support AIGLX, and people can't fix them.

---

### Post by laxmanb on 2007-06-04
> **jiminycricket said:**
> Yes, it does.  GNU started after Richard Stallman couldn't get a printer driver to work!

The GPL drivers are actually not inferior, as you will see with the many crashes, bugs, suspend, memory, **security**, portability, glitches, and other problems that nVidia and especially ATI inflict on GNU/Linux.

But they don't actually work with my notebook, so what's the use...

---

### Post by jiminycricket on 2007-06-04
> **laxmanb said:**
> But they don't actually work with my notebook, so what's the use...

fglrx doesn't work well itself.  That's why Dell doesn't sell an ATI Linux machines, only Intel (open drivers) and nVidia.

---

### Post by laxmanb on 2007-06-04
But hey, it works... and why are the policies of an entire community decided by a single person... If Richard Stallman wants drivers to be FOSS, then why does ubuntu have to have FOSS drivers only??

---

### Post by aysiu on 2007-06-04
Ubuntu is dedicated to free software. It's not quite as religious about it as Stallman is, but Mark Shuttleworth wants to promote free software. If you don't dig that philosophy, install the drivers yourself (not that difficult) or don't use Ubuntu. There are plenty of Linux distros out there that include and embrace proprietary software: PCLinuxOS, Xandros, Linspire, Mepis, Linux Mint, Blag...

If you want help, create a support thread, and you'll get help.

---

### Post by pragmatine on 2007-06-04
One of the problems is that the licensing of the closed source drivers (Nvidia and ATI) prevent them from being distributed on the install cd, and they must be downloaded  separately. So Ubuntu cannot legally do what you ask anyway.

---

### Post by aysiu on 2007-06-04
> **pragmatine said:**
> One of the problems is that the licensing of the closed source drivers (Nvidia and ATI) prevent them from being distributed on the install cd, and they must be downloaded  separately. So Ubuntu cannot legally do what you ask anyway.
That's not what I read.

This is from [Mepis' page on the Nvidia driver license](http://www.mepis.org/node/10353) (which includes the actual license): > 2.1.2  Linux Exception.  Notwithstanding the foregoing terms of
Section 2.1.1, SOFTWARE designed exclusively for use on the Linux
operating system may be copied and redistributed, provided that
the binary files thereof are not modified in any way (except for
unzipping of compressed files). Here's the actual license page:
[http://www.nvidia.com/object/nv_swlicense.html](http://www.nvidia.com/object/nv_swlicense.html)

---

### Post by jiminycricket on 2007-06-04
> **laxmanb said:**
> But hey, it works... and why are the policies of an entire community decided by a single person... If Richard Stallman wants drivers to be FOSS, then why does ubuntu have to have FOSS drivers only??

The 'policies' are decided by the copyright holders who placed their code under the GPL (General Public _License_); otherwise, it's copyright infringement, so you might want to check out Kororaa's history...

Linux also had to suffer for a few years as GTK was developed in response to a non-free QT, but in the end there are now two completely free toolkits for Linux.

---

### Post by laxmanb on 2007-06-04
No I like ubuntu... but the driver thing is just an annoyance... you have to download the Alternate Install CD, install ubuntu, then it boots up in text mode, then you install Ati drivers, then it works...

another problem is that bandwidth charges are high in India, so I'll have spent $30 downloading ubuntu... which is also a lot by Indian standards...

---

### Post by jiminycricket on 2007-06-04
I understand what you're saying...The ball is really in ATI's court though.  People are trying to reverse engineer the driver so it can be included, but their hardware is apparently not very well thought out and it'll probably be a few years before it will fully work.  Same thing goes on with nVidia and Nouveau, although they're farther along I believe.

---

