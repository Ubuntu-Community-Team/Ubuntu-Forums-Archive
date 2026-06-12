---
title: "Kenel 3.4-rc* is here..."
date: 2012-04-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by zika on 2012-04-01
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-rc1-precise/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.4-rc1-precise/")

---

### Post by bmbaker on 2012-04-01
just tried it out and it wouldn't compile the nvidia-current!
I am using the nvidia-current 295.33 !
though i did finally manage to install the 3.3 kernel after i copiled it from source using the instruction here
[http://verahill.blogspot.de/2012/03/kernel-33-on-debian-testing.html](http://verahill.blogspot.de/2012/03/kernel-33-on-debian-testing.html)

---

### Post by Doug S on 2012-04-01
I have been following a particular kernel bug, and I have been trying the various 3.3RC kernels, and now the 3.4RC1 kernel (as a side note 3.4RC1 has the fix I have been waiting for).
 
For all my 3.3RCX and 3.4RC1 tests, my locally connected video display does not work and I have to SSH into the computer to do my test. My display has always worked fine before and still does with 12.04 (Kernel 3.2.0.21). My computer is very old and runs server edition. I am just mentioning it, and I really haven't looked into it yet.

---

### Post by matt_symes on 2012-04-01
```
matthew@matthew-Aspire-7540:~$ uname -a
Linux matthew-Aspire-7540 3.4.0-030400rc1-generic #201203312035 SMP Sun Apr 1 00:36:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
matthew@matthew-Aspire-7540:~$
```

Using radeon. 

Will let you know what i think.

---

### Post by VinDSL on 2012-04-01
Oh, drat!  Kernel panic, for me...

Heh!  Things were going too smoothly, anyway.  :lolflag:

---

### Post by zika on 2012-04-02
At my place there are two issues:

1. Grub timeout (there is a thread (of mine) about that...)
2. shutdown doesn't work as it is supposed... It works up to &#8222;will halt&#8220; and then all I get is flashing CL and SL on keyboard... ;)

---

### Post by matt_symes on 2012-04-02
I'm getting a kernel panic when using the wireless connection. Wired is fine though.

Suspend is causing the laptop to shutdown. 

I am currently back in 3.2.0.21 as i need to do things today.

---

### Post by VinDSL on 2012-04-17
Just upgraded from 3.4rc2 -> 3.4rc3...  working fine!

Working so good, in fact, I purged all other kernels (except Liquorix)  ;)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-rc3-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-rc3-precise/)

---

### Post by ft_ on 2012-04-17
Can I install this kernel along with the fglrx driver (from the Ubuntu repos) ?
I never succeeded. (And I do not want the radeon driver because the power usage is much too high...)

---

### Post by VinDSL on 2012-04-18
> **ft_ said:**
> Can I install this kernel along with the fglrx driver (from the Ubuntu repos)?
[LIST]
[*]Toe bone's connected to the foot bone.
[*]Foot bone's connected to the leg bone.
[*]Leg bone's connected to the knee bone.
[*]et cetera, et cetera, et cetera...
[/LIST]

In order to install Linux 3.4-rc*, I first had to upgrade my xorg server to version 1.12.0

The xorg 1.12.0 server requires that you upgrade ALL of your video drivers, so they're 1.12 compliant.

I did all of this using the "unstable, bleeding edge" xorg-edgers fresh X crack PPA.

