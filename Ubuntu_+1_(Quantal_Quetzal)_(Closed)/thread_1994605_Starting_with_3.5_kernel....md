---
title: "Starting with 3.5 kernel..."
date: 2012-06-03
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by zika on 2012-06-03
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-rc1-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-rc1-quantal/)

As I was reporting in [http://ubuntuforums.org/showthread.php?p=11985120#post11985120](http://ubuntuforums.org/showthread.php?p=11985120#post11985120) this 3.5-rc1 also does not work at my place...
It boils down to```
watchdog hard lockup on cpu {0,1,2}...
kworker/0:2
```
Future for me with new kernels looks bleak ... ;)

---

### Post by pressureman on 2012-06-03
Booted ok here... doing better than 3.4 so far.

```

Linux thinkpad 3.5.0-030500rc1-generic #201206022335 SMP Sun Jun 3 03:36:00 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by zika on 2012-06-03
I've managed to boot with 3.5-daily using &#8222;nomodeset&#8220;... Now to figure out what is happening... ;)
Update&#8321;: It is interesting that &#8222;radeon.modeset=0&#8220; does not work. Only plain &#8222;nomodeset&#8220;...
Update&#8322;: &#8222;radeon.modeset=0&#8220;as a matter of fact works also...

---

### Post by scradock on 2012-06-03
> **pressureman said:**
> Booted ok here... doing better than 3.4 so far.

```

Linux thinkpad 3.5.0-030500rc1-generic #201206022335 SMP Sun Jun 3 03:36:00 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

Also here:

```
Linux scqq 3.5.0-030500rc1-generic #201206022335 SMP Sun Jun 3 03:36:00 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by VinDSL on 2012-06-03
> **zika said:**
> Future for me with new kernels looks bleak ... ;)
Hrm... working fine here.  :(

And, I'm running ancient iron (see sig).  

Maybe you need a "seasoned" computer too...  

Thanks for the link.  Hope things improve for you.

---

### Post by zika on 2012-06-03
> **VinDSL said:**
> Maybe you need a "seasoned" computer too... Well, this much years my computer has is usually enough even for a good wine... ;) DDR2 made me look everywhere just to find Mushkin pair for this beast... ;) It was much younger when it started working with daily kernels just fine. Is this computer of mine entering andropause... ? I've been there some years ago... ;) Calm and peaceful...
Nomodeset, step backwards and long step indeed... ;)

---

### Post by VinDSL on 2012-06-03
Noticed a new phenomena...

[S]Seems like CPU cycles are running higher now, so I invoked HTOP.

LightDM is motorboating up n' down, between 5-49% CPU usage [/S]:confused:

**[COLOR="Sienna"]EDIT[/COLOR]**

DOH!  N/M

I just realized "System Monitor" was running in the background, in another workspace.

Soon as I killed it, LightDM stabilized around 2% CPU usage  :oops:

**[COLOR="DarkRed"]EDIT II[/COLOR]**

BTW, here are the particulars...

```
vindsl@Zuul:~$ echo && echo "~ VinDSL 12.5.22 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch" && apt-cache policy xserver-xorg-core | grep Installed && echo

~ VinDSL 12.5.22 (vindsl.com) ~
Current Date/Time: Sun Jun  3 12:13:59 MST 2012
Distro Release: Ubuntu quantal (development branch)
Kernel Release: Linux 3.5.0-030500rc1-generic
Unity Release: unity 5.12.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 302.11

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
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

Xserver Xorg Core Branch
  Installed: 2:1.12.2+git20120530+server-1.12-branch.97cae5e0-0ubuntu0ricotz

vindsl@Zuul:~$ 

```

---

### Post by matt_symes on 2012-06-03
Seems stable after 40 mins....

```
matthew@matthew-Aspire-7540 ~ % uname -a && uptime
Linux matthew-Aspire-7540 3.5.0-030500rc1-generic #201206022335 SMP Sun Jun 3 03:36:00 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
 21:48:28 up 41 min,  2 users,  load average: 2.20, 2.19, 2.20
matthew@matthew-Aspire-7540 ~ %
```

---

### Post by VinDSL on 2012-06-03
> **matt_symes said:**
> Seems stable after 40 mins....
Yep!  I've been dancing on the keyboard for 3+ hours...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-3-jun-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-3-jun-2012-1.png")[/INDENT]


Very unremarkable, so far -- which, is a good thing!  :)

---

### Post by Starks on 2012-06-04
3.5 mainline kernels are built with LTS toolkits. They aren't supposed to work well.

---

### Post by effenberg0x0 on 2012-06-04
> **zika said:**
> Well, this much years my computer has is usually enough even for a good wine... ;) DDR2 made me look everywhere just to find Mushkin pair for this beast... ;) It was much younger when it started working with daily kernels just fine. Is this computer of mine entering andropause... ? I've been there some years ago... ;) Calm and peaceful...
Nomodeset, step backwards and long step indeed... ;)

Hi Zika, I think one thing we could try, to get to get to the bottom of this, is to diff the kernel .config files of the last version that worked normally there, and the first one after that (where the problem started).

You will have to sort the .config files, to get a usable diff. 
When you create a diff file, it may have a lof of lines. But, for example, if you chose to discard CONFIG_KEYBOARD, CONFIG_MOUSE, Android stuff, etc, irrelevant things, you might get to the true relevant differences. If you can cut it down to, say, 20 potential suspects, it's easy to play with this options and find out what's going on.

I think you know what I'm talking about but, anyway, here's an example:

```
cd /boot
ls config-*
mkdir -p ~/dev/temp/kernel-zika-test/
sudo cp config-3.2.0-23-generic ~/dev/temp/kernel-zika-test/
sudo cp config-3.2.0-24-generic ~/dev/temp/kernel-zika-test/
cd ~/dev/temp/kernel-zika-test/
sort config-3.2.0-23-generic -o config-3.2.0-23-generic-sorted
sort config-3.2.0-24-generic -o config-3.2.0-24-generic-sorted

