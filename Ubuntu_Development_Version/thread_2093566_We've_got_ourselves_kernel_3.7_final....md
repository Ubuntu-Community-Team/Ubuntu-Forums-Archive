---
title: "We've got ourselves kernel 3.7 final..."
date: 2012-12-11
forum: Ubuntu Development Version
---

### Post by zika on 2012-12-11
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-raring/)

---

### Post by ventrical on 2012-12-11
Thanks zika. 

One question. Am I to assume that there will be no more release candidates for this cycle?

regards.

---

### Post by zika on 2012-12-11
> **ventrical said:**
> Thanks zika. 

One question. Am I to assume that there will be no more release candidates for this cycle?

regards.As far as my experience goes, we're now to expect 3.7.n where n=1,... and in fortnight 3.8.rc1...

---

### Post by offgridguy on 2012-12-11
> **ventrical said:**
> Thanks zika. 

One question. Am I to assume that there will be no more release candidates for this cycle?

regards.
Thanks for the link to terminal commands.

---

### Post by zika on 2012-12-11
> **offgridguy said:**
> Thanks for the link to terminal commands.
Did You mean this:
```
cd /tmp
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-raring/linux-headers-3.7.0-030700-generic_3.7.0-030700.201212102335_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-raring/linux-headers-3.7.0-030700_3.7.0-030700.201212102335_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-raring/linux-image-3.7.0-030700-generic_3.7.0-030700.201212102335_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-raring/linux-image-extra-3.7.0-030700-generic_3.7.0-030700.201212102335_amd64.deb
sudo dpkg -i linux*.deb
```or something else?
(Commands above are for amd64, easily corrected for i386 via simple substitute...)

---

### Post by synaptix on 2012-12-11
Wonder if this was fixed in final?