LINKAGE:  [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

Although I'm running an nVidia card, they do have a fglrx-installer available in their PPA.

Soooo, yes, fglrx drivers are available, but no, you cannot use the official Ubu repos, e.g. you cannot mix n' match.  

You must install the edgers package, as a whole, or you'll run into dependency issues.  ;)

---

### Post by Miykel on 2012-04-18
G'Day;  I'm intrigued with the threads I read concerning kernels, is this the kernel which belongs to Ubuntu 12.04 or is it some other deal ??.
 Kind Regards Miykel

---

### Post by jefsview on 2012-04-18
> **Miykel said:**
> G'Day;  I'm intrigued with the threads I read concerning kernels, is this the kernel which belongs to Ubuntu 12.04 or is it some other deal ??.
 Kind Regards Miykel

This is the main kernel that all others are tweaked from. Ubuntu 12.04 uses the 3.2.0 kernel, but tweaks and backports code from newer kernels to optimize performance for Ubuntu-based systems.

-- jeff

---

### Post by Miykel on 2012-04-18
So I can install it on Ubuntu 12.04 LTS or is it more complicated than that ?, why I ask is I'd like to investigate Linux more, learn more about what can be done with it from a practical view point as apposed to just reading books, which, in themselves are important, but it's the application that interests me.
Regards Miykel

---

### Post by VinDSL on 2012-04-18
> **jefsview said:**
> This is the main kernel that all others are tweaked from.
That's as good an answer, as any.  ;)

The way I look at it is...

Linux is just the kernel.  That's it.  Linux=Kernel

Linux distributions (and there are a zillion of them) are simply Linux plus GNU Project software.  Linux+Software= GNU/Linux Distro

My favorite Linux is Liquorix, but it's still just a kernel.  Ubu distros run fine, on top of Liquorix (when the compilers are compatible).

Ubu mainline kernels are a compromise, of sorts, for me.  I *feel* like I should test Ubu on something that has a fighting chance of becoming part of the official distribution.  Wouldn't do much good, if I was testing Precise on Liquorix, eh what (unless I started my own distro)?

So, I always run the latest Ubu dev release, on the latest mainline kernel.

Probably some sort of psychological defect.  I can't stand it, when things just work!  :)

---

### Post by VinDSL on 2012-04-18
> **Miykel said:**
> So I can install it on Ubuntu 12.04 LTS or is it more complicated than that?
Yes n' yes!

You can install it on Ubu 12.04... that's what I'm running.

And, yes, it's a little more complicated than that!

Linux 3.3 was very tricky.  Linux 3.4 was tricky too, but in a different way.  There are several +1 threads discussing how to do this.

Anyway, it's lots of fun, if you enjoying pulling out your own hair!  Really gets the neurons firing... :D

Sort of anti-climatic, when you get it working, but there's always another one waiting for you, in the wings, when Sunday night rolls around (these days).

---

### Post by Miykel on 2012-04-19
Thanks for the replies guys; I'll have to do some digging, now I have a rough idea what I'm looking for, and see if this old brain of mine can learn yet another new trick LOL. If you hear any blood curdling screams coming from "down under" you'll know what it is.
Regards Miykel  ):P

---

### Post by Miykel on 2012-04-19
G'Day VinDSL; I went to the site you posted;


