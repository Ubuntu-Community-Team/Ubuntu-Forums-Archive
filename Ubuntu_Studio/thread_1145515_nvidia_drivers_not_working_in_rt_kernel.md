---
title: "nvidia drivers not working in rt kernel"
date: 2009-05-01
forum: Ubuntu Studio
---

### Post by ENatanael on 2009-05-01
There has been a thread a bit like this earlier, but not exactly.

When running the real-time kernel in Ubuntu 8.10 it worked fine, but after upgrading to 9.04 it won't load the nvidia drivers anymore. It works in the generic kernel. 

Can I fix it?
Should I file a bug report? Where?
Is it worth it waiting for a fix or should I try another kernel version? If so, how?

Graphic card: Nvidia GeForce FX 5500

Attaching the logs from starting the X-server with the real-time kernel.

EDIT: Real-time kernel version: 2.6.28.3.1

---

### Post by hardyn on 2009-05-01
Try the drivers from the nvidia website, see if the issue is in the ubuntu package, or the driver its self.


> **ENatanael said:**
> There has been a thread a bit like this earlier, but not exactly.

When running the real-time kernel in Ubuntu 8.10 it worked fine, but after upgrading to 9.04 it won't load the nvidia drivers anymore. It works in the generic kernel. 

Can I fix it?
Should I file a bug report? Where?
Is it worth it waiting for a fix or should I try another kernel version? If so, how?

Graphic card: Nvidia GeForce FX 5500

Attaching the logs from starting the X-server with the real-time kernel.

EDIT: Real-time kernel version: 2.6.28.3.1

---

### Post by GiveLove on 2009-05-01
I have this same problem. I'm using a Nvidia 7600GS AGP graphic card. And upon booting the RT kernel I get some error about not being able to load the video card driver. Is this really something specific to Nvidia graphic card users?

---

### Post by ENatanael on 2009-05-02
Ok, I've downloaded the driver from the nvidia website, but it has to be run when X isn't running. This is from the readme:

"Before you begin the installation, exit the X server and terminate all OpenGL applications (note that it is possible that some OpenGL applications persist even after the X server has stopped). You should also set the default run level on your system such that it will boot to a VGA console, and not directly to X. Doing so will make it easier to recover if there is a problem during the installation process."

But as I understand it Ubuntu doesn't use runlevels? Or at least fewer than what is common? How do I boot into a console and preventing X from running on reboot while being able to later change this back so that I can start normally after having installed the driver?

---

### Post by thorgal on 2009-05-02
to compile the nvidia driver from the nvidia website, you need a few things:

- make sure you have installed a package called linux-headers-at-whatever-version-your-kernel-is.
- debian based systems do use runlevels but only use 2. To disable X, switch a virtual terminal, e.g. VT2 :
```

Ctrl+Alt+F2

```

if that does not trigger what it is supposed to, then from a terminal in X:
```

sudo chvt 2 

```

log in in the VT, then
```

sudo /etc/init.d/gdm stop

```

if you are using KDE and kdm, use kdm instead of gdm.

Now, go to the directory where you downloaded the package from nvidia.com, make it executable:
```

chmod +x NVIDIA-blabla.run

```

then execute it:
```

sudo ./NVIDIA-blabla.run

```

- accept the terms of the licence
- don't accept the offer to check whether a precompiled version exists on their FTP server for your particular kernel (chances of such are ultra slim :lol: )
- go ahead with building of the kernel module

That will install the nvidia.ko kernel module + X libraries.
To restart X:
```

sudo /etc/init.d/gdm start

```


The following does not require you leave X at all:

If you only want the kernel module because the nvidia X libs are already installed (say you changed kernel in the mean time but want to stick to the version of the nvidia driver already installed):
```

sudo ./NVIDIA-blabla.run -K

```

if you only want the kernel module for another kernel that you have installed but not booted into (and you have the kernel headers for it as well):
```

sudo ./NVIDIA-blabla.run -K -k the-kernel-version

```

replace the-kernel-version by the real kernel version (a quick check in /lib/modules or /boot/grub/menu.lst or 'dpkg -l linux-image* | grep ii' will show you what kernels you have installed).


For my debian based laptop, which holds an old GeForce FX 5200 GPU, I never relied on the debian packaged nvidia driver, always installed the driver from nvidia.com. It installed flawlessly against kernel 2.6.29.2-rt10 (which I compiled myself) and suspends / resumes flawlessly as well :)

---

### Post by ENatanael on 2009-05-02
Thanks for the quick answer!
I tried building the kernel module booted into my generic kernel (should I have done it on the rt kernel?) and everything went fine until I started the X-server again. nvidia wouldn't load.
I then tried to build the kernel module booted into my rt kernel, but then it wouldn't even build. 

Running the command
```
sudo ./NVIDIA-Linux-x86-173.14.18-pkg1.run -K -k 2.6.28-3-rt
```
gave the error message 
"ERROR: Unable to build the NVIDIA kernel module."
Attaching log from starting generic kernel (failsafe...) and trying to run "sudo ./NVIDIA-Linux-x86-173.14.18-pkg1.run -K -k 2.6.28-3-rt" (nvidia-installer.log).

---

### Post by chaser.nl on 2009-05-02
maybe my reply in this other thread can help ;)