```

Then compare both *-sorted files using meld, kdiff3, or even diff. I prefer GUI-based diff for large files, my favorite tool for this is meld). Output a diff file. If it's too large, you can sed/awk stuff like Keyboard, Mouse, etc out to get to what is relevant. 

It will be a little boring, but I *think* you will find a solution working this way.

Regards,
Effenberg

---

### Post by VinDSL on 2012-06-04
> **effenberg0x0 said:**
> [M]y favorite tool for this is meld.
Meld rawks!  :guitar:  

Can't do serious coding without a comparator!  I'd surely have gone blind by now, without Meld.

I was thinking about it, as I was reading your post... then, you mentioned it.  Kudos!  :)

---

### Post by jppr on 2012-06-04
developers could first try to correct the update-manager even before the system will bring a new kernel... Sorry my **** english...

---

### Post by zika on 2012-06-04
> **effenberg0x0 said:**
> Hi Zika, I think one thing we could try, to get to get to the bottom of this, is to diff the kernel .config files of the last version that worked normally there, and the first one after that (where the problem started).

You will have to sort the .config files, to get a usable diff. 
When you create a diff file, it may have a lof of lines. But, for example, if you chose to discard CONFIG_KEYBOARD, CONFIG_MOUSE, Android stuff, etc, irrelevant things, you might get to the true relevant differences. If you can cut it down to, say, 20 potential suspects, it's easy to play with this options and find out what's going on.

I think you know what I'm talking about but, anyway, here's an example:

```
cd /boot
ls config-*
mkdir -p ~/dev/temp/kernel-zika-test/
sudo cp config-3.2.0-23-generic ~/dev/temp/kernel-zika-test/
sudo cp config-3.2.0-24-generic ~/dev/temp/kernel-zika-test/
cd ~/dev/temp/kernel-zika-test/
sort config-3.2.0-23-generic -o config-3.2.0-23-generic-sorted
sort config-3.2.0-24-generic -o config-3.2.0-24-generic-sorted

```Then compare both *-sorted files using meld, kdiff3, or even diff. I prefer GUI-based diff for large files, my favorite tool for this is meld). Output a diff file. If it's too large, you can sed/awk stuff like Keyboard, Mouse, etc out to get to what is relevant. 

It will be a little boring, but I *think* you will find a solution working this way.

Regards,
EffenbergAs soon as I find enough time for this I'll do it. It is easy,:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-quantal/) works
[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2012-06-03-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2012-06-03-quantal/) needs nomodeset...
So, if I do not get enough spare time to make diff is is easy for anybody else to do that...
Good advice. Thank You...
But, the only thing that discourages me in that endeavor is that it is probably a labor in vain. I'm waiting for solution of [http://ubuntuforums.org/showthread.php?t=1867927](http://ubuntuforums.org/showthread.php?t=1867927) for ages... ;) There I've isolated a culprit...

---

### Post by effenberg0x0 on 2012-06-04
> **zika said:**
> 
[...]
But, the only thing that discourages me in that endeavor is that it is probably a labor in vain. I'm waiting for solution of [http://ubuntuforums.org/showthread.php?t=1867927](http://ubuntuforums.org/showthread.php?t=1867927) for ages... ;) There I've isolated a culprit...

I completely understand that... As a side note, I gave up pushing for fixes of some known bugs (Ubiquity, partitioning, plymouth, link for offline documentation at launcher after install, etc) a while ago and don't feel like repeatedly testing stuff known to be broken or posting bug reports about Unity only. Without getting too much into the politics of it, IMO we've been through a dark age in testing for some releases, it will reach it's lowest point in QQ and, hopefully, only last up to UDS-S. 

Anyway, I have noticed that bug reports of some upstream projects and mainly kernel, outside Ubuntu scope, do get fixed. In kernel, if we can get to the problem, we can probably locate the email of the contributor responsible for that piece of code and contact him. It has worked for me a couple times.

Regards,
Effenberg

---

### Post by zika on 2012-06-09
3.5 (both rc2 and daily) (I've just tried) work OK on my laptop (HP, 386, Intel) on 11.10...
Still no luck on desktop (AMD, 64bit, ATI) on 12.10... Kind of working with nomodeset... :)

---

### Post by fjgaude on 2012-06-09
> **Starks said:**
> 3.5 mainline kernels are built with LTS toolkits. They aren't supposed to work well.

Yep, that answers one issue, gcc 4.6 vs 4.7. With kernel 3.5 in 12.04 I can compile VMware Player modules okay. Can't with 12.10 because of gcc 4.7. Hmmm...

---

### Post by zika on 2012-06-10
> **Starks said:**
> 3.5 mainline kernels are built with LTS toolkits. They aren't supposed to work well.
Why (then) they carry the name of quantal... ;) ?

---

### Post by VinDSL on 2012-06-10
Thanks, for the "heads up", zika!

I'm been logged into UbuQQ/LXDE/Openbox for 5+ hours, today.

Linux 3.5-rc2 is working like a champ!  ;)


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-10-jun-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-10-jun-2012-1.png")[/INDENT]

---

### Post by jerrylamos on 2012-06-10
> **zika said:**
> Why (then) they carry the name of quantal... ;) ?

I just update/upgraded lubuntu precise to "quantal":

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu quantal (development branch)"
Linux ThinkPad-T40 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:52 UTC 2012 i686 i686 i686 GNU/Linux

Now this is a Pentium M with no pae flag so 3.4.0-5 won't install, but it still calls itself quantal.  What does "quantal" signify?

Jerry

---

### Post by zika on 2012-06-11
3.4.0-030400.201205221131 did work on my amd64 machine.
3.4 rc1 did not work on my amd64 machine.
3.4 rc2 does work on my  amd64 machine. That is encouraging since that is a 4-piece kernel also...
any kind of 3.5 does not work on my  amd64 machine... ;)
Just to let You know...

---

### Post by pbhedlund on 2012-06-13
Kernel 3.5 is good as it fixes a bug present in kernels 3.2 (Precise) and 3.4 (Quantal) in nouveau that makes those kernels  unusable on Nvidia 320M graphics adapters. See [https://bugs.launchpad.net/ubuntu/+s...au/+bug/898784]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/898784") and linked bug reports.

---

### Post by pressureman on 2012-06-13
I've had practically zero problems with 3.5rc1. It boots every time without fail, which is more than I can say for 3.4. I don't even bother trying the 3.4 official kernels anymore, since 3.5 is supposed to land in the main repos sometimes before October anyway.

I'm just about to install 3.5rc2.

---

### Post by matt_symes on 2012-06-13
> **pressureman said:**
> I've had practically zero problems with 3.5rc1. It boots every time without fail, which is more than I can say for 3.4. I don't even bother trying the 3.4 official kernels anymore, since 3.5 is supposed to land in the main repos sometimes before October anyway.

I'm just about to install 3.5rc2.

I've had some random graphics freezing with -rc1 when coming out of suspend.

-rc2 has been much better for me though.

---

### Post by 3vi1 on 2012-06-16
So far, rc2 kernel works much better than the 3.4 kernel here.  I couldn't get any of the 3.4's to stay running for more than a couple of minutes without hanging - if it would boot at all.

I also noticed that with 3.4, my usb 3 drives (which often would not even mount) would show up as /run/media/user/label, whereas they are showing up properly in /media/label under 3.5 (though I did have to powercycle them after booting to the desktop to get them to appear).

---

### Post by kevpan815 on 2012-06-16
> **zika said:**
> [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-rc1-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-rc1-quantal/)

As I was reporting in [http://ubuntuforums.org/showthread.php?p=11985120#post11985120](http://ubuntuforums.org/showthread.php?p=11985120#post11985120) this 3.5-rc1 also does not work at my place...
It boils down to```
watchdog hard lockup on cpu {0,1,2}...
kworker/0:2
```
Future for me with new kernels looks bleak ... ;)

I tried to install 3.5 RC2 and it will NOT even install for me.

---

### Post by SpaceCeph on 2012-06-17
RC3 is out. I will try later with a clean QQ install.

---

### Post by VinDSL on 2012-06-17
> **SpaceCeph said:**
> RC3 is out. I will try later with a clean QQ install.
Looks like it's time to do some "housekeeping"...  :D

```