[http://kernel.ubuntu.com/~kernel-ppa...4-rc3-precise/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.4-rc3-precise/")

  I wonder if you would have the time to explain what to do with what i found there or maybe you know of a site where I could go to learn about what to do.

Kind Regards Miykel

---

### Post by zika on 2012-04-19
> **Miykel said:**
> G'Day VinDSL; I went to the site you posted;


[http://kernel.ubuntu.com/~kernel-ppa...4-rc3-precise/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.4-rc3-precise/")

  I wonder if you would have the time to explain what to do with what i found there or maybe you know of a site where I could go to learn about what to do.

Kind Regards Miykel
From any folder within that site You can install kernel by:
1. choosing architecture (64 bit or 32bit (pae or non-pae))
2. grab 3 files: two (image&headers) for Your chosen architecture and one marked &#8222;all&#8220;...
3. put them in one folder on Your machine
4. **sudo dpkg -i linux*.deb** in that folder (assuming only these 3 are .deb with name starting with &#8222;linux&#8220;)...
5. You're done. On next boot You will be able to choose that kernel...
6. Enjoy!

Example:
```
cd /tmp
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2012-04-19-precise/linux-headers-3.4.0-999-generic_3.4.0-999.201204190406_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2012-04-19-precise/linux-headers-3.4.0-999_3.4.0-999.201204190406_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2012-04-19-precise/linux-image-3.4.0-999-generic_3.4.0-999.201204190406_amd64.deb
sudo dpkg -i /tmp/linux*.deb
```

---

### Post by Miykel on 2012-04-19
thanks zika for the help, so damn simple when you know how, it's the know how thats hard :confused:, trouble is it doesn't like nVidea drivers, the resolution was terrible, blast !!, would the command 

sudo apt-get --purge remove 

remove it ?? then update grub ???

Also, I tried to run this code

[I]cat /boot/config-`uname -r`>.config

earlier but it's not recognized, could someone help with that please

Regards Miykel
[/I]

---

### Post by zika on 2012-04-19
> **Miykel said:**
> thanks zika for the help, so damn simple when you know how, it's the know how thats hard :confused:, trouble is it doesn't like nVidea drivers, the resolution was terrible, blast !!, would the command 

sudo apt-get --purge remove 

remove it ?? then update grub ???

Also, I tried to run this code

[I]cat /boot/config-`uname -r`>.config

earlier but it's not recognized, could someone help with that please

Regards Miykel
[/I]You do not need to remove it to get to Your machine again. Just choose old kernel (You used before) on boot in Grub...
To remove it find names (In my example these were: linux-headers-3.4.0-999-generic linux-headers-3.4.0-999 linux-image-3.4.0-999-generic) and remove them:```
sudo apt-get purge linux-headers-3.4.0-999-generic linux-headers-3.4.0-999 linux-image-3.4.0-999-generic
```...
I'm ATI user so I'm not good with NVidia stuff...

---

### Post by VinDSL on 2012-04-19
> **Miykel said:**
> [...] trouble is it doesn't like nVidea drivers, the resolution was terrible, blast !!

earlier but it's not recognized, could someone help with that please
AFAIK, Linux 3.4 requires xorg server 1.12.0

The first thing I did was upgrade to xorg server 1.12.0, and nVidia 295.40, from the edgers PPA... then, I installed the Linux 3.4 mainline kernel (in that order).

You're probably running xorg server 1.11 and stale nVidia drivers...  ;)

---

### Post by Miykel on 2012-04-19
Thanks so much again guys, I ended up removing the kernel with synaptic, seemed the safest way, will see about upgrading xorg server then try again.
Regards Miykel

---

### Post by xebian on 2012-04-19
Using 3.4.0-rc3 here with NVidia 295.40 and  stock
 xserver-xorg-core                      2:1.11.4-0ubuntu10

---

### Post by VinDSL on 2012-04-19
> **xebian said:**
> Using 3.4.0-rc3 here with NVidia 295.40 and  stock
 xserver-xorg-core                      2:1.11.4-0ubuntu10
Are you compiling from source, or using the pre-built binaries?!?!?

---

### Post by xebian on 2012-04-19
> **VinDSL said:**
> Are you compiling from source, or using the pre-built binaries?!?!?

Yes I compile my kernel and 295.40 from Nvidia.

---

### Post by paul_in_london on 2012-04-22
3.4-rc4 is here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-rc4-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-rc4-precise/)

Just installed it. No issues with nvidia-current [COLOR="Red"]**295.40-0ubuntu1+xedgers~precise1**[/COLOR]. :)

---

### Post by Miykel on 2012-04-22
G'Day ; Finally got the xorg server to upgrade to 1.12.1 so tried to install new kernel 3.4-rc 3 and 4 but they will not boot, just get the red screen but not the login screen ??? always something,
  Used the .deb packages
Any help would be great.
Regards Miykel

---

### Post by fooman on 2012-04-22
by red screen,  do you mean a purple-ish screen?  when you get there,  try dropping to a shell terminal by pressing ctrl-alt-f1

if that gets you to a shell,  log in and try purging the nvidia drivers and reinstalling them.


```
sudo apt-get --purge remove nvidia-*

sudo apt-get install nvidia-current

sudo reboot
```see if that helps

---

### Post by Miykel on 2012-04-22
Thanks for the reply Fooman, yes thats the screen, it only happens with any of the 3.4 ** kernels, if I go back to the 3.2.2 kernel it boots fine.
Regards Miykel

---

### Post by pqwoerituytrueiwoq on 2012-04-22
> **Miykel said:**
> Thanks for the reply Fooman, yes thats the screen, it only happens with any of the 3.4 ** kernels, if I go back to the 3.2.2 kernel it boots fine.
Regards Miykel
do you get a login screen if you use gdm instead of lightdm?
that description sounds like something i encountered but i was changing a lot of packages so it could be something else entirely
edit i still have kernel 3.2 so what i posted is probably pointless

---

### Post by VinDSL on 2012-04-23
> **paul_in_london said:**
> 3.4-rc4 is here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-rc4-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-rc4-precise/)

Just installed it. No issues with nvidia-current [COLOR="Red"]**295.40-0ubuntu1+xedgers~precise1**[/COLOR]. :)
Thanks!  I forgot it was Sunday...  :)

Surprisingly, my sound system is much louder, and cleaner now!

Never noticed that before, after upgrading the kernel.  Hrm...

---

### Post by VinDSL on 2012-04-23
> **Miykel said:**
> G'Day ; Finally got the xorg server to upgrade to 1.12.1 so tried to install new kernel 3.4-rc 3 and 4 but they will not boot, just get the red screen but not the login screen ??? always something,
  Used the .deb packages
Any help would be great.
Regards Miykel
Assuming you're running nVidia...

Are you using nvidia-current **[COLOR="Red"]295.40-0ubuntu1+xedgers~precise1[/COLOR]**, from the edgers PPA?

---

### Post by Miykel on 2012-04-23
Thanks Guys, yes I'm running nVidia 295.4 which were installed when I got the update xorg server to 1.12.1, when I boot it just goes to the redish screen, where you normally get the Ubuntu with the dots underneath it, just before the login screen, and it just sits there.
 Went to  /usr/src and there was only the generic and the new kernel there ??? all very strange.
Regards Miykel

---

