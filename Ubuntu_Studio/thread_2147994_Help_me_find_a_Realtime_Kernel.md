---
title: "Help me find a Realtime Kernel?"
date: 2013-05-23
forum: Ubuntu Studio
---

### Post by forkenbrock on 2013-05-23
I have a current setup from the standard 32-bit 12.04 LTS Ubuntu.  I want to install a patched Realtime kernel, but nothing I've tried has worked.

I followed the instructions at the link below and was able to successfully install a patched 3.4 realtime kernel.  However, it was not compatible with my Remastersys installation and I ABSOLUTELY have to be able to create a live disc for this project.  Maybe the problem with this kernel and Remastersys was that it was a generic kernel, rather than an Ubuntu kernel?  I tried Relinux, but it led me down a rabbit hole of problems with Python.  

[http://askubuntu.com/questions/72964/how-can-i-install-a-realtime-kernel](http://askubuntu.com/questions/72964/how-can-i-install-a-realtime-kernel)

Next, I tried apt-get in the terminal and downloaded the Ubuntu 3.2.0 kernel, but the only RT patch available for 3.2 is 3.2.45.  Maybe those two are not compatible, because the patching failed.  Finally I went looking for a packaged Ubuntu realtime kernel, but the Bogani PPA will not allow me to access the launchpad site and the Ubuntu Studio page no longer exists.

Again, what I need is an Ubuntu realtime kernel that will also work with my Remastersys installation.  I prefer to find a packaged version, to avoid potential headaches, but I can probably patch it myself if necessary.

---

### Post by jejeman on 2013-05-23
What about the lowlatency kernel which comes with Ubuntu Studio? Do you realy need RT?

---

### Post by forkenbrock on 2013-05-23
Hi Jejeman, I might not "need" RT.  I just wanted to do it so my audio friends and I could hear and experiment with it and we want to go all the way.  I was under the impression that it's still possible to do RT in Ubuntu.

One more thing.  It's taken me a long time to configure everything the way I have it now.  I don't want to do a fresh install and have to redo everything.  I'd like to just replace the kernel with an RT kernel.

---

### Post by tgalati4 on 2013-05-23
If you want a shareable audio/media distro then I would consider [http://www.dynebolic.org/](http://www.dynebolic.org/).

---

### Post by zequence on 2013-05-23
linux-lowlatency is good enough for most people. It's based on the Ubuntu kernel, and only differs slightly from it. I would try that first, and then see if you need anythint better. It is the default kernel for Ubuntu Studio. But to make use of it, with jack, you need to have realtime privilege set up. Also fixed on Ubuntu Studio.

-rt kernels are more experiemental. Don't get one, if you don't need one.

---

### Post by forkenbrock on 2013-05-24
I'm not interested in another distro right now, as I said, I don't want  to have to go back and rebuild everything else in the OS.  I probably  will try low-latency at some point, but right now trying to do RT in  Ubuntu.  I don't care that it's experimental, because what we're doing  is experimenting.  If anyone out there knows how to do RT in Ubuntu your  help is appreciated.

---

### Post by CrocoDuck on 2013-05-25
Hi. You can find real time kernels for ubuntu in KXStudio repos: [http://kxstudio.sourceforge.net/](http://kxstudio.sourceforge.net/) , [https://launchpad.net/~kxstudio-team/+archive/kernel](https://launchpad.net/~kxstudio-team/+archive/kernel) . Also you can find it in Abogani's repo: [https://launchpad.net/~abogani/+ppa-packages](https://launchpad.net/~abogani/+ppa-packages) . I suggest you to add one of this repo and then install the kernel with apt.

---

### Post by forkenbrock on 2013-05-25
Great.  Thank you CrocoDuck.  That's exactly what I needed.

---

### Post by forkenbrock on 2013-05-26
It doesn't look like the Kernel sources pointed out by CuocoDuck will work.  The Bogani PPA has been taken down and KX Studio doesn't have any RT kernel downloads except for 2.6.

---

### Post by CrocoDuck on 2013-05-27
Oh... I didn't noticed. Until now I've been able to run an up to date realtime kernel only with Archbang linux (when I tryed it on ubuntu, using the one on KXStudio repos something like a year or two ago, it failed to boot). You said you don't want to install a new system, however I link this to you, you may find it useful: [http://www.linuxmusicians.com/viewtopic.php?f=19&t=10837](http://www.linuxmusicians.com/viewtopic.php?f=19&t=10837) . If you don't find an up to date package probably you will have to build your own realtime kernel, adding the realtime patch in the source and then compiling it after configuration. I never done it, so I can't help you or link to you some cool page, but you should be able to find a lot of guides on internet. If you go through this way take your time, is better to do it the best you can. However, an older version of the kernel could still work even on newer ubuntu releases... If I'm not wrong KXStudio has chosen the older kernel for stability reasons (I may be wrong).

---

### Post by CrocoDuck on 2013-05-27
Uhm... I remember I installed the rt-kernel, without success, on Ubuntu Studio 12.04. On KXStudio pages I read this:

> 

[http://kxstudio.sourceforge.net/Documentation:Ubuntu:Upgrade](http://kxstudio.sourceforge.net/Documentation:Ubuntu:Upgrade)**Step 5 - Install a Kernel (Optional)**

      This step is optional, and mostly useful for audio production only.
    Installing a kernel in KXStudio couldn't be easier - just install one of these packages: 
 
[LIST]
[*]kxstudio-kernel-generic 
[*]kxstudio-kernel-generic-pae *(32bit only)* 
[*]kxstudio-kernel-lowlatency 
[*]kxstudio-kernel-lowlatency-pae *(32bit only)* 
[*]kxstudio-kernel-realtime *(10.04 or 12.04)* 
[*]kxstudio-kernel-realtime-pae *(10.04 or 12.04, 32bit only)* 
[/LIST]
      The realtime kernels are only available for 10.04 and 12.04.
    Ubuntu 10.04 uses a 2.6.33 RT kernel and 12.04 uses a 3.2.0 one. 




Try to add the Kernel repos and then search for the package kxstudio-kernel-realtime with apt (or anything you like). If you find one marked for ubuntu 12.04 it should be a 3.2.0 . [http://kxstudio.sourceforge.net/KXStudio:Repositories](http://kxstudio.sourceforge.net/KXStudio:Repositories) . I don't remember very good how it works, maybe the installation of the version 3.2.0 is automatical if you have Ubuntu 12.04... Another link you may find useful: [http://wiki.linuxaudio.org/wiki/system_configuration](http://wiki.linuxaudio.org/wiki/system_configuration) .

---