<SNIP>
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.5.0-030500rc3-generic...
P: Writing config for /boot/vmlinuz-3.5.0-030500rc2-generic...
P: Writing config for /boot/vmlinuz-3.5.0-030500rc1-generic...
P: Writing config for /boot/vmlinuz-3.4.0-3-generic...
P: Writing config for /boot/vmlinuz-3.4.0-2-generic-pae...
P: Writing config for /boot/vmlinuz-3.4.0-1-generic-pae...
P: Writing config for /boot/vmlinuz-3.3.0-6.dmz.1-liquorix-686...
P: Writing config for /boot/vmlinuz-3.2.0-14.dmz.1-liquorix-686...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.5.0-030500rc3-generic /boot/vmlinuz-3.5.0-030500rc3-generic
[B][COLOR="DarkRed"]Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-030500rc3-generic
Found initrd image: /boot/initrd.img-3.5.0-030500rc3-generic
Found linux image: /boot/vmlinuz-3.5.0-030500rc2-generic
Found initrd image: /boot/initrd.img-3.5.0-030500rc2-generic
Found linux image: /boot/vmlinuz-3.5.0-030500rc1-generic
Found initrd image: /boot/initrd.img-3.5.0-030500rc1-generic
Found linux image: /boot/vmlinuz-3.4.0-3-generic
Found initrd image: /boot/initrd.img-3.4.0-3-generic
Found linux image: /boot/vmlinuz-3.4.0-2-generic-pae
Found initrd image: /boot/initrd.img-3.4.0-2-generic-pae
Found linux image: /boot/vmlinuz-3.4.0-1-generic-pae
Found initrd image: /boot/initrd.img-3.4.0-1-generic-pae
Found linux image: /boot/vmlinuz-3.3.0-6.dmz.1-liquorix-686
Found initrd image: /boot/initrd.img-3.3.0-6.dmz.1-liquorix-686
Found linux image: /boot/vmlinuz-3.2.0-14.dmz.1-liquorix-686
Found initrd image: /boot/initrd.img-3.2.0-14.dmz.1-liquorix-686
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 10.10 (10.10) on /dev/sda1[/COLOR][/B]
done
<SNIP>

```

**EDIT**

Working like a charm...

```
vindsl@Zuul:~$ echo && echo "~ VinDSL 12.5.22 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch" && apt-cache policy xserver-xorg-core | grep Installed && echo

~ VinDSL 12.5.22 (vindsl.com) ~
Current Date/Time: Sun Jun 17 00:19:32 MST 2012
Distro Release: Ubuntu quantal (development branch)
**[COLOR="DarkRed"]Kernel Release: Linux 3.5.0-030500rc3-generic[/COLOR]**
Unity Release: unity 5.12.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 302.11

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
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

Xserver Xorg Core Branch
  Installed: 2:1.12.2+git20120605+server-1.12-branch.aaf48906-0ubuntu0ricotz

vindsl@Zuul:~$ 

