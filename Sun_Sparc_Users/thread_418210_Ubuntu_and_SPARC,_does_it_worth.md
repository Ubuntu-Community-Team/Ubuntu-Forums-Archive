---
title: "Ubuntu and SPARC, does it worth ?"
date: 2007-04-22
forum: Sun Sparc Users
---

### Post by chatuser on 2007-04-22
I have tested Solaris x86 and ... it could be an excellent operating system for servers, but I'm an administrator of Debian and Ubuntu systems and I prefer to use them instead Solaris.

I'm considering to buy a Blade 150 or an Ultra 60 on eBay and install Ubuntu, but ... does it worth ?

- How fast is Ubuntu compared to Solaris on the same machine ?
I have tested Debian on my sgi Indy (MIPS R4400) and it's really slow, Debian is not optimized at all for that hardware. Is there the same problem with Ubuntu on SPARC ?

- How usable is it ?
I wonder if you can use it as daily computer or it's only for enthusiast use.

If you tell me your experiences with Ubuntu on your SPARC computers I'll be pleased, it's the best reference I can have.

Thanks in advance.

---

### Post by netztier on 2007-04-23
> **chatuser said:**
> If you tell me your experiences with Ubuntu on your SPARC computers I'll be pleased, it's the best reference I can have.

Ubuntu is not a bad choice for SPARC machines, but there are issues when running X or Gnome: There's no hardware-acceleration for X, neither with Creator or Elite cards, nor for the ATIs as they are used in U5, U10 and some of the smaller Blades; with the ATI chips, we had to use a file from Debian's X.org packages to make X work.

The XVR video cards with the Permerida Chips have even less support; xorg's glint driver doesn't seem to like any of them. There were a few threads in the forums about these, an no one seems to have had any luck.

So I would not recommend using Ultras as desktop machines. The Ubuntu releases for SPARC are offered as "server versions" anyway. Nothing stops you from installing the desktop-packages, of course, but you'll have to  expect the occasional tripwire.

Performance: Can't help you there with figures - but remember that these old SPARCs are slow - a 360Mhz UltraSPARC II is not really faster than a P-II 400 Mhz, so expect no miracles. It is under load that these machines shine - like old diesel tractors pulling some heave trailer uphill. Not fast, but steady, and always ready to take one more task, one more service, one more bit of load.  :-)

best regards

Marc

---

### Post by chatuser on 2007-04-23
Thank you very much for you answer, I like comments about Linux on non-PC machines.

I have an sgi Indy (Irix and Debian) and a sgi Octane2, and I'm waiting for an IBM 7044 44p-170, I'll install Debian on the IBM among AIX.

I was thinking about to buy a Sun machine to use it under Solaris and Ubuntu, but now I think it's better to wait because the graphics hardware is not entirely supported and I have enough with my machines and their "alternate" operating systems.

If anyone has more comments about Linux and SPARC they will be appreciated.

Thanks in advance.

---

### Post by pakman on 2007-04-24
Hi chatuser,