[http://www.phoronix.com/scan.php?page=article&item=linux_power_20&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_power_20&num=1)

---

### Post by ronacc on 2012-12-11
still no boot here with 3.7 final so it looks like 3.7 is a total loss for me .

---

### Post by jppr on 2012-12-11
> **ronacc said:**
> still no boot here with 3.7 final so it looks like 3.7 is a total loss for me .

Same here, maybe 3.8 kernel works then ...

---

### Post by serdotlinecho on 2012-12-11
I think the next release will be 3.7.1
Raring for 3.8 release cycle...

---

### Post by zenarcher on 2012-12-11
> **jppr said:**
> Same here, maybe 3.8 kernel works then ...

Same here....no boot for me, either.  Booting gets as far as my USB KVM switch and everything stops.  Using AMD 64 bit CPU's.  Same issue I've had with all revisions of the 3.7 kernel.  3.5 works just fine.

zenarcher

---

### Post by anca-emanuel on 2012-12-11
From: Leann Ogasawara leann.ogasawara [at] canonical.com

We have uploaded a new Raring linux kernel.  Please note the ABI Bump.  The most notable changes are as follows:

Rebase to upstream stable v3.7
Re-enable build of dm-raid45
tools: hv: Netlink source address validation allows DoS (LP: #1084777)
Improved kernel config annotations for Ubuntu kernel config review
SAUCE: ACPICA: Fix ACPI mutex object allocation memory leak on error
SAUCE: drm: Fix possible EDID memory allocation oops
SAUCE: ttm: Fix possible _manager memory allocation oops
SAUCE: iwlwifi: iwlagn_request_scan: Fix check for priv->scan_request
SAUCE: i915: intel_set_mode: Reduce stack allocation from 500 bytes to2 pointers

The full changelog can be seen at:

  [https://launchpad.net/ubuntu/+source/linux/3.7.0-6.14](https://launchpad.net/ubuntu/+source/linux/3.7.0-6.14)

---

### Post by anca-emanuel on 2012-12-11
> **zenarcher said:**
> Same here....no boot for me, either.  Booting gets as far as my USB KVM switch and everything stops.  Using AMD 64 bit CPU's.  Same issue I've had with all revisions of the 3.7 kernel.  3.5 works just fine.

zenarcher
Learn about git bisect.
Learn how to compile an upstream kernel.

[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)


For the first kernel compilation you will need this steps:

sudo apt-get install git kernel-package fakeroot build-essential
git clone git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git
cd linux
cp /boot/config-`uname -r` .config
yes '' | make oldconfig
CONCURRENCY_LEVEL=`getconf _NPROCESSORS_ONLN` fakeroot make-kpkg --initrd kernel_image kernel_headers
cd ..
sudo dpkg -i linux*.deb
sudo reboot


git bisect --help

---

### Post by ronacc on 2012-12-11
> **anca-emanuel said:**
> Learn about git bisect.
Learn how to compile an upstream kernel.

[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)


For the first kernel compilation you will need this steps:

sudo apt-get install git kernel-package fakeroot build-essential
git clone git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git
cd linux
cp /boot/config-`uname -r` .config
yes '' | make oldconfig
CONCURRENCY_LEVEL=`getconf _NPROCESSORS_ONLN` fakeroot make-kpkg --initrd kernel_image kernel_headers
cd ..
sudo dpkg -i linux*.deb
sudo reboot


git bisect --help

compiling a custom kernel is all well and good if your only goal is to optimize YOUR system . However I prefer to test what Ubuntu is actually providing since that is the whole point of this forum .

---

### Post by anca-emanuel on 2012-12-11
Testing mainline kernel is the first step.
Not working ? boot from last known working kernel (3.5 in this situation)

cd linux
git bisect start
git bisect bad
git bisect good v3.5

Delete *.deb in home
Compile again, this time:

CONCURRENCY_LEVEL=`getconf _NPROCESSORS_ONLN` fakeroot make-kpkg --initrd --append-to-version=-bisect1 kernel_image kernel_headers

---

### Post by dino99 on 2012-12-11
> **anca-emanuel said:**
> Testing mainline kernel is the first step.
Not working ? boot from last known working kernel (3.5 in this situation)

git bisect start
git bisect bad
git bisect good v3.5

Delete *.deb in home
Compile again, this time:
cd linux
CONCURRENCY_LEVEL=`getconf _NPROCESSORS_ONLN` fakeroot make-kpkg --initrd --append-to-version=-bisect1 kernel_image kernel_headers

You should make a wiki, as you seems knowing a lot :)

---

### Post by anca-emanuel on 2012-12-11
> **ventrical said:**
> Thanks zika. 
One question. Am I to assume that there will be no more release candidates for this cycle?
regards.

For kernel ?
We will have an 3.8 kernel.
Want some more ? [http://www.youtube.com/watch?v=WwXR89WYkFg](http://www.youtube.com/watch?v=WwXR89WYkFg)

---

### Post by ventrical on 2012-12-11
> **zika said:**
> Did You mean this:
```
cd /tmp
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-raring/linux-headers-3.7.0-030700-generic_3.7.0-030700.201212102335_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-raring/linux-headers-3.7.0-030700_3.7.0-030700.201212102335_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-raring/linux-image-3.7.0-030700-generic_3.7.0-030700.201212102335_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-raring/linux-image-extra-3.7.0-030700-generic_3.7.0-030700.201212102335_amd64.deb
sudo dpkg -i linux*.deb
```or something else?
(Commands above are for amd64, easily corrected for i386 via simple substitute...)

@zika,

They meant the link in my sig :) .. the Sudo Code Quick Grabber :)

---

### Post by ventrical on 2012-12-11
btw .. I downloaded the *.deb files, installed them and it broke xorg. I had to boot into 3.5.n-n to get terminal and:
sudo apt-get update
sudo apt-get upgrade

I finally got my desktop back. I can't find that kernel install anywhere in grub.

 I'm back on :desktop 3.7.0-030700rc8-generic #201212031649 SMP Mon Dec 3 22:00:46 UTC 2012 i686 i686 i686 GNU/Linux

---

### Post by Harry33 on 2012-12-12
> **ventrical said:**
> btw .. I downloaded the *.deb files, installed them and it broke xorg. I had to boot into 3.5.n-n to get terminal and:
sudo apt-get update
sudo apt-get upgrade

I finally got my desktop back. I can't find that kernel install anywhere in grub.

 I'm back on :desktop 3.7.0-030700rc8-generic #201212031649 SMP Mon Dec 3 22:00:46 UTC 2012 i686 i686 i686 GNU/Linux

Does the RR version of 3.7.0 work for you?
Here:
[https://launchpad.net/ubuntu/raring/+source/linux/3.7.0-6.14](https://launchpad.net/ubuntu/raring/+source/linux/3.7.0-6.14)

---

### Post by serdotlinecho on 2012-12-12
Kernel 3.7.0-6.14 i386 is working really well for me :D

---

### Post by zika on 2012-12-12
> **ventrical said:**
> @zika,
They meant the link in my sig :) .. the Sudo Code Quick Grabber :)I'm obviously old and thick (not just due to the age)...
:lolflag:

Update&#8321;:  After quite some time I've got kernel panic (with 996(drm-next yesterday's edition),  while 999(daily, yesterday's edition) works very good...)...

---

### Post by ventrical on 2012-12-12
> **Harry33 said:**
> Does the RR version of 3.7.0 work for you?
Here:
[https://launchpad.net/ubuntu/raring/+source/linux/3.7.0-6.14](https://launchpad.net/ubuntu/raring/+source/linux/3.7.0-6.14)


Yes.. it does.  After using synaptic it installed the new kernel .. but I thought I could do that from the link Zika provided. Somehow, installing from the *.deb files just did not work.. but it is working just fine now.

Linux dale-desktop 3.7.0-6-generic #14-Ubuntu SMP Tue Dec 11 13:15:27 UTC 2012 i686 i686 i686 GNU/Linux

---

### Post by zika on 2012-12-12
> **ventrical said:**
> Yes.. it does.  After using synaptic it installed the new kernel .. but I thought I could do that from the link Zika provided. Somehow, installing from the *.deb files just did not work.. but it is working just fine now.

Linux dale-desktop 3.7.0-6-generic #14-Ubuntu SMP Tue Dec 11 13:15:27 UTC 2012 i686 i686 i686 GNU/LinuxWell, &#8222;method&#8220; I've gave above should work... Are You sure You do not have some broken files or another trouble with dpkg...?
As far as I can see You've installed new generic, not a mainline kernel... Not wanting to be picky but if I were in Your shoes I'd investigate a bit further why &#8222;method&#8220; failed...
Were You among those having trouble with 3.7 kernel?... Old and becoming (more and more) senile... 3.7.0-6 is still in proposed...?

---

### Post by ronacc on 2012-12-12
I'm still stuck on the 3.5 kernel , I've tried all of the repo 3.7's up to and including the current one , several of the mainline RC's and anca-emanuel's suggestion of compiling and bisecting all no help , all ( including the daily lives ) stop at the same place during boot ( attaching drives ) all leave no log files , the only thing logged is sucessful boots to the 3.5 kernel . several other problems but they may have to do with the kernel being so far behind everything else .

---

### Post by wnelson on 2012-12-12
I use the following, for less bloat!

This updates the configuration to only compile modules that are actually used in your system:

make localmodconfig 

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

Walt

---

### Post by ventrical on 2012-12-12
> **zika said:**
> Well, „method“ I've gave above should work... Are You sure You do not have some broken files or another trouble with dpkg...?
As far as I can see You've installed new generic, not a mainline kernel... Not wanting to be picky but if I were in Your shoes I'd investigate a bit further why „method“ failed...
Were You among those having trouble with 3.7 kernel?... Old and becoming (more and more) senile... 3.7.0-6 is still in proposed...?


 I had no problems with the mainline kernels .. all the way up to rc8 .. both 64bit and 32 bit.. I even installed 3.7.rc8 on Lucid install and that worked (but had nVidia error).

  It was just a 'blip' when I manually installed the 'final' 3.7.0-6.14. That swhen everything went south .. but all was recovered .. broken xorg and abi13 fixed with synaptic..etc..

no .. you are not senile at all zika. :) .. sometimes I get some-timers (sometimers means one forgets things sometimes)  but at least I am not having sometimers all-the-timers :) so .. I think we all get sometimers sometimes.  ? :)

---

### Post by VinDSL on 2012-12-16
> **zika said:**
> [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-raring/)
Finally got around to upgrading.  Very nice, really! :)

