---
title: "Install Failed Until Nvidia Purged &amp; Reinstalled"
date: 2011-12-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by drs305 on 2011-12-01
Just tried installing Precise for the first time today, using Alpha 1. I have an nvidia gs7600 card.

Installation went fine but on reboot the system repeatedly hung without booting to the Desktop. The 'nomodeset' option did not help.

Updating the packages from the recovery mode terminal didn't work either, nor did trying to start lightdm after a terminal log in.

What finally allowed booting to the Desktop was removing all nvidia packages and then reinstalling *nvidia-current* (which also installed nvidia-settings).
```

sudo apt-get purge nvidia*
sudo apt-get install nvidia-current
```

---

### Post by ventrical on 2011-12-01
I just had one glitch  with Broadcom wireless driver.

sudo apt-get install firmware-b43-installer

fixed it just fine.

---

### Post by effenberg0x0 on 2011-12-01
Nvidia-proprietary 290.10 install survived the ton of updates normally. But, then again, I already had been using PP and updating daily, so there was no kernel update / need to rebuild kernel module.

---

### Post by ventrical on 2011-12-01
> **drs305 said:**
> Just tried installing Precise for the first time today, using Alpha 1. I have an nvidia gs7600 card.

Installation went fine but on reboot the system repeatedly hung without booting to the Desktop. The 'nomodeset' option did not help.

Updating the packages from the recovery mode terminal didn't work either, nor did trying to start lightdm after a terminal log in.

What finally allowed booting to the Desktop was removing all nvidia packages and then reinstalling *nvidia-current* (which also installed nvidia-settings).
```

sudo apt-get purge nvidia*
sudo apt-get install nvidia-current
```

I hope you don't mind but I  inserted your solution, here: [http://ubuntuforums.org/showpost.php?p=11505338&postcount=50](http://ubuntuforums.org/showpost.php?p=11505338&postcount=50)

---

### Post by drs305 on 2011-12-01
> **ventrical said:**
> I hope you don't mind but I  inserted your solution, here: [http://ubuntuforums.org/showpost.php?p=11505338&postcount=50](http://ubuntuforums.org/showpost.php?p=11505338&postcount=50)

Don't mind at all. In fact, that's a nice thread you started. 

I was going to wait a bit (and take a breather) before starting on Precise, but I just went blindly ahead and installed it this afternoon. I haven't even read any of the threads in U+1 until seeing your link above.  ;-)

---

### Post by mc4man on 2011-12-02
Haven't checked because I never allow the installer Internet access but the installer was known to use the wrong nvidia drivers, as in using the 173.X when it should have used nvidia-current

May of happened here?

---

### Post by 3vi1 on 2011-12-02
I have the same problem (wont start DM) in my system with a 560GTX (my non-nvidia systems work fine) ever since the 3.2 kernels hit, but purging/re-installing the nvidia packages hasn't helped.

Booting pre-3.2 kernels works fine though.

I'll probably try newer nvidia drivers from edgers tonight or tomorrow.  To see if that offers any relief.

---

### Post by 3vi1 on 2011-12-03
...Nope.  Even updating to all the packages in Xorg-edgers didn't fix the issue.

I decided to bite the bullet and do a clean install.... and have the same problem.  :\  Nouveau works with the 3.2 kernel and my GTX560 Ti, but the nvidia (285 and 290) drivers do not.

---

### Post by paul_in_london on 2011-12-03
> **3vi1 said:**
> I have the same problem (wont start DM) in my system with a 560GTX (my non-nvidia systems work fine) ever since the 3.2 kernels hit, but purging/re-installing the nvidia packages hasn't helped.

Booting pre-3.2 kernels works fine though.

I'll probably try newer nvidia drivers from edgers tonight or tomorrow.  To see if that offers any relief.

That's strange. The 3.2 kernels have been booting fine for me with nvidia-current 290.10 from xorg-edgers.

```
paul@precise-64:~$ uname -a
Linux precise-64 3.2.0-030200rc4-generic #201112012035 SMP Fri Dec 2 01:36:30 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
paul@precise-64:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 290.10-0ubuntu1~xedgers~precise1
  Candidate: 290.10-0ubuntu1~xedgers~precise1
  Version table:
 *** 290.10-0ubuntu1~xedgers~precise1 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
     285.05.09-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
```

One difference from your situation is that this PP install was upgraded from 11.10 when the PP repos opened.

So you can't get to the desktop at all with a 3.2 kernel?

---

### Post by 3vi1 on 2011-12-03
> **paul_in_london said:**
> So you can't get to the desktop at all with a 3.2 kernel?