[http://ubuntuforums.org/showthread.php?p=7197037#post7197037](http://ubuntuforums.org/showthread.php?p=7197037#post7197037)

---

### Post by ENatanael on 2009-05-02
By first removing the nvidia packages using 
```
sudo apt-get remove --purge nvidia*
```
and then reinstalling the driver on my generic kernel I managed to get it to work there. But it's still the same problem with the rt kernel. 

I run the command
```
sudo ./NVIDIA.run -K -k 2.6.28-3-rt
```
and the installation starts and goes to 100%, but then displays the error message:
"ERROR: Unable to build the NVIDIA kernel module."
Attaching log from this installation attempt.

---

### Post by thorgal on 2009-05-02
I briefly looked at your compilation log. It looks like this version of the nvidia driver and the RT patch are incompatible. At this stage, the only option that I would recommend is to try and get a 2.6.29.2 kernel, patched for RT (rt-10) and try again. However, I am afraid that such would require you compiled your own kernel. That's maybe not what you want.

I can be wrong of course, but my experience is that 2.6.29 is a much better serie than 2.6.28 in many aspects.

---

### Post by ENatanael on 2009-05-02
If compiling my own kernel is the only option, then I will compile my own kernel. :)
Do you have any suggestion on a good guide for it? I assume this is quite a risky thing for a not so advanced user.

---

### Post by thorgal on 2009-05-02
compiling your own kernel is not risky so long as you keep a safe bootable kernel as well (like a packaged generic kernel) should any kernel you compile fail to boot.

you can get inspired by this debian RT kernel howto:
[http://forums.debian.net/viewtopic.php?t=17035](http://forums.debian.net/viewtopic.php?t=17035)

just replace the kernel version mentioned in there by what you are after. I run 2.6.29.2-rt10 and am really satisfied.

Make sure you have installed a package called "kernel-package" and another one called "build-essential" before trying to compile a kernel.
The 1st package contains the very useful make-kpkg utility.

As the howto mentions, you need to create two packages: linux-image and linux-headers. Make sure you target both. Compiling the nvidia driver will require the linux-headers as well.

The tricky part is to configure the kernel before invoking make-kpkg. If you want to be safe, just use whatever config file you have in /boot and copy it to the kernel source directory into a file called .config. Then say make oldconfig. If you patched the kernel source with the RT patch, make oldconfig will prompt you with a few options to choose. Make sure you select complete_preemption. That's the mandatory RT option you don't want to miss.

---

### Post by ENatanael on 2009-05-03
Thank you! 
I compiled the kernel (2.6.29.2-rt11) and installed the kernel module from my generic kernel. Now everything works fine! Thank you again!

---

### Post by thorgal on 2009-05-04
hi there, sounds great :)
just tell how you like the new kernel (performance, etc) and report to UbuntuStudio. The choice of 2.6.28 in jaunty is somewhat strange to me ...

---

### Post by Stochastic on 2009-05-04
> **thorgal said:**
> The choice of 2.6.28 in jaunty is somewhat strange to me ...

The kernel version for a release is decided by the overall Ubuntu developers, then Ubuntu Studio devs are handed the task of making it RT.  IIRC 2.6.29 was released too late into Jaunty's development cycle (as the reason why 2.6.28 was chosen).

It looks like Karmic will get 2.6.30 (from what I hear).

---

### Post by thorgal on 2009-05-04
I see. Since the RT kernel is a critical component of Ubuntu Studio, I would recommend a more loose policy as to the version choice, same goes with jack. But again, I am no Ubtuntu maintainer or developer, it's up to them ...

---

### Post by blakew on 2009-06-06
I'm just compiling the 2.6.29-4-rt16 kernel myself... you need a few other packages, if you dont already have them: libncurses5-dev, and unp. Another tip: the font used in the debian forum for code shows the number one (1) as looking remarkably identical to the letter l. In both cases in the commands it's actually the number one, just to save other people the trouble there.

Edit: I get the feeling this has something to do with the issue:

> Nvidia graphics driver:
You might want to disable Paravirtualization in make menuconfig. The Nvidia driver does not build against kernels with this enabled.

I used the config that ships with ubuntu studio 9.04, then when i got into menuconfig, paravirtualisation was indeed enabled. Made sure to disable it.

Edit 2: Hang on, it seems to work!

---

### Post by flemmingbjerke on 2010-01-05
I had installed the generic kernel that worked with an nvidia-driver and linux-image-2.6.31-9-rt that did not work with nvidia.

I got the rt-kernel to work in the following way:

1. Download latest driver from nvidia
[http://www.nvidia.com/object/unix.html]("http://www.nvidia.com/object/unix.html")

2. Reboot to the rt-kernel, where X does not work.
Cd to the downloaded nvidia-file and run as root on the file:

> sh NVIDIA-Linux-x86-190.53-pkg1.run -x

This produces a folder that you cd into:

> cd NVIDIA-Linux-x86-190.53-pkg1

then run:

> ./nvidia-installer

If the installation went without problems:

3. Reboot on the rt-kernel
Now the rt-kernel should work with X.

4. Remove the generic kernel with apt-get because it probably does not work anymore. Eventually:
> update-grub

And your box run realtime - only.:guitar:

The PC:
> dual kernel intel 2*2,5 GHz 32 bit
nVidia Corporation GT200 [GeForce GT 220]

---