5+ hours, in this session, and everything is noticeably snappier than rc-8.

Anxiously awaiting v3.8 testing...

---

### Post by The Spectre on 2012-12-16
I have been running the Linux Kernel 3.7 since it was released and it has been rock solid for me.

For the upgrade I used the method from this site...
[http://www.upubuntu.com/2012/12/installupgrade-to-linux-kernel-37-under.html](http://www.upubuntu.com/2012/12/installupgrade-to-linux-kernel-37-under.html)

I have also successfully upgraded to various 3.6.x versions over the past couple of months when this site has posted the Kernel Update.

For the people that are have problems booting after the Kernel Update, I experienced a similar issue during one of the 3.6.x updates and for me it turned out to be the AMD/ATI Proprietary driver that was the problem.
I uninstalled the AMD/ATI Proprietary driver and then Updated the Kernel and the computer Booted up without any issues.

---

### Post by zika on 2012-12-17
Just to see if [this](http://users.on.net/~ckolivas/kernel/) will get into [this](https://launchpad.net/~chogydan/+archive/ppa) or I will have to compile it for myself...
It is nice to see that Con is back...

---

### Post by nomenkultur on 2012-12-17
3.7.0-6-generic #14-Ubuntu SMP Tue Dec 11 13:13:42 UTC 2012 x86_64

 stable and solid. 

 When will k3.8 be implemented into 13.04?? 


 only thing I can complain about is the slow dash perfomance under intel gfx, but it improved when I use those mesa codes...

 now I'm hoping for significant improvements in 3.8 since intel claims to have been working on their drivers

---

### Post by zika on 2012-12-17
> **nomenkultur said:**
> 3.7.0-6-generic #14-Ubuntu SMP Tue Dec 11 13:13:42 UTC 2012 x86_64

 stable and solid. 

 When will k3.8 be implemented into 13.04?? 


 only thing I can complain about is the slow dash perfomance under intel gfx, but it improved when I use those mesa codes...

 now I'm hoping for significant improvements in 3.8 since intel claims to have been working on their drivers
3.8 should emerge fortnight after 3.7 was published on mainline...
So, by a simple math, we could expect it on mainline on 25th of December...
Later we will have official 3.8 in Ubuntu...

---

### Post by VinDSL on 2012-12-17
> **zika said:**
> Just to see if [this](http://users.on.net/~ckolivas/kernel/) will get into [this](https://launchpad.net/~chogydan/+archive/ppa) or I will have to compile it for myself...
It is nice to see that Con is back...
I am so glad to hear him say this...

[QUOTE=Con]
**[SIZE="+1"]Kernel patch homepage of Con Kolivas[/SIZE]**

These are patches designed to **[COLOR="Red"]improve system responsiveness and interactivity[/COLOR]**
with specific emphasis on the desktop, but suitable to any workload.[/QUOTE]
Whenever I comment on a kernel (such as 3.7 final) making everything  "noticeably snappier", invariably someone will quip, "Oh, yeah?  How can a kernel make a desktop snappier?"

So it is written, so it is done...  LoL!  :D

---

### Post by jerrylamos on 2012-12-17
> **VinDSL said:**
> I am so glad to hear him say this...

Whenever I comment on a kernel (such as 3.7 final) making everything  "noticeably snappier", invariably someone will quip, "Oh, yeah?  How can a kernel make a desktop snappier?"

So it is written, so it is done...  LoL!  :D

I'll give it a go when it comes in.  The final, that is, whatever it is. I just compared gtkperf on raring 3.7.0-7 to meerkat 10.10 and raring took over twice as long.  Very visible slowdown.  The drivers etc. are whatever ubuntu does "out of the box" on an install.  ATI RC410 Radeon Xpress 200.

---

### Post by rrnbtter on 2012-12-17
Greetings,
I find all of this interesting. I clean installed my RR on Dec 4 and the kernel version was 3.7.0.4. No lockups no problems and it is currently updated to  v3.7.0.6. Everything that I'm interested in works perfect.  Best OS I have ever used! Toshiba Intel Chipset single processor, GM45 Vid with 1.2G of Video Ram out of 4Gig total ram. 

FYI
rrnbtter
Life is good! Live it to the Ubuntu-ist!

---

### Post by craig10x on 2012-12-17
I know a lot of you are testing 13.04 but considering it's in early alpha stage, do you think it would be "safe" enough to use as a primary distro? As the updates come in and features change, do you still find it reliable and no breakage?

Just curious ;)
I ran it live and like it a lot...but was a bit chicken about installing :D

---

### Post by ronacc on 2012-12-17
do not use raring or any development version as your only distro , severe breakage is possible at any time . It may be rock stable today and not boot at all tomorrow .

---

### Post by VinDSL on 2012-12-17
Linux 3.7.1 mainline kernel has been released.

So far, so good...

```

vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 12.12.06 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch:" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    Dell UltraSharp 1907FP (analog input)" && echo  && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 12.12.06 (vindsl.com) ~
Current Date/Time: Mon Dec 17 19:17:27 MST 2012
Distro Release: Ubuntu Raring Ringtail (development branch)
Kernel Release: Linux 3.7.1-030701-generic
Gnome Release: GNOME Shell 3.7.2
Unity Release: unity 6.6.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.64

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 106
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2+edgers~quantal
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

Xserver Xorg Core Branch:
  Installed: 2:1.13.0.902+git20121207+server-1.13-branch.ede07c1a-0ubuntu0ricotz~quantal

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[02]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (339x271 millimeters)
  resolution:    96x96 dots per inch

```

---

### Post by rrnbtter on 2012-12-17
Greetings, 
It's a testing version so test it if you want to. Over 400 beans suggests you at least know your way around.  It has a pretty good chance of crashing over a 4 month period. So make sure your installation procedure protects your data.  Also, make sure "proposed" in the update manager is turned off since these are incomplete packages. I also backup my var/apt/cache dir before an update so that I can update easily to that point if I have to reinstall.  
The only warning that I can think of is that if you don't know how to backup and protect your home partition then don't use your test installation as primary.  
 
I use 13.04 as my main system and I don't care what the results are. It takes 1 hour max to get it back up and thats no big deal for me. 
Just MHO!

rrnbtter
Life is good! Live it to the Ubuntu-ist!

---

### Post by craig10x on 2012-12-17
Thanks for the input, guys...
I think i will probably wait then for the final release...going to be a long wait ;)

I saw some improvements for me on 13.04 over 12.04 and 12.10 (which i am currently running) so i guess that is why i got anxious...but i will just have to have a few beers, calm down and be patient :lolflag:

---

### Post by rrnbtter on 2012-12-17
Greetings,
It seems that since the 3.7.0-7 update the shut-down link is just going to log-out. Endless cycle.  Using "sudo shutdown +0 -h . 
FYI

rrnbtter
Life is good! Live it to the Ubuntu-ist!

---

### Post by serdotlinecho on 2012-12-18
Working smooth here on my netbook:

```
~$ apt-cache policy linux-image-generic linux-headers-generic xserver-xorg xserver-xorg-video-intel | cut -d "/" -f 6
```

```
unity:
  Installed: 6.12.0daily12.12.05-0ubuntu1
  Candidate: 6.12.0daily12.12.05-0ubuntu1
  Version table:
 *** 6.12.0daily12.12.05-0ubuntu1 0
main i386 Packages

compiz:
  Installed: 1:0.9.9~daily12.12.05-0ubuntu2
  Candidate: 1:0.9.9~daily12.12.05-0ubuntu2
  Version table:
 *** 1:0.9.9~daily12.12.05-0ubuntu2 0
main i386 Packages

linux-image-generic:
  Installed: 3.7.0.7.11
  Candidate: 3.7.0.7.11
  Version table:
 *** 3.7.0.7.11 0
main i386 Packages

linux-headers-generic:
  Installed: 3.7.0.7.11
  Candidate: 3.7.0.7.11
  Version table:
 *** 3.7.0.7.11 0
main i386 Packages

xserver-xorg:
  Installed: 1:7.7+1ubuntu4
  Candidate: 1:7.7+1ubuntu4
  Version table:
 *** 1:7.7+1ubuntu4 0
main i386 Packages

xserver-xorg-video-intel:
  Installed: 2:2.20.16-0ubuntu1
  Candidate: 2:2.20.16-0ubuntu1
  Version table:
 *** 2:2.20.16-0ubuntu1 0
main i386 Packages

```

---

### Post by craig10x on 2012-12-19
Just curious, but would ubuntu 12.10 eventually be getting this kernel in it's updates?  Or is this really for 13.04 only?

---

### Post by serdotlinecho on 2012-12-20
> **craig10x said:**
> Just curious, but would ubuntu 12.10 eventually be getting this kernel in it's updates?  Or is this really for 13.04 only?

I don't think so. Quantal will continue using and updating kernel 3.5.  But you can download and manually install the latest stable kernel 3.7.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.1-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.1-raring/)

---

### Post by mcellius on 2012-12-20
I'm using the 3.7.1 kernel in Quantal and it works perfectly - at least so far.  It could be that something due to the kernel will eventually go wrong, but as I installed and ran all the 3.6 versions and then moved up to 3.7, and all has been good, I have only good things to say about these kernels.  Of course, your mileage may vary, but it's easy enough to boot into an older kernel if something goes wrong.  (I first tested on a non-production installation of Quantal, on a non-production laptop, but now I'm running it on my producton desktop, too.  And I backup, too, just to be safe.)

---

### Post by zika on 2012-12-20
It looks like we are into a nice 3.8-kernel...
996 (drm-next) doesn't live long on my machine but 999 (daily) (after couple of days with problems) works nice today...
5 days to go and counting...

---

### Post by craig10x on 2012-12-20
Thanks Serdotlinecho...I thought that might be the case...
Would that be "safe" to add to 12.10?  
And if added, would the ubuntu update manager then update it from there or would manual installs be needed for any updates on this kernel?

Which lines would you would need to grab from that download page you linked to?  (i have a new computer with 64 bit and run 64 bit ubuntu 12.10...
Thanks

---

### Post by zika on 2012-12-20
> **craig10x said:**
> Thanks Serdotlinecho...I thought that might be the case...
Would that be "safe" to add to 12.10?  
And if added, would the ubuntu update manager then update it from there or would manual installs be needed for any updates on this kernel?

Which lines would you would need to grab from that download page you linked to?  (i have a new computer with 64 bit and run 64 bit ubuntu 12.10...
ThanksThere is no safe stuff here in this part of Forum...
As it is given above:
```
cd /tmp
wget  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.1-raring/linux-headers-3.7.1-030701-generic_3.7.1-030701.201212171620_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.1-raring/linux-headers-3.7.1-030701-generic_3.7.1-030701.201212171620_amd64.deb)
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.1-raring/linux-headers-3.7.1-030701_3.7.1-030701.201212171620_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.1-raring/linux-headers-3.7.1-030701_3.7.1-030701.201212171620_all.deb)
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.1-raring/linux-image-3.7.1-030701-generic_3.7.1-030701.201212171620_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.1-raring/linux-image-3.7.1-030701-generic_3.7.1-030701.201212171620_amd64.deb)
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.1-raring/linux-image-extra-3.7.1-030701-generic_3.7.1-030701.201212171620_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.1-raring/linux-image-extra-3.7.1-030701-generic_3.7.1-030701.201212171620_amd64.deb)
sudo dpkg -i linux*.deb
```Yes, it has to be done for any new kernel from mainline... No automatic updates...
Remember to purge previous kernel from mainline once You're finished with it so You will not collect old stuff afterwards...
Also be sure to select this new kernel on Your Grub screen while booting...

---

### Post by kevpan815 on 2012-12-20
> **zika said:**
> [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-raring/)

You should probably update that link with the 3.7.1 Link, I tried installing 3.7, then when I had problems installing it, I realized that 3.7.1 was there. :p

---

### Post by zika on 2012-12-21
> **kevpan815 said:**
> You should probably update that link with the 3.7.1 Link, I tried installing 3.7, then when I had problems installing it, I realized that 3.7.1 was there. :p
I did in #47...
I can not edit #1...

---