I run Ubuntu 6.06 along with Solaris 9 on a dual-boot SunBlade 100. Having Ubuntu is good because of the huge range of applications that it gives me access to (for example, I haven't found equivalents of Audacity, Muse or Rosegarden that I can use on Solaris, not even on blastwave.org) and better support for some devices (e.g. flash memory cards above 128MB), but I have to say that some things don't work very well. The internal sound card is not supported fully (I can play WAV files, but that is about it: ALSA or Artsd doesn't work). Maybe an external USB sound card would be OK. I fitted an internal USB 2.0 PCI card (a D-link one if I remember correctly): this is definitely worth doing if you are going to connect any USB external storage beause the 4 USB ports that are already there are only USB 1.1

A while back I replaced the CD-ROM drive with a LGE tri-mode CD/DVD burner. This works fine with Solaris, both with cdrecord (with the Solaris volume manager vold turned off) and Sun's own cdrw application, but Ubuntu has problems with it, probably because you have to boot Ubuntu with the ide=nodma kernel option (see posts elsewhere on this forum). I do all my CD/DVD burning in Solaris. The framebuffer also has problems (persistent red dots and other graphics corruption). There is another kernel option to fix this (video=... I forget exactly what but I can look it up tomorrow if you like), but this means that the consoles accessible by Alt-F1 to Alt-F4 are a lot less usable.

I have also found architecture problems: one attempt at doing a dist-upgrade all to go from 6.06 to 6.10 trashed my system so completely that I had to do a complete re-install. I then found that there were SunBlade-specific problems with the kernel that was included in that particular version of 6.10, but the news hadn't made it into the Ubuntu forums (remember that low-end workstations are not the main target of Ubuntu/Sparc!). In future, I'll always check that I can boot from the installation CD of any version that I am thinking of upgrading to.

The Sunblades are slow machines, and subjectively I find that Ubuntu is even slower than Solaris 9 (my usual benchmark is using timidity to convert MIDI files to WAV, which is a CPU-limited operation). I would suggest using a lightweight desktop like xfce rather than gnome or kde (after installing Ubuntu-server, install xubuntu-desktop). When I referred to Muse and Rosegarden, I use them as MIDI file and notation editors only - forget about any real-time MIDI sequencing. I don't know if the speed would be improved by building a Linux distro with the Sun studio compilers under Solaris.

As to whether it is worth it: well, I tried because  I had the machine already and was interested to see how far I could push it (a bit like someone I used to know who kept a DEC MicroVAX going to annoy salesmen when they tried to persuade him to buy the latest and greatest hardware). It is definitely useful to have both Linux and Solaris available. (Solaris is also free for personal use, of course). It is usable, but don't expect too much. Also, the base configuration of the SunBlades has very little RAM (128Mb for the 100, maybe 256 for the 150?). You definitely need more if you decide to go down this route.

Regards,
P.

---

### Post by erm67 on 2007-04-24
I was tired of Solaris 9 + Blastwave on my Ultra2 2x296mhz 36Gbhd 1280mb ram and solaris 10 is simply too slow for that machine so I installed xUbuntu FeistyFawn + a few other apps from main.
I use it in my second house where I spend only a few weeks per year so the speed does't bother me much, and it is not so slow anyway. openoffice starts faster than on solaris9 and is usable the same for most apps.
I was able to configure ALSA (the module is not loaded automatically, just added in /etc/modules), and I have read that is possible to activate the dri accelleration at least for the creator3d.
Solaris is more stable, linux is going to crash ofter probably but offers more speed and much more software readily available.

I find curious that the ubuntu sparc distribution doesn't support sun keyboards .......

---

### Post by netztier on 2007-04-24
> **erm67 said:**
>  I find curious that the ubuntu sparc distribution doesn't support sun keyboards .......

In GMOME (as delivered by the meta-package **ubuntu-desktop**), see **System -> Preferences -> Keyboard Shortcuts**. There's quite an interesting number of predefined functions you can map to the special keys, including Volume Up/Down, Mute, PowerOff/Logoff. This works even if you configure pc104/105 in console-data and xorg.conf.

best regards

Marc

---

### Post by chatuser on 2007-04-25
Thank you very much for your posts, they are very interesting.

I had a look to Debian documentation on several platforms and there is always the same problem: lack of hardware support. Linux is centered on x86 architecture and the rest of architectures have several problems (except Mac, I believe).

There are several problems about graphic cards on sparc, hppa (HP PA-RISC), powerpc (IBM RS/6000 and pSeries), ... the explanation is always the same: manufacturers don't provide complete documentation about their hardware.

Some graphic cards have limited support through frame buffer, even some people is trying to install old graphic cards (as S3 36x) in HP's or pSeries to make Xorg work. Has anyone tried this with a Sun ? I'll try this with my IBM 44p 170 :) , it has PCI slots.

As example, my sgi Indy (MIPS R4400 150 MHz processor) graphic card is supported but without acceleration, so the graphical environment is very, very slow.

I'm thinking to buy a Sun Ultra 60 Creator 3D - 2x 450 UltraSparcII, 512MB on eBay to play with Solaris and Ubuntu, if I finally buy it I'll report my experience.

Regards.

---

### Post by pakman on 2007-04-27
> **erm67 said:**
> 
Solaris is more stable, linux is going to crash ofter probably but offers more speed and much more software readily available.


This is interesting: as far as speed is concerned I found the exact opposite. The processor architecture is not so different (both UltraSPARC-II). Since writing my previous post, I upgraded to the latest Blastwave stable release on Solaris which includes xfce. This desktop is actually quite responsive with Solaris: not the case with Ubuntu 6.06 at all. I wonder if Feisty Fawn is better optimised for UltraSPARC than 6.06, but I probably can't upgrade because of the 6.10 problems. I'll have to go for a complete re-install, so it isn't going to happen just yet :) 

Cheers,
P.

---

### Post by erm67 on 2007-04-27
> **pakman said:**
> This is interesting: as far as speed is concerned I found the exact opposite. 
P.
Maybe is just enthusiasm for the new amusement on my side, I formatted the drive with solaris so I cannot test again ...
But well I am still conviced that OpenOffice is faster ...
Blastwaves apps are compiled with sun forte compiler that usually generates faster executable than gcc.
I cannot explain the speed, file says executables are compiled for Sparc V1 i.e. not optimized for ultrasparc, some libraries however are, the kernel too is compiled for ultrasparc.
Since I installed the smp kernel booting is really fast. 
The only annoyance is that whenever I run glxinfo or other apps that use dri accelleration the X server crashes.
A really strange thing happens with my dvd drive, if I put a cd in the drive first after the boot the I can no longer read dvd. I f I put a dvd in it after the boot than it can read both dvd and cd.... strange. The esp driver beheves strangely always in connection with the dvd reader /dev/scd0 if I put a damage dvd in it and try to read after a few failures all devices on the controller are put offline inclusive /dev/sda where the / is .......
Never had problems with solaris reading dvds (well except for iso9660/UDF ibrid that can't be read) or cds.

A worrying thing is this:
[https://wiki.ubuntu.com/sparc64-stabilization](https://wiki.ubuntu.com/sparc64-stabilization)
it looks like from this blue print that there is a single guy working on ubuntu-sparc 
> 
Make FabioMassimoDiNitto redundant (since he is basically the only sparc guy in the team and this is NOT ideal)

and that there are many problems:
> The community momentum has unveiled a lot of new bugs and problems in different parts of the distro

---

### Post by chatuser on 2007-04-28
Hi erm67.

Reading your post I wonder how committed is Sun about Linux.

I read on Sun's website lots of information about Linux, but the reality is that the hardware is not entirely supported, the performance is not optimized and there is not enough people working for Linux in Sun.

So ... is Linux another marketing tool for Sun ? What do you all think about it ?

Regards.

---

### Post by erm67 on 2007-04-28
sun sell solaris for sparc boxes with more than 1 cpu AFAIK (well someone pays for it I suppose)
Sun sells also opteron servers
Solaris doesn't work well on x86
sun sponsors linux, but not for sparc, for its opteron and cobalt servers

Sun has all the interest if the linux kernel on sparc does not work very well I think.

---

### Post by netztier on 2007-04-29
> **erm67 said:**
> 
Solaris doesn't work well on x86


Hm - please clarify if you mean "general i386" (including AMD and Intel) or if your statement points out a difference between amd64 and x86.

At work, we're switching to AMD based machines (from SPARCs) running Solaris, because the app we intend to use needs the boost in (single thread) performance. So I'm somewhat surprised to see a statement that Solaris didn't work well on x86.

best regard

Marc

---

### Post by erm67 on 2007-04-29
> **netztier said:**
>  So I'm somewhat surprised to see a statement that Solaris didn't work well on x86.

It was just a general rant rant about the problems we have using old sun hardware with linux, solaris worked beautifully on it.

but historically Solaris x86 was never as good as Solaris sparc.
I first used a copy of Solaris 7 x86 "borrowed" at work (you had to pay for it at the time, we had received it to test it), and well it was not uncommon for the intels to crash (let's not talk about the drivers), later I started using some Solaris 8 x86 servers as test servers at work and it was indeed better but using it with "non  HCL" or cheapo hw was certainly more problematic than linux if possible at all. Eventually we have now a 2xXEON Solaris 9 x86production server running some web-applications, and it works flawlessy but to find harware that works with it was not easy, the turning point I think was when we switched to scsi disks. Later I always proposed sparc server to be used with solaris.
I haven't tried Solaris 10 yet and I am no longer doing network and server administration so maybe things are better now, and probably it works perfectly with sun servers.
As for using it at home last time I checked there was no flash-player, Acrobat >4, opengl, dri, drivers for tv card ......
I worked 10 years with solaris and I love it but I prefer to have ubuntu on my desktop at home :)

---

### Post by ykanello on 2007-05-07
I am running 2 sparc servers with ubuntu.a T1, v120.
the T1 i use it as a LAMP server, and the second one as torrentflux server.
For the T1 i cannot tell you much since is not heavily used.
The v120 though is a different story. 
Initially i had it with solaris9 running a moded TF. 
More than 16mb/s traffic  and 40 active torrents and the system would go to pretty much unresponsive stage.
After a nasty disk crash, I replaced solaris with ubuntu 6.10. 

Except the small issue with the booting from second disk (the /boot partition in sparc cannot be mirrored or i dont know how to -- so I ahve to boot with ok boot disk2 in case of failure)

Actually the system behaves MUCH better now. It can widthstand much more load (active torrents, and more bandwidth)

I have actually started replacing all the SPARC hardware with ubuntu 6.10, since I have found big dissapointments in solaris10.

---

### Post by chatuser on 2007-05-07
I can't believe my eyes: "Actually the system behaves MUCH better now"

Usually propietary OSs are completely adjusted to work fine on their target machines.

I finally received my IBM 44p 170 and installed Linux, it works fine but perhaps just a little bit slower than AIX. No support for IBM graphic cards, I have tested several PCI graphic cards unsuccessfully.

I also have read on Debian mailing list about Debian on PA-RISC machines, let's have a look to Linux on some non-Intel hardware:

SGI MIPS: very slow on Indy (I have one), unaccelerated video. Works on O2 without X
HP PA-RISC: at least 50% slower than HP-UX (Debian mailing list), no support for modern graphic cards
PowerPC: good performance on pSeries (I have one), no support for graphic cards. I think Macs also have good performance and X support.
SPARC: I understand Linux works fine on modern hardware, limited graphic cards support.

So, except for Intel and PowerPC  Macs, we could think Linux works fine on few architectures with limited hardware support. I think the right use is like server instead workstation.

---

### Post by ykanello on 2007-05-08
I have also installed debian (not ubuntu didn't have installer when I tried) on PARISC.
On a c3000 workstation. 
Installation went fine, mirrored the disks, boot kernel, OS.
Cannot install drivers for the GLX card I think its called FX4.
So only 1024x768 text mode. (this is my main problem)
But I also managed to use some other hardwre with the Box.
When I had HPUX 11 on the box, i couldnt make the SUN quad ethernet (happymeal) work on the HP workstation. with debian I can. 

Also I want to asnwer that my measurements are only on application level, and response times of http, and other apps that I run.
I do not test graphics cards, or X environments because I really use these boxes as servers and not workstations...

On the attached screenshot, you can see the system's cpu/memory/bandwidth.
I changed the OS at the downtime it seems on end of February.
As you can see the IO load has dropped significantly with ubuntu... and much higher traffic.

[IMG]http://www.gamato.info/getdox.php/Screenshot.png[/IMG]

---