```

---

### Post by firekage on 2012-06-17
Excusme for asking - can you write how to install new kernels or post sites where i could find help with it? I would like to learn it.

---

### Post by VinDSL on 2012-06-17
> **firekage said:**
> Can you write how to install new kernels or post sites where i could find help with it? I would like to learn it.
I use a "shotgun" approach...

Using Linux 3.5-rc3 as an example:

[LIST]
[*]Download the binaries from:
 [INDENT][http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-rc3-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-rc3-quantal/)[/INDENT]
In my case, I download the three files ending in _i386.deb & the file ending in _all.deb, e.g. four files total.


[*]Place these four files in a folder, all by themselves.
[*]Open a terminal (command line interface [aka CLI]).
[*]Navigate (change directory) to the folder containing the four files.
[*]Build them using "dpkg".  I simply use:  sudo dpkg -i *.deb
[*]If all goes well (and it usually does)... reboot.
[*]If all does not go well, fix the problem(s) before rebooting.
[/LIST]
That's about it...  ;)

---

### Post by matt_symes on 2012-06-17
> **SpaceCeph said:**
> RC3 is out. I will try later with a clean QQ install.

Thanks for the heads up SpaceCeph. Installing it now.

---

### Post by firekage on 2012-06-17
> **VinDSL said:**
> I use a "shotgun" approach...

Using Linux 3.5-rc3 as an example:

[LIST]
[*]Download the binaries from:[INDENT][http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-rc3-quantal/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.5-rc3-quantal/")[/INDENT]In my case, I download the three files ending in _i386.deb & the file ending in _all.deb, e.g. four files total.
[*]Place these four files in a folder, all by themselves.
[*]Open a terminal (command line interface [aka CLI]).
[*]Navigate (change directory) to the folder containing the four files.
[*]Build them using "dpkg".  I simply use:  sudo dpkg -i *.deb
[*]If all goes well (and it usually does)... reboot.
[*]If all does not go well, fix the problem(s) before rebooting.
[/LIST]
That's about it...  ;)

Thank you.

One more thing if i may - 

1-how to store old kernel (or make boot with two kernels - choose during boot) when i installed newer using Your tutorial (in order to restore it if i screw something and it won't work again)

2-how to remove old/new kernel after installation when i don't need old or i don't want newer cause it works bad, wrong etc.

I'm sorry for asking in this thread but people here knows what they are doing that's why i wanted to ask.

---

### Post by dino99 on 2012-06-17
the easiest for maintaining packages is to use synaptic:

sudo apt-get install synaptic
sudo synaptic

then select the package(s) you need: for example, install or purge kernel(s)

---

### Post by dino99 on 2012-06-17
This 3.5 rc3 is a good one : less memory used, fan less noisy

only get a warning on a P4 : TSC unstable due to TSC halts in idle

---

### Post by VinDSL on 2012-06-17
> **firekage said:**
> 1-how to store old kernel (or make boot with two kernels - choose during boot) when i installed newer using Your tutorial (in order to restore it if i screw something and it won't work again)
When you boot up, GRUB2 should have a selection called "Previous Linux Versions".  Highlight and choose that, and a second page will appear with all of the previous (earlier) versions that are still installed on your computer. To get back to the original GRUB screen, press [ESC] on your keyboard.

I ALWAYS keep a stable backup version of Ubuntu handy, in case my dev release blows up.  Saved my bacon many, many times! :)

> **firekage said:**
> 2-how to remove old/new kernel after installation when i don't need old or i don't want newer cause it works bad, wrong etc.
As dino said, you can install Synaptic, and use it to uninstall old kernels.  That's what I use.  

Just do a search in Synaptic for "Linux" and "linux-image", "linux-headers", et cetera, will appear in the results.  Choose wisely, which ones you are removing.  I've accidentally deleted the wrong kernel(s) before. LoL!

You can also use Ubuntu Tweak, do it from CLI, and any number of other ways.  ;)

---

### Post by kevpan815 on 2012-06-17
> **jppr said:**
> developers could first try to correct the update-manager even before the system will bring a new kernel... Sorry my **** english...

Pardon me for asking, but how do you correct the problems with Update Manager, and how do you install a New Kernel when executing the files inside of the GUI Interface returns an error inside of Software Center?

---

### Post by kevpan815 on 2012-06-17
> **VinDSL said:**
> I use a "shotgun" approach...

Using Linux 3.5-rc3 as an example:

[LIST]
[*]Download the binaries from:
 [INDENT][http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-rc3-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-rc3-quantal/)[/INDENT]
In my case, I download the three files ending in _i386.deb & the file ending in _all.deb, e.g. four files total.


[*]Place these four files in a folder, all by themselves.
[*]Open a terminal (command line interface [aka CLI]).
[*]Navigate (change directory) to the folder containing the four files.
[*]Build them using "dpkg".  I simply use:  sudo dpkg -i *.deb
[*]If all goes well (and it usually does)... reboot.
[*]If all does not go well, fix the problem(s) before rebooting.
[/LIST]
That's about it...  ;)

Thanks for Sharing, could you tell me what command you used to print that diagnostic info in the Command Line Interface?

---

### Post by kevpan815 on 2012-06-17
> **kevpan815 said:**
> Thanks for Sharing, could you tell me what command you used to print that diagnostic info in the Command Line Interface?

P.S. I tried installing RC3 using your installation method and it worked like a charm!

---

### Post by matt_symes on 2012-06-17
> **kevpan815 said:**
> Thanks for Sharing, could you tell me what command you used to print that diagnostic info in the Command Line Interface?

VinDSL is using these commands. 

```
echo && echo "~ VinDSL 12.5.22 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch" && apt-cache policy xserver-xorg-core | grep Installed && echo
```

I would add them to a script and make the script executable.

---

### Post by kevpan815 on 2012-06-17
> **matt_symes said:**
> VinDSL is using these commands. 

```
echo && echo "~ VinDSL 12.5.22 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch" && apt-cache policy xserver-xorg-core | grep Installed && echo
```

I would add them to a script and make the script executable.

Thanks for Sharing, for some reason when I run that command it does not recognize my ATI Radeon X300 Graphics Card, could it be that it is Too Old to be Recognized?

---

### Post by kevpan815 on 2012-06-17
> **kevpan815 said:**
> P.S. I tried installing RC3 using your installation method and it worked like a charm!

I just tried out today's Daily Kernel Build, which appears to be newer then RC3 and it worked just fine as well.

---

### Post by VinDSL on 2012-06-17
> **kevpan815 said:**
> Thanks for Sharing, for some reason when I run that command it does not recognize my ATI Radeon X300 Graphics Card, could it be that it is Too Old to be Recognized?
I don't have a working ATI card to test those commands on, but...

I'm running ancient iron too, so I doubt age is a factor.

Here's my nVidia 7600GT (with CoolViva Z1 heat pipe cooling)...


[INDENT][IMG]http://vindsl.com/images/CoolViva-Z1-3.png[/IMG][/INDENT]


Doesn't get much older than this rig.  LoL!  :D

---

### Post by kevpan815 on 2012-06-17
> **VinDSL said:**
> I don't have a working ATI card to test those commands on, but...

I'm running ancient iron too, so I doubt age is a factor.

Here's my nVidia 7600GT (with CoolViva Z1 heat pipe cooling)...

Doesn't get much older than this rig.  LoL!  :D

Nice Picture! Thanks 4 Sharing! :-)

---

### Post by VinDSL on 2012-06-17
> **kevpan815 said:**
> Nice Picture! :-)
Thanks!  Camera is 5-years older than my PC.  LoL!

BTW, I just installed Linux 3.4.0-3.dmz.1-liquorix-686 (aka Liquorix).

LINKAGE:  [http://liquorix.net/debian/pool/main/l/linux-liquorix/](http://liquorix.net/debian/pool/main/l/linux-liquorix/)

Installed without issue, and flys like the wind.  Plymouth even works.

Check that CPU usage:


[INDENT][INDENT][IMG]http://vindsl.com/images/vindsl-desktop-17-jun-2012-2.png[/IMG][/INDENT][/INDENT]


Not bad for Unity!

Heh!  Okay, back on topic... ;)

---

### Post by firekage on 2012-06-18
> **VinDSL said:**
> 
Not bad for Unity!

Try to check it with system-monitor applet/gadget in unity panel. I have the same readings on kernel 3.0.0.24 with 4 cores CPU. As a matter of fact with 2% in the same widget but system-monitor applet/gadget for unity panel shows 20-35%.

---

### Post by VinDSL on 2012-06-18
> **firekage said:**
> [...] system-monitor applet/gadget for unity panel shows 20-35%.
Yep!  That's a long-standing system-monitor bug.  ;)

Has to do with the fancy, 32-bit chart windows...

[Bug #93847: Excessive CPU usage by Gnome System Monitor]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/93847")

Ppl have been reporting it for 5 years.  Needs to be fixed upstream.

---

### Post by 3vi1 on 2012-06-20
Mainline 3.5rc2 was working fine here, but 3.5rc3 is a major step backwards for me - it hangs just like the 3.4 kernels on my machine.  :(

When it hangs, the machine goes totally locked (no sysreq-RSEIUB, nor even response from the caps-lock key on my USB keyboard).

The last things I could see in the log were messages about it discovering my USB3 devices.  Though I'm not sure if that's the cause of the hangs or it just didn't have time to flush subsequent messages.

---

### Post by zika on 2012-06-21
Ubuntu version of 3.5 kernel arrived. Not working (still) on my AMD machine Hard freeze without and heavy problems even with &#8222;nomodeset&#8220;...
I'm still afraid that QQ will be a struggle for me, kernel-wise...

---

### Post by fjgaude on 2012-06-21
The 3.5 kernel is working just fine on 12.10 Intel graphics machine. An old story...

---

### Post by zika on 2012-06-27
[http://ubuntuforums.org/showpost.php?p=12057667&postcount=11](http://ubuntuforums.org/showpost.php?p=12057667&postcount=11)

Something clicked: even 3.5.0-999-generic #201206270421 today works... ;) Nice...

---

### Post by VinDSL on 2012-07-01
I installed Linux 3.5.0-rc5-quantal about an hour ago.

LINKAGE: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-rc5-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-rc5-quantal/)

Working fine, here...  ;)

---

### Post by frogotronic on 2012-07-07
> **firekage said:**
> Excusme for asking - can you write how to install new kernels or post sites where i could find help with it? I would like to learn it.

I just tried out the [XOrg.EDGERS PPA]("https://launchpad.net/~xorg-edgers/+archive/ppa") and it installed the 3.5.0-3 kernel.  So would that be 3.5rc3?

BYW:  Prior to upgrading with the XOrg.EDGERS PPA, I was running a PAE kernel - I assume that the new Generic Kernels now incorporate *both* PAE and non-PAE kernels, so that it should automagically install whichever is appropriate?  Can someone explicitly confirm this?

Thanks,
CH

---

### Post by jerrylamos on 2012-07-07
I've an IBM Thinkpad T40 with Pentium M which does not have the pae flag.  Quantal with "-generic" tests for the flag and refuses to boot on it.

Someplace in this forum the pundits explain why they changed the Quantal kernel generic-pae to generic even though it tests the pae flag and won't boot without it.

Now whether it really needs the pae function is another question...

Jerry

---

### Post by dino99 on 2012-07-08
rc6 is out

---

### Post by thotz on 2012-07-08
> **dino99 said:**
> rc6 is out
Just wanted to post it :)

Here is the link: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-rc6-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-rc6-quantal/)

---

### Post by frogotronic on 2012-07-08
> **jerrylamos said:**
> I've an IBM Thinkpad T40 with Pentium M which does not have the pae flag.  Quantal with "-generic" tests for the flag and refuses to boot on it.

Someplace in this forum the pundits explain why they changed the Quantal kernel generic-pae to generic even though it tests the pae flag and won't boot without it.

Now whether it really needs the pae function is another question...

Jerry

I think it was changed because Linus Torvalds has changed it, in others words, God has decided, and thus it is so...

Yep, old machines without the PAE flag will no longer be supported on 12.10.

- CH

---

### Post by matt_symes on 2012-07-08
> **dino99 said:**
> rc6 is out

> **thotz said:**
> Just wanted to post it :)

Here is the link: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-rc6-quantal/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.5-rc6-quantal/")

Thanks for keeping us informed.

Just installed and going for a reboot :)

---

### Post by pressureman on 2012-07-08
> **cement_head said:**
> I think it was changed because Linus Torvalds has changed it, in others words, God has decided, and thus it is so...

Yep, old machines without the PAE flag will no longer be supported on 12.10.

- CH

NX (No/Never eXecute) requires PAE.

I'm not a Fedora user, but the release notes for Fedora 11 (which is going back a while now) state that a PAE kernel is used by default on 32 bit hardware.

I don't really see what the big deal is. If you have 32-bit, non-PAE hardware, your options with Ubuntu are to continue running 12.04 LTS - that's right, a Long Term Support release - which got a last-minute reprieve to retain non-PAE support.

If you want to run Ubuntu 12.10 or later, either get a post-1995 32 bit box, or migrate to 64 bit (which the vast majority of Intel/AMD CPUs are these days).

Yes, I know it's rough... finding 32 bit hardware that was manufactured less than 17 years ago, to run an OS release that is not even a few months old. But there may be some second hand gear on eBay for under $3000.

Seriously, anybody would think you were being charged for this software....

---

### Post by jerrylamos on 2012-07-08
> **pressureman said:**
>  finding 32 bit hardware that was manufactured less than 17 years ago, to run an OS release that is not even a few months old.
I think my IBM Thinkpad T40 was manufactured about 2006. 2012 - 2006 = 6. 

What memory size requires PAE?  Is it 4 MB?  I've got 3 pc's purchased over the last 3 years that don't have that much memory.  

How soon will it be that Ubuntu drops support of 32 bit?  I do have one notebook that runs 64 bit.  My netbook, tower, and two compact pc's are all 32 bit.

Jerry

---

### Post by ronacc on 2012-07-08
with yesterdays daily I finally got a semi stable install . The 1st one since 3.5.0-1 .

---

### Post by pressureman on 2012-07-08
> **jerrylamos said:**
> I think my IBM Thinkpad T40 was manufactured about 2006. 2012 - 2006 = 6. 

What memory size requires PAE?  Is it 4 MB?  I've got 3 pc's purchased over the last 3 years that don't have that much memory.  

How soon will it be that Ubuntu drops support of 32 bit?  I do have one notebook that runs 64 bit.  My netbook, tower, and two compact pc's are all 32 bit.

Jerry

PAE has been around in Pentium Pros since 1995. Of course, some budget-constrained 32-bit CPU variants may not have had it (although I've only encountered one such CPU in the last seven years). It's a case of "buyer beware."

32-bit CPUs are and always will be limited to 4GB (2^32 bytes) virtual address space. However, PAE (eg. 36-bit physical memory addressing) allows the CPU to address memory beyond the 4GB limit (up to 64GB), albeit still only in chunks of max 4GB at a time. If you're running processes that need to address more than 4GB of virtual address space, you will have to migrate to 64 bit. No way around that.

I strongly doubt that Ubuntu will drop support for 32-bit anytime soon. They're just dropping support for non-PAE 32-bit, which IMHO is fair enough, considering the rarity / vintage of such hardware, and the numerous releases that have supported such CPUs for almost a decade now.

The point I'm trying to drive home is that your non-PAE hardware hasn't turned into a pumpkin overnight, just because it won't run Ubuntu 12.10. It still runs 12.04 LTS. I seriously hope we're not still debating this in April, 2017, when that version reaches EOL.

---

### Post by jerrylamos on 2012-07-09
> **pressureman said:**
> I strongly doubt that Ubuntu will drop support for 32-bit anytime soon.What's "cloud computing" going to do to this picture?  Will it force 128 bit processors?  I've been in computing since 1959 sometimes things are pretty static over 5 years sometimes there are a couple revolutions. > The point I'm trying to drive home is that your non-PAE hardware hasn't turned into a pumpkin overnight, just because it won't run Ubuntu 12.10. I'm running Meerkat {support dropped} 12.04 Lubuntu, two siamese 12.04 partly upgraded to 12.10 except for kernel and some packages> It still runs 12.04 LTS. I seriously hope we're not still debating this in April, 2017, when that version reaches EOL.Yeh, it won't last that long...at this point it's running 12.04/10 just fine, very useful laptop.

Jerry

---

### Post by jerrylamos on 2012-07-09
BTW, on topic, 3.5 has been giving me fits on "automatic connection" - NOT - to wireless WPA security with my  Intel Corporation Centrino Wireless-N 1000.  That's pretty recent hardware bought last November.  Bug #101983 with Ubuntu kernel, bugzilla 44291 with upstream kernel.  Cold boot might "autoconnect" in a couple minutes, might take 5 minutes and still not connected so I do a manual connect with really turgid menu response like 30 to 40 seconds to a mouse click with a 1.66 gHz dual core...

Anyone else running wireless WPA security?  My Broadcom on my widescreen notebook has similar trouble but much faster.  Some big difference in "3.5" - driver interaction.

"3.5" also has trouble supporting 1366x768 TV external monitor easier on the eyes than the netbook's 1024x600.  Systems Settings Display won't handle it so I do an xorg.conf, a .xprofile, and an exec to give it a boot in the pants.  I don't know how many people are trying to do this....

I'm able to "work around" these quirks I don't know how many will be present at release, or how many Ubuntu target customers will hit these and give up.  Development unstable can hit some configurations which are far from "plug and play". 

Having fun anyway,

Jerry

---

### Post by ronacc on 2012-07-09
3.5 seems to have lots of hardware problems , my test box is a reasonably modern AMD64/nvidia box and I just yesterday got an almost stable daily install , the 1st one since the start of the 3.5 kernels . I say "almost" since once I managed to get gnome shell installed it won't kernel panic too often , unity ( which I don't care about panics almost immediately ). I have no security on my router and auto connect is flaky here too . it sees the router but sometimes don't connect unless I click on it .

---

### Post by VinDSL on 2012-07-09
> **ronacc said:**
> with yesterdays daily I finally got a semi stable install . The 1st one since 3.5.0-1 .
Heh!  I accidentally booted into Linux 3.5-rc4 this morning.

OMG!!! What a mess?!?!?  My cursor would flash, then disappear, every time I moved it, et cetera, et cetera.

Linux 3.5-rc6 is working MUCH better for me...  ;)

---

### Post by ronacc on 2012-07-09
I keep my daily installs pristine and just replace frequently , so I get whatever the repos choose to give me .:P

---

### Post by Harry33 on 2012-07-10
The 3.5-rc6 is in QQ repos soon (can be manually downloaded already).
Here:
[https://launchpad.net/ubuntu/quantal/+source/linux/3.5.0-4.4](https://launchpad.net/ubuntu/quantal/+source/linux/3.5.0-4.4)

---

### Post by nsicad on 2012-07-18
I tried 3.5.rc7 in MacbookPro retina, 

"Switching to clocksource"

Then it hangs (i.e. power is cut off from external usb drive). 

Booting external usb hard drive using 3.2 kernel in MacBookPro retina, but wireless in not working, hence I am trying 3.5.x.

---

### Post by ronacc on 2012-07-18
I'm convinced that there is something about my hardware that 3.5 don't like , I would try the rc6 if I could get an install that was stable enough to install it . Ever since the start of 3.5 I get kernel panics when ever I try to actualy do something , that is if it even gets to DT without panicking and that is if the installer don't crash before I actually get a daily to install .

---

### Post by effenberg0x0 on 2012-07-18
Hi Ron, I've been trying to refrain from interfering in testing this cycle, but I'm a little puzzled by the problems you and also Zika and others are reporting. 

IMO, this requires real testing, the kind that has always been done at Ubuntu+1. Frankly, finding this bug before it gets through to newer releases depends on the people that reported in this thread - none of the currently available testing processes and trackers, unfortunately, covers the big issues. It won't be tested in large scale and won't get fixed unless you guys find something and directly report it to kernel.org. 

For yet another release we still don't have a working and useful way to automatically compare testers hardware profiles. It should be 2 clicks away by now, after some releases we have been talking about it. Well, nothing to do about it - the comparison will have to be done manually. 

My suggestion is that we try to compare your hardware here, in as much detail as possible. If affected users could upload their lshw, we can work to diff them. In the case of those that can't get a stable enough system to debug it, I suggest they kexec 3.5 from a stable kernel (so you can all get better dumps on a crash), stuff like that. This is easy to do and there are tutorials everywhere. 

Something is clearly wrong and we shouldn't deal with the risk of perpetuating it to newer kernels, for the sake of Ubuntu. For lack of other resources, maybe this thread could be the only chance we have of fixing this and avoiding an unknown percentage of broken Ubuntu installs when QQ is released. 

I volunteer to help with whatever people here need.

Regards,
Effenberg

---

### Post by ronacc on 2012-07-18
there is definitely a problem here with the 3.5 kernel and some hardware  but obviously not all . and compounding that are problems with apport and ubiquity and we have a real mess on our hands .  I am quite certain that the problem I am having is a kernel . While I have not been able to get a stable install of a recent daily I do have a precise install updated at repo open and kept up to date and it runs well as long as I select the 3.4.0-5 or before kernel at boot , If I select any of the 3.5 kernels I get immediate kernel panics just like the recent dailys when I can get them to install . Unfortunately when the kernel panics it leaves no tracks behind that I can file a bug with .

---

### Post by Harry33 on 2012-07-19
Linux 3.5 rc-7 is in repos now.
Here:
[https://launchpad.net/ubuntu/quantal/+source/linux/3.5.0-5.5](https://launchpad.net/ubuntu/quantal/+source/linux/3.5.0-5.5)

---

### Post by JMB74 on 2012-07-19
Getting this problem in the RC7 (3.5.0-5.5) of blank screen when resuming from suspend (intel cards?).

[https://lkml.org/lkml/2012/7/15/104](https://lkml.org/lkml/2012/7/15/104)

Fixed upstream in: [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=blobdiff;f=kernel/time/timekeeping.c;h=3447cfaf11e7d61b11d30bc063967e47d85e59d4;hp=269b1fe5f2ae2f7e6c0bb0fac8ce9a54e2d4d278;hb=3e997130bd2e8c6f5aaa49d6e3161d4d29b43ab0;hpb=33d519feaccb8a1208f736d00f53a2a73d98ffaa](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=blobdiff;f=kernel/time/timekeeping.c;h=3447cfaf11e7d61b11d30bc063967e47d85e59d4;hp=269b1fe5f2ae2f7e6c0bb0fac8ce9a54e2d4d278;hb=3e997130bd2e8c6f5aaa49d6e3161d4d29b43ab0;hpb=33d519feaccb8a1208f736d00f53a2a73d98ffaa)

3.5.0-4.4 pre-dates the problem commit, so works OK.

A daily build later than 16 July from the kernel repo also seems OK as presumably contains the fix.

---

### Post by VinDSL on 2012-07-22
3.5-quantal mainline kernel is available now:

[INDENT][http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-quantal/)[/INDENT]

Working fine, here... :)

---

### Post by fdellale on 2012-07-22
I've installed kernel 3.5 and my laptop (Dell E6410 with Ubuntu 12.04) gets stuck during boot.
I've tried to reboot several times removing the quiet and splash options trying to understand where is the problem but  it seems that the pc gets stuck in different places (sometimes when loading apparmor, sometimes when loading battery-stats,..) .
With 3.4.5 everything works fine.
How can I understand where the problems are? (attached a couple of screenshots related to 2 consecutive reboots)

---

### Post by effenberg0x0 on 2012-07-22
> **fdellale said:**
> I've installed kernel 3.5 and my laptop (Dell E6410 with Ubuntu 12.04) gets stuck during boot.
I've tried to reboot several times removing the quiet and splash options trying to understand where is the problem but  it seems that the pc gets stuck in different places (sometimes when loading apparmor, sometimes when loading battery-stats,..) .
With 3.4.5 everything works fine.
How can I understand where the problems are? (attached a couple of screenshots related to 2 consecutive reboots)

<WildGuessMode>
1) Both your pics show network connection manager close to the stall. Considering things that have happened in the past, there's a chance of problems with NIC module and/or modem-manager and/or network-manager. I would investigate these first (considering no other info is available for debugging).
2) Maybe it's just not loading the vga kernel module, not going into X. If that's the case, all you'd have to do is reinstall your VGA drivers.

Some other ideas:
- Boot using an older kernel via Grub or boot to a live-USB, mount / and check /var/log/kernel.log just to make sure no usable info was dumped there;
- Check if you can get a VT with Ctrl+Alt+F1(F1 to F6 actually);
- See if you can get a little more info with SysRq+c (maybe you could try SysRQ+K before SysRq+c);
- Maybe boot with nomodeset or to vesa. With some luck you can get a system stable enough to debug. It would make some sense to try clocksource=tsc (default=hpet) and nohz=off (default=on).
</WildGuessMode>

Regards,
Effenberg

---

### Post by kyleabaker on 2012-07-22
> **ronacc said:**
> there is definitely a problem here with the 3.5 kernel and some hardware  but obviously not all . and compounding that are problems with apport and ubiquity and we have a real mess on our hands .  I am quite certain that the problem I am having is a kernel . While I have not been able to get a stable install of a recent daily I do have a precise install updated at repo open and kept up to date and it runs well as long as I select the 3.4.0-5 or before kernel at boot , If I select any of the 3.5 kernels I get immediate kernel panics just like the recent dailys when I can get them to install . Unfortunately when the kernel panics it leaves no tracks behind that I can file a bug with .

I'm in a similar situation. I've had to revert to either using kernel 3.4.0-5 or simply booting back into 12.04 (which I've been doing for a week or so now).

I don't mind alpha builds being unreliable, but its a little disturbing that this appears to be a non-Ubuntu specific issue and something deeper in the Kernel. I'm downloading a daily build now and will attempt a fresh install, but its not looking very promising.

The Alpha 2 installer wouldn't even boot up for me. I get the following error:

```
[   16.916754] journal commit I/O error
[   18.690150] Kernel panic - not syncing: Attempted to kill init | exitcode=0x00000100
[   18.690150]
[   18.690166] Pid: 1, comm: run-init Not tainted 3.5.0-2-generic #2-Ubuntu
[   18.690172] Call Trace:
[   18.690181]  [<ffffffff81667303>] panic+0xba/0x1c9
[   18.690187]  [<ffffffff810579ae>] do_exit+0x81e/0x8e0
[   18.690193]  [<ffffffff81057d87>] sys_exit+0x17/0x20
[   18.690199]  [<ffffffff8167c8e9>] system_call_fastpath+0x16/0x1b
[   18.690211] panic occurred, switching back to text console
```

...then it just never progresses from there.

---

### Post by kyleabaker on 2012-07-23
I just tried installing via the latest daily build and am getting a kernel panic around the time the Network Manager is loading, so I can't even really attempt to install 12.10 alpha.

System specs:
AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ × 2
MB ASUS M2N4-SLI NF4 SLI AM2
WIRELESS LAN PCI CARD ZEW1600 RTL

Does anyone know if this issue is known by the kernel developers or if its filed anywhere?

---

### Post by ronacc on 2012-07-23
> **kyleabaker said:**
> I just tried installing via the latest daily build and am getting a kernel panic around the time the Network Manager is loading, so I can't even really attempt to install 12.10 alpha.

System specs:
AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ × 2
MB ASUS M2N4-SLI NF4 SLI AM2
WIRELESS LAN PCI CARD ZEW1600 RTL

Does anyone know if this issue is known by the kernel developers or if its filed anywhere?

I have filed a couple of bugs on it when I could actually get apport to run and report something , but go ahead and file your own . The response my bugs have gotten so far seem to be disbelief , the more people that file bugs the better the chance that they will take it seriously .

---

### Post by Gyokuro on 2012-07-23
QQ-Current runs fine here but this was expected due to Intel hardware (CPU, NIC, GPU) - maybe you connect your pc via a serial console to check where it goes boom. Try also nomodeset

---

### Post by kyleabaker on 2012-07-23
> **ronacc said:**
> I have filed a couple of bugs on it when I could actually get apport to run and report something , but go ahead and file your own . The response my bugs have gotten so far seem to be disbelief , the more people that file bugs the better the chance that they will take it seriously .

I googled to see if others were experiencing any similar issues and found the following. Add your comments if you feel like yours is the same so we can get some attention on this and get it fixed asap! :D

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1027322](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1027322)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1021086](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1021086)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1019674](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1019674)

---

### Post by lehjr on 2012-07-23
Here's one for the bug list: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1022351](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1022351)

Thing is, it looks like kernel 3.5 already got finalized upstream :confused:

---

### Post by dino99 on 2012-07-23
maybe you hit the same issue i get on my desktop, resulting in kernel panic. Could you glance at ureadahead log on your system ? and post your comments in case, on this report ?

[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/969926](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/969926)

---

### Post by kyleabaker on 2012-07-23
> **lehjr said:**
> Here's one for the bug list: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1022351](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1022351)

Thing is, it looks like kernel 3.5 already got finalized upstream :confused:

My wireless card is Ralink. When I get home I'll try pulling the card and booting kernel 3.5. If that resolves the issue then at least I'll be a step closer than before. That won't help the fact that I ONLY have wireless access at home and won't be able to use it. :P

---

### Post by kyleabaker on 2012-07-23
> **dino99 said:**
> maybe you hit the same issue i get on my desktop, resulting in kernel panic. Could you glance at ureadahead log on your system ? and post your comments in case, on this report ?

[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/969926](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/969926)

The kernel 3.5 issues that I'm seeing don't appear to be related to the ones in that report.

---

### Post by lehjr on 2012-07-23
> **kyleabaker said:**
> My wireless card is Ralink. When I get home I'll try pulling the card and booting kernel 3.5. If that resolves the issue then at least I'll be a step closer than before. That won't help the fact that I ONLY have wireless access at home and won't be able to use it. :P

To add insult to injury, see comment 10 and 12 for the upstream report results: [https://bugzilla.kernel.org/show_bug.cgi?id=44411](https://bugzilla.kernel.org/show_bug.cgi?id=44411)

---

### Post by lehjr on 2012-07-23
> **dino99 said:**
> maybe you hit the same issue i get on my desktop, resulting in kernel panic. Could you glance at ureadahead log on your system ? and post your comments in case, on this report ?

[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/969926](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/969926)

Although I do actually have that same log entry in the Quantal daily build as of yesterday, I don't have an actual kernel panic, at least not in those terms. The bug I have is related to the wireless drivers as the issue goes away without the device present.

Quantal does have quite a few bugs right now, hopefully they will get fixed before the actual release. However, looking at the results of the my last bug report and others before it, I'm not feeling very confident about it right now.

---

### Post by kyleabaker on 2012-07-23
> **lehjr said:**
> To add insult to injury, see comment 10 and 12 for the upstream report results: [https://bugzilla.kernel.org/show_bug.cgi?id=44411](https://bugzilla.kernel.org/show_bug.cgi?id=44411)

Wow, that's very unsettling. Will a backport be ready for Ubuntu 12.10 to be released with? Cause I can't even get the ***_installer_*** to boot with that kernel.

I as well as anyone else with this issue with have no way of even installing with a non-patched kernel, let alone upgrading the kernel *after* installing.

---

### Post by lehjr on 2012-07-23
> **kyleabaker said:**
> Wow, that's very unsettling. Will a backport be ready for Ubuntu 12.10 to be released with? Cause I can't even get the ***_installer_*** to boot with that kernel.

I as well as anyone else with this issue with have no way of even installing with a non-patched kernel, let alone upgrading the kernel *after* installing.

Yes, but it's that comment # 12 that gets me, pretty much insisting that the reason distros exist is for fixing known, but ignored, kernel bugs. I don't think I've seen a distro-specific patch in years. I think the last time I even compiled a kernel from source, aside for an OpenWRT build, was back when Mandrake had barely diverged from Red Hat's base.

---

### Post by ronacc on 2012-07-23
in my case at least  I doubt it is wireless related  . my wireless card is a realtek 8185 and if I get to the login screen and then do not log in but ctrl>alt>f1  to a console I can update my sys , install things etc stably . From the various posts in this and other threads I think there is more than 1 serious bug with the 3.5 series kernel and that Ubuntu had better consider reverting to the 3.4 series for this release .

---

### Post by lehjr on 2012-07-23
> **ronacc said:**
> in my case at least  I doubt it is wireless related  . my wireless card is a realtek 8185 and if I get to the login screen and then do not log in but ctrl>alt>f1  to a console I can update my sys , install things etc stably . From the various posts in this and other threads I think there is more than 1 serious bug with the 3.5 series kernel and that Ubuntu had better consider reverting to the 3.4 series for this release .

From my understanding , the wireless issue isn't limited to the RaLink devices, but rather has more to do with "single-queue drivers" as per the patch description.

I'm wondering if reverting will have any affect on Wayland making it into the final release. I come across some info that Wayland has a dependency on "systemd" and that there is some effort required to make it work with upstart.

---