I can, if I uninstall nvidia-current (or nvidia-current-updates, as I've also tested) and fall back to the nouveau driver (losing Unity3D in the process).

I just now downloaded the 290 installer directly from nVidia... but I don't have many expectations that it will work, given that the edgers 290 package did not.

I could not find anyone with exactly the same issue reported in the launchpad bug-tracker...  so I'll probably break it again with the standard nvidia-current packages one more time before I try installing 290 so that I can collect the relevant info for a useful bug report.

---

### Post by 3vi1 on 2011-12-03
> **paul_in_london said:**
> 
One difference from your situation is that this PP install was upgraded from 11.10 when the PP repos opened.


Not really a difference - I hopped did the same thing - hopped on the PP repos the day they were opened and upgraded my 11.10.  It's been fine until the 3.2 kernels hit. (fine, except for how broken all the multi-arch stuff is right now).

[EDIT:  Doh, I see from your uname string that it's obvious that you are running 64-bit too, so removed my question]

---

### Post by kuvanito on 2011-12-03
drs305 BIG THANK YOU!
i was having prob with an hp pavilion desktop with AMD and Nvidia,i have a thread here about it but thanks to you i no longer have a prob.
took hd out and shoveled it in to my intel machine,run your commands and shoveled back to the AMD machine and BOOM! it runs,it runs,it runs,couldn't b happier :):):)

---

### Post by paul_in_london on 2011-12-03
> **3vi1 said:**
> Not really a difference - I hopped did the same thing - hopped on the PP repos the day they were opened and upgraded my 11.10.  It's been fine until the 3.2 kernels hit. (fine, except for how broken all the multi-arch stuff is right now).

[EDIT:  Doh, I see from your uname string that it's obvious that you are running 64-bit too, so removed my question]

Sorry, I was thinking of the bit where you mentioned doing a clean install. I'm on 64 bit yes. Have you tried reinstalling your 3.2 kernel (with nvidia-current 290.10 already installed)?

Does 3.2-rc4 from ppa kernel mainline work?

What if you purge xorg-edgers? Can you boot 3.2 normally then?

FWIW, I remember purging various ":386" packages a while back. Not sure if that's relevant to your problem though. I've used Nvidia's installer in the past, but I prefer to stick to packaged debs.

---

### Post by 3vi1 on 2011-12-03
> **paul_in_london said:**
> Have you tried reinstalling your 3.2 kernel (with nvidia-current 290.10 already installed)?

No.  Might be worth a shot though.

> **paul_in_london said:**
> 
Does 3.2-rc4 from ppa kernel mainline work?


I wasn't aware there was a ppa for newer versions.  Sounds like it's worth testing too.

> **paul_in_london said:**
> 
What if you purge xorg-edgers? Can you boot 3.2 normally then?


No.  I tried purging it when it didn't help, but I consistently could not boot 3.2+nvidia-current before, during, or after trying edgers.

> **paul_in_london said:**
> 
FWIW, I remember purging various ":386" packages a while back. Not sure if that's relevant to your problem though. I've used Nvidia's installer in the past, but I prefer to stick to packaged debs.


Probably not, since I've now done a complete clean install and tried using nvidia-current before installing any non-default multiarch packages.  I actually need the mutiarch stuff, because I run Wine1.3 (for L4D2) on this.  Now, I can't even reinstall multiarch because of the current state of the repos.

```

evil@saturn:~$ sudo apt-get install ia32-libs-multiarch
[sudo] password for evil: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ia32-libs-multiarch:i386 : Depends: gstreamer0.10-plugins-base:i386 but it is not going to be installed
                            Depends: gstreamer0.10-plugins-good:i386 but it is not going to be installed
                            Depends: gstreamer0.10-fluendo-mp3:i386 but it is not going to be installed
                            Depends: ibus-gtk:i386 but it is not going to be installed
                            Depends: libcanberra-gtk-module:i386 but it is not going to be installed
                            Depends: libcap2:i386 but it is not going to be installed
                            Depends: libgphoto2-2:i386 but it is not going to be installed
                            Depends: libgphoto2-port0:i386 but it is not going to be installed
                            Depends: libqtwebkit4:i386 but it is not going to be installed
                            Depends: libsane:i386 but it is not going to be installed
                            Depends: libsdl-mixer1.2:i386 but it is not going to be installed
                            Depends: libpam-winbind:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by paul_in_london on 2011-12-03
> **3vi1 said:**
> I wasn't aware there was a ppa for newer versions.  Sounds like it's worth testing too.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc4-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc4-oneiric/)

Download and install the two amd64 debs plus the _all.deb :)


> **3vi1 said:**
> No.  I tried purging it when it didn't help, but I consistently could not boot 3.2+nvidia-current before, during, or after trying edgers.

Stranger still.


> **3vi1 said:**
> Probably not, since I've now done a complete clean install and tried using nvidia-current before installing any non-default multiarch packages.  I actually need the mutiarch stuff, because I run Wine1.3 (for L4D2) on this.  Now, I can't even reinstall multiarch because of the current state of the repos.

```

evil@saturn:~$ sudo apt-get install ia32-libs-multiarch
[sudo] password for evil: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ia32-libs-multiarch:i386 : Depends: gstreamer0.10-plugins-base:i386 but it is not going to be installed
                            Depends: gstreamer0.10-plugins-good:i386 but it is not going to be installed
                            Depends: gstreamer0.10-fluendo-mp3:i386 but it is not going to be installed
                            Depends: ibus-gtk:i386 but it is not going to be installed
                            Depends: libcanberra-gtk-module:i386 but it is not going to be installed
                            Depends: libcap2:i386 but it is not going to be installed
                            Depends: libgphoto2-2:i386 but it is not going to be installed
                            Depends: libgphoto2-port0:i386 but it is not going to be installed
                            Depends: libqtwebkit4:i386 but it is not going to be installed
                            Depends: libsane:i386 but it is not going to be installed
                            Depends: libsdl-mixer1.2:i386 but it is not going to be installed
                            Depends: libpam-winbind:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

I don't have **ia32-libs-multiarch:i386** installed.

```
paul@precise-64:~$ apt-cache policy ia32-libs-multiarch:i386
ia32-libs-multiarch:i386:
  Installed: (none)
  Candidate: 20090808ubuntu31
  Version table:
     20090808ubuntu31 0
```

I'd recommend using **aptitude** instead of **apt-get** by the way. Try purging **ia32-libs-multiarch:i386** (tempoarily) and try to update using **aptitude**:

```
sudo aptitude purge ia32-libs-multiarch:i386
sudo aptitude update
sudo aptitude safe-upgrade
```

HTH

---

### Post by 3vi1 on 2011-12-03
```

[     6.002] (II) NVIDIA(0): Creating default Display subsection in Screen section
[     6.002] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[     6.002] (==) NVIDIA(0): RGB weight 888
[     6.002] (==) NVIDIA(0): Default visual is TrueColor
[     6.002] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     6.002] (**) NVIDIA(0): Option "NoLogo" "True"
[    14.524] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:5:0:0.  Please
[    14.524] (EE) NVIDIA(0):     check your system's kernel log for additional error
[    14.524] (EE) NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
[    14.524] (EE) NVIDIA(0):     README for additional information.
[    14.524] (EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!

```

Looking at the kernel log... this seems to be caused by:

```

Dec  3 12:22:51 saturn kernel: [    4.953412] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  285.05.09  Fri Sep 23 17:31:57 PDT 2011
Dec  3 12:23:01 saturn kernel: [   14.799931] NVRM: RmInitAdapter failed! (0x27:0x38:1193)
Dec  3 12:23:01 saturn kernel: [   14.799939] NVRM: rm_init_adapter(0) failed

```

Did some searches and it looks like this may be a nVidia driver bug that's affecting only nVidia cards with large amounts of RAM - and only at specific versions of 3.1 and later kernels.  If it is that bug, it's been fixed by the developers, but they haven't released a beta that has the fix.  :\

---

### Post by 3vi1 on 2011-12-03
Well I'll be damned...

Since I thought your rc4 kernel suggestion was a good one, I went ahead just now and gave it a shot - even though I had pretty much convinced myself it was a problem that would have to be corrected in the driver.

AND IT WORKED!  It looks like whatever they have been doing in the 'official' 3.2 kernels that makes it fail in combination with my hardware is not present in that ppa kernel.  I hope this is because of a fix, and not build options... so that future 'official' kernels work as well.  I had already tried the 3.2.0-3 kernel... though the meta packages are not yet dependent on it... and it does not work.  :(

So, thanks for the suggestion!  At least I've got a version of 3.2 that works for now.

On a side note, I noticed this kernel fixes another issue that I had noticed but not started pursuing:  My Marvell USB3 card did not seem to work with the 'official' precise 3.2 kernels either - but it works fine on rc4.  So, thanks again!

---

### Post by paul_in_london on 2011-12-03
> **3vi1 said:**
> I can, if I uninstall nvidia-current (or nvidia-current-updates, as I've also tested) and fall back to the nouveau driver (losing Unity3D in the process).

I just now downloaded the 290 installer directly from nVidia... but I don't have many expectations that it will work, given that the edgers 290 package did not.

I could not find anyone with exactly the same issue reported in the launchpad bug-tracker...  so I'll probably break it again with the standard nvidia-current packages one more time before I try installing 290 so that I can collect the relevant info for a useful bug report.

Ah ok. Sorry to hear that, but at least a fix is apparently in the pipeline! :)

This box has:

```
paul@precise-64:~$ lspci -v | grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation NV41GL [Quadro FX 1400] (rev a2) (prog-if 00 [VGA controller])
        Subsystem: nVidia Corporation Device 0243
        Kernel driver in use: nvidia
        Kernel modules: nvidia_current, nouveau, nvidiafb
paul@precise-64:~$
```

which has 128MB RAM I think.

I have another (broken) box with an Nvidia 8800GT card. That card has 512MB RAM as far as I remember so I wonder if that would work at the moment. Really should get it fixed. Thought the PSU had gone (which it may well have done), but when I put in a new PSU it was still dead. Hardware isn't my forte I'm afraid.

---

### Post by paul_in_london on 2011-12-03
> **3vi1 said:**
> Well I'll be damned...

Since I thought your rc4 kernel suggestion was a good one, I went ahead just now and gave it a shot - even though I had pretty much convinced myself it was a problem that would have to be corrected in the driver.

AND IT WORKED!  It looks like whatever they have been doing in the 'official' 3.2 kernels that makes it fail in combination with my hardware is not present in that ppa kernel.  I hope this is because of a fix, and not build options... so that future 'official' kernels work as well.  I had already tried the 3.2.0-3 kernel... though the meta packages are not yet dependent on it... and it does not work.  :(

So, thanks for the suggestion!  At least I've got a version of 3.2 that works for now.

On a side note, I noticed this kernel fixes another issue that I had noticed but not started pursuing:  My Marvell USB3 card did not seem to work with the 'official' precise 3.2 kernels either - but it works fine on rc4.  So, thanks again!

No problem. Sorry - somehow I missed this reply earlier. Glad it's working for you.

---

### Post by paul_in_london on 2011-12-03
This page might end up being of use to someone who finds themselves here:

[http://askubuntu.com/questions/37590/nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal](http://askubuntu.com/questions/37590/nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal)

---

### Post by ScislaC on 2011-12-08
> **paul_in_london said:**
> That's strange. The 3.2 kernels have been booting fine for me with nvidia-current 290.10 from xorg-edgers.

Out of curiousity, are you only running the nvidia packages from xorg-edgers, or did you upgrade your xserver too?

---

### Post by Dlambert on 2011-12-08
I would always install the linux drivers directly from Nvidia, and for some reason I would have to install them twice just for them to work. Weird right?

---

### Post by paul_in_london on 2011-12-08
> **ScislaC said:**
> Out of curiousity, are you only running the nvidia packages from xorg-edgers, or did you upgrade your xserver too?

I'm using the nvidia-current and xserver-related packages from xorg-edgers yes.

```
paul@precise-64:~$ uname -a
Linux precise-64 3.2.0-3-generic #9-Ubuntu SMP Wed Dec 7 21:06:41 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

paul@precise-64:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 290.10-0ubuntu1~xedgers~precise1
  Candidate: 290.10-0ubuntu1~xedgers~precise1
  Version table:
 *** 290.10-0ubuntu1~xedgers~precise1 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
     285.05.09-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
paul@precise-64:~$
paul@precise-64:~$ apt-cache policy xorg
xorg:
  Installed: 1:7.6+7ubuntu7edgers2
  Candidate: 1:7.6+7ubuntu7edgers2
  Version table:
 *** 1:7.6+7ubuntu7edgers2 0
        100 /var/lib/dpkg/status
     1:7.6+7ubuntu7 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
paul@precise-64:~$
paul@precise-64:~$ apt-cache policy xserver-xorg
xserver-xorg:
  Installed: 1:7.6+7ubuntu7edgers2
  Candidate: 1:7.6+7ubuntu7edgers2
  Version table:
 *** 1:7.6+7ubuntu7edgers2 0
        100 /var/lib/dpkg/status
     1:7.6+7ubuntu7 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
```

---

### Post by cariboo on 2011-12-08
> **Dlambert said:**
> I would always install the linux drivers directly from Nvidia, and for some reason I would have to install them twice just for them to work. Weird right?

I have to ask why install from Nvidia's site, when it is easier to use the drivers in the repositories, or the xorg-edgers ppa, the xorg-edgers drivers are usually only a couple of hours behind when they are released by the manufacturer.

---