### Post by Mathor on 2012-04-23
I've been lucky with this kernel, as 3.4 hasn't given me a single panic and is very stable for me, thanks to following VinDSL's advice and adding the edgers ppa. I added the ppa and then simply updated and upgraded in Synaptic, and purged the old kernel.

EDIT: also, I've had similar success as VINDSL With my soundsystem. Most of the time, the sound will be basically muted until it gets to about 30-40 percent, but now it registers at 10-20-30 percent like it's supposed to work. I'm impressed!

---

### Post by VinDSL on 2012-04-23
> **Mathor said:**
> [...]I've had similar success as VINDSL With my soundsystem. Most of the time, the sound will be basically muted until it gets to about 30-40 percent, but now it registers at 10-20-30 percent like it's supposed to work. I'm impressed!
Aha!  It's not our imagination, e.g. we aren't (ahem) hearing things...  :D

SOURCE: [https://lkml.org/lkml/2012/4/20/105](https://lkml.org/lkml/2012/4/20/105)

> Date	Fri, 20 Apr 2012 12:04:30 +0200
From	Takashi Iwai <>
Subject	**[COLOR="DarkRed"][GIT PULL] sound fixes for 3.4-rc4[/COLOR]**

Hi Linus,

The following changes since commit 7d7eb9ea314e992413620610b4d09c9cd5fa8959:

  ALSA: hda/realtek - Fix mem leak (and rid us of trailing whitespace). (2012-04-13 07:35:57 +0200)

are available in the git repository at:

  git://git.kernel.org/pub/scm/linux/kernel/git/tiwai/sound.git tags/sound-3.4

for you to fetch changes up to c817eebec5971febab86d397582954bd52f403a8:

  Merge branch 'fix/cxt-stable' into fix/hda (2012-04-19 17:13:03 +0200)

----------------------------------------------------------------
sound fixes for 3.4-rc4

Fixes for a few regressions of HD-audio, originated partly from 3.4
and partly 3.3.
The fixes for ThinkPad docking-station are for 3.3 kernels, thus they
are based on 3.3 then merged back to 3.4, so that they can be merged
to stable tree cleanly.  The non-trivial merge conflicts are because
of this action.

In addition, a copule of trivial fixes for documentation and a long-
statnding issue in the listing of built-in sound driver at boot time.

----------------------------------------------------------------
Kuninori Morimoto (1):
      ALSA: workaround: change the timing of alsa_sound_last_init()
Randy Dunlap (1):
      ALSA: fix core/vmaster.c kernel-doc warning

Takashi Iwai (5):
      ALSA: hda/realtek - Fix regression on Quanta/Gericom KN1
      ALSA: hda/sigmatel - Fix inverted mute LED
      ALSA: hda/conexant - Don't set HP pin-control bit unconditionally
      ALSA: hda/conexant - Set up the missing docking-station pins
      Merge branch 'fix/cxt-stable' into fix/hda

 sound/core/vmaster.c           |    1 +
 sound/last.c                   |    2 +-
 sound/pci/hda/patch_conexant.c |   35 ++++++++++++++++++++++++----
 sound/pci/hda/patch_realtek.c  |   49 ++++++++++++++++++++++++++++++++++++----
 sound/pci/hda/patch_sigmatel.c |    5 ++--
 5 files changed, 79 insertions(+), 13 deletions(-)


---

### Post by vikrant82 on 2012-04-25
Is anyone else noticing a slower wifi connect speed compared to 3.2.XX ?

Normally I connect at 65mbps on 3.2 but on 3.4 I am connecting at 19-25 mbps.  Occasionally connection would drop to 5mbps or so.

On:

> 
03:00.0 Network controller: Intel Corporation Centrino Wireless-N + WiMAX 6150 (rev 67)
        Subsystem: Intel Corporation Centrino Wireless-N + WiMAX 6150 BGN
        Flags: bus master, fast devsel, latency 0, IRQ 48
        Memory at f5600000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: iwlwifi
        Kernel modules: iwlwifi


---

### Post by VinDSL on 2012-04-25
> **vikrant82 said:**
> Is anyone else noticing a slower wifi connect speed compared to 3.2.XX ?
I'm running a wired connection right now, so no, I haven't noticed any slowness, but...

Network-Manager gave me fits on Linux 3.2/3.3. I had to switch to Wicd for a couple of months, just to get a web connection.

Anyway, if you're running NM, you might want to give Wicd a whirl, and see if things improve.

BTW, sorry for being rudimentary, but if you switch interfaces, make sure to download (only) the Wicd package, before purging NM.

You won't be able to install Wicd, unless you have a local copy, because you won't have a web connection, in between purging NM and installing Wicd, e.g. you can't have two network managers installed at the same time.

Don't wanna get you in the jackpot, following my advice, you know?  ;)

---

