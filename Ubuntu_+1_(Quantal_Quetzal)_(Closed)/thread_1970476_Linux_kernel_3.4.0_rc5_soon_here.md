---
title: "Linux kernel 3.4.0 rc5 soon here"
date: 2012-05-01
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-05-01
The new linux kernel 3.4.0 rc5 will soon hit the Quantal repos.
This is the second attempt to build it here, though it failed:

[https://launchpad.net/ubuntu/quantal/+source/linux/3.4.0-1.2](https://launchpad.net/ubuntu/quantal/+source/linux/3.4.0-1.2)

---

### Post by dino99 on 2012-05-01
i386 have failed again :( , python3 will give some headaches for this early alpha.

---

### Post by xebian on 2012-05-01
Hmm..wonders why it's failing.  I have compiled src from kernel.org with quantal 4.7 right after rc5 came out successfully.
```

Linux version 3.4.0-rc5-ik1 (root@kubu1) (gcc version 4.7.0 (Ubuntu/Linaro 4.7.0-4ubuntu2) ) #1 SMP Sun Apr 29 18:02:04 CDT 2012
```

Maybe the newer "gcc 4:4.7.0-5ubuntu1 " is the reason?

---

### Post by JMB74 on 2012-05-01
> **xebian said:**
> Hmm..wonders why it's failing.

Buildlog seems to say that the docbook-utils dep couldn't be installed.

I think there was a new tex-common upload at about the same time...

---

### Post by xebian on 2012-05-01
> **JMB74 said:**
> Buildlog seems to say that the docbook-utils dep couldn't be installed.

I think there was a new tex-common upload at about the same time...

I was thinking something connected to kernel patches, and/or compiler/linker flags.

---

### Post by JMB74 on 2012-05-01
[https://launchpadlibrarian.net/103765039/buildlog_ubuntu-quantal-i386.linux_3.4.0-1.2_FAILEDTOBUILD.txt.gz](https://launchpadlibrarian.net/103765039/buildlog_ubuntu-quantal-i386.linux_3.4.0-1.2_FAILEDTOBUILD.txt.gz)

> Reading package lists... 
Building dependency tree... 
Reading state information... 
Some packages could not be installed. 
This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming. 
The following information may help to resolve the situation:  
[COLOR=Red]The following packages have unmet dependencies:  docbook-utils : Depends: jadetex but it is not going to be installed [/COLOR]
E: Unable to correct problems, you have held broken packages.
 apt-get failed. 
Package installation failed 
Trying to reinstall removed packages: 
Trying to uninstall newly installed packages: 
Source-dependencies not satisfied; skipping linux ****************************************************************************** Finished at 20120501-1443 Build needed 00:00:00, 0k disk space

EDIT: Just saw that debian sync is causing dependency probs for now.

---

### Post by VinDSL on 2012-05-01
> **Harry33 said:**
> The new linux kernel 3.4.0 rc5 will soon hit the Quantal repos.[...]
Good Ol' Mainline Kernel works...  ):P


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-1-may-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-1-may-2012-1.png")[/INDENT]

---

### Post by Harry33 on 2012-05-02
The 3.4.0 rc5 kernel is now in Quantal repos:

[https://launchpad.net/ubuntu/quantal/+source/linux/3.4.0-1.2](https://launchpad.net/ubuntu/quantal/+source/linux/3.4.0-1.2)

---

### Post by VinDSL on 2012-05-02
Beautiful!  

Thanks, Harry!  I haven't "seen" Plymouth in ages. LoL! :D


[INDENT][IMG]http://vindsl.com/images/vindsl-linux-3.4-2-may-2012.png[/IMG][/INDENT]


As usual, everything is working great!

Gotta love these pre-alphas... :guitar:

---

### Post by VinDSL on 2012-05-02
7 hours later...

Okay, fully updated (another 103 package upgrades) and survived a cold boot.

Time to purge some old kernels.  :)

---

### Post by jppr on 2012-05-02
[https://launchpad.net/ubuntu/quantal/+source/linux-meta/3.4.0.1.1](https://launchpad.net/ubuntu/quantal/+source/linux-meta/3.4.0.1.1)

---

### Post by 3vi1 on 2012-05-02
Nvidia proprietary blobs appear to not be in love with the new kernel.

```
Setting up linux-headers-3.4.0-1-generic (3.4.0-1.2) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.4.0-1-generic /boot/vmlinuz-3.4.0-1-generic
Error! Bad return status for module build on kernel: 3.4.0-1-generic (x86_64)
Consult /var/lib/dkms/nvidia-current/295.40/build/make.log for more information.
Error! Bad return status for module build on kernel: 3.4.0-1-generic (x86_64)
Consult /var/lib/dkms/nvidia-current-updates/295.40/build/make.log for more information.

```

```
In file included from /var/lib/dkms/nvidia-current-updates/295.40/build/nv.c:13:0:
/var/lib/dkms/nvidia-current-updates/295.40/build/nv-linux.h: At top level:
/var/lib/dkms/nvidia-current-updates/295.40/build/nv-linux.h:114:75: fatal error: asm/system.h: No such file or directory
compilation terminated.

```

---

### Post by *^kyfds( on 2012-05-02
> **VinDSL said:**
> Good Ol' Mainline Kernel works...  ):P
[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-1-may-2012-1%28650x520%29.png[/IMG]]("http://vindsl.com/images/vindsl-desktop-1-may-2012-1.png")[/INDENT]

my jaw hit the floor when i saw this screenshot.

nice backround dude! :D

---

### Post by 3vi1 on 2012-05-02
> **Thehumorouscheese said:**
> my jaw hit the floor when i saw this screenshot.

Vin's always got the best looking screenshots.  He's the one that turned me on to using conky - though my desktop still never looks as good as his.

---

### Post by xebian on 2012-05-02
Quantal seems a bit strange right now.  

```
p   linux-image-3.4.0-1-generic                                           - Linux kernel image for version 3.4.0 on 32 bit x86 SMP                          
p   linux-image-3.4.0-1-generic-pae:i386                                  - Linux kernel image for version 3.4.0 on 32 bit x86 SMP      
```                    

Not sure if this is just typo or not though I'm betting it is.

---

### Post by Cheesemill on 2012-05-02
It's a typo, I'm running it now:
```
root@quantal:/# aptitude search linux-image-3.4
i   linux-image-3.4.0-1-generic                                                  - Linux kernel image for version 3.4.0 on 32 bit x86 SMP                                
p   linux-image-3.4.0-1-generic-pae:i386                                         - Linux kernel image for version 3.4.0 on 32 bit x86 SMP                                
p   linux-image-3.4.0-1-virtual                                                  - Linux kernel image for version 3.4.0 on 32 bit x86 Virtual Guests                     
p   linux-image-3.4.0-1-virtual:i386                                             - Linux kernel image for version 3.4.0 on 32 bit x86 Virtual Guests                     
root@quantal:/# uname -a
Linux quantal 3.4.0-1-generic #2-Ubuntu SMP Tue May 1 13:03:06 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by Mathor on 2012-05-02
I just installed the one from the repos, and it is working perfectly on this machine. :P

---

### Post by cecilpierce on 2012-05-02
> **Mathor said:**
> I just installed the one from the repos, and it is working perfectly on this machine. :P

Yea 3.4.0-1 and it had problems with the nvidia-current (295-40). Boots to fail-safe vesa mode with huge graphics  :confused:

Back on the old kernel now til some one else has a fix or maybe its me
 :P

---

### Post by Bowmore on 2012-05-02
Right, the new kernel doesn't like nvidia-current. This is due to missing header files for most of the archs.

A workaround is to manually copy those header files from arm to x86:
```
cd /usr/src/linux-headers-3.4.0-1/arch
sudo cp arm/include/asm/system.h x86/include/asm/
sudo cp arm/include/asm/compiler.h x86/include/asm/
sudo cp arm/include/asm/system_info.h x86/include/asm/
sudo cp arm/include/asm/system_misc.h x86/include/asm/
```and then reinstall the kernel via synaptic.

---

### Post by Harry33 on 2012-05-02
I am using xserver 1.12.1 from xorg-edgers so I am also using differently built nvidia-current.
It depends on xorg-video-abi-12, for xserver 1.11.4 (precise and quantal ATM) it is xorg-video-abi-11.

Anyways nvidia-current (both 295.40 and the new 302.07) builds fine and works fine with linux kernel 3.4.0-1 (rc5) from quantal repos.

---

### Post by xebian on 2012-05-02
I haven't been paying much attention lately but now even though I have 64-bit installation the 32-bit packages are showing up and available for installation?

Haven't used a 32-bit ubuntu since 2005 but can @VinDSL confirm if these 64-bit packages are showing up in your 32-bit installation?

No wonder APT seems sluggish lately as it has to fetch and search twice as many packages/indices.  I find it absurd to bother with the 32-bits when I have no need for them.  Is there a way of setting a flag to ignore them altogether?

---

### Post by Bowmore on 2012-05-02
@Harry
Ok, but those two nvidia driver versions contain dkms patches for the 3.4 kernel that probably fix this issue for xorg-edgers.

---

### Post by pressureman on 2012-05-02
> **xebian said:**
> I haven't been paying much attention lately but now even though I have 64-bit installation the 32-bit packages are showing up and available for installation?

Do you have 'foreign-architecture i386' in your /etc/dpkg/dpkg.cfg.d/multiarch?

---

### Post by VinDSL on 2012-05-02
> **xebian said:**
> Haven't used a 32-bit ubuntu since 2005 but can @VinDSL confirm if these 64-bit packages are showing up in your 32-bit installation?
Yes, I can see several pages of 64-bit upgrades available, including kernel images & headers.

It does seem (ahem) a bit senseless...   :)

---

### Post by xebian on 2012-05-02
> **pressureman said:**
> Do you have 'foreign-architecture i386' in your /etc/dpkg/dpkg.cfg.d/multiarch?

Commented this line and apt-get update is now faster without those 32-bit.

Thanks a lot.

---

### Post by xebian on 2012-05-02
> **VinDSL said:**
> Yes, I can see several pages of 64-bit upgrades available, including kernel images & headers.

It does seem (ahem) a bit senseless...   :)

It is.  But the master @pressureman showed a way.  Comment out this line in /etc/dpkg/dpkg.cfg/multiarch 

#[COLOR="Red"]foreign-architecture i386[/COLOR]  <<== probably amd64 in your case.

then apt-get update to refresh indices.  Do a aptitude search  'something' and you can now only see <pkg-name>i386, and less clutter.

---

### Post by xebian on 2012-05-02
For 64-bit it makes some sense because you can run 32-bit but for 32-bit installation it's absolute nonsense to include 64-bit. I suggest for 32-bit, this should be off by default.

---

### Post by cecilpierce on 2012-05-02
> **Bowmore said:**
> Right, the new kernel doesn't like nvidia-current. This is due to missing header files for most of the archs.

A workaround is to manually copy those header files from arm to x86:
```
cd /usr/src/linux-headers-3.4.0-1/arch
sudo cp arm/include/asm/system.h x86/include/asm/
sudo cp arm/include/asm/compiler.h x86/include/asm/
sudo cp arm/include/asm/system_info.h x86/include/asm/
sudo cp arm/include/asm/system_misc.h x86/include/asm/
```and then reinstall the kernel via synaptic.

Thanks, that fixed it for now, whats next?
:lolflag:

---

### Post by 3vi1 on 2012-05-02
I was able to get it running, after copying the headers and fixing nvidia-current.

But... I had to jump back to the 3.2 kernel on my main machine.

Each time I test the 3.4.0-1 kernel, I get a full system freeze (sometimes I can't even ctrl-alt-sysreq-reboot) within a minute or two after signing in.  It's odd, because everything seems to work okay, then the system locks hard.

I *think* it's locking when the Ubuntu One syncdaemon kicks in.

Anyone else seeing this?

My sys:  x58 mobo, i980x CPU, 12GB RAM, nV GeForce 560 Ti

(3.4 works fine on a second system I'm testing, with all different specs)

---

### Post by pressureman on 2012-05-02
The package description is wrong on the amd64 package (apt-cache show linux-image-3.4.0-1-generic):

```

Description-en: Linux kernel image for version 3.4.0 on 32 bit x86 SMP
 This package contains the Linux kernel image for version 3.4.0 on
 32 bit x86 SMP.

```

and 'dpkg -l | grep linux-image'
```

ii  linux-image-3.2.0-23-generic           3.2.0-23.36                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-24-generic           3.2.0-24.37                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.4.0-1-generic            3.4.0-1.2                               Linux kernel image for version 3.4.0 on 32 bit x86 SMP
ii  linux-image-generic                    3.4.0.1.1                               Generic Linux kernel image

```

Even though it sounds like a wild ride, I don't usually mix and match 64 and 32 bit kernels on my box.

---

### Post by pressureman on 2012-05-02
> **xebian said:**
> It is.  But the master @pressureman showed a way.  Comment out this line in /etc/dpkg/dpkg.cfg/multiarch 

#[COLOR="Red"]foreign-architecture i386[/COLOR]  <<== probably amd64 in your case.

then apt-get update to refresh indices.  Do a aptitude search  'something' and you can now only see <pkg-name>i386, and less clutter.

There's no reason whatsoever to have 'foreign-architecture amd64' on a 32-bit machine, as they are not forwards-compatible with 64 bit arch. A 64 bit application simply will not run on a 32 bit machine.

Remember that you'll need 'foreign-architecture i386' if you want to install closed-source, 32 bit apps like Skype on your 64 bit machine.

---

### Post by VinDSL on 2012-05-02
I purged all unused kernels, this morning.

My options are a little sparse, right now.  LoL!  :D


```
vindsl@Zuul:~$ dpkg -l | grep linux-image
ii  linux-image-3.2.0-14.dmz.1-liquorix-686   3.2.0-19                                                        Linux 3.2.0 for modern PCs
ii  linux-image-3.4.0-1-generic-pae           3.4.0-1.2                                                       Linux kernel image for version 3.4.0 on 32 bit x86 SMP

```

---

### Post by Mathor on 2012-05-02
I'm so glad I don't have nvidia sometimes. 3.4.0-1 works fine. I'm not using the edgers ppa, either.

Linus Torvalds said there were some new issues that came with this release (rc5).  I'm looking to linux 3.5.

---

### Post by Xgen on 2012-05-03
> **Mathor said:**
> I'm so glad I don't have nvidia sometimes. 3.4.0-1 works fine.

Are you using the propriety driver? Tried AMD 12.3 and 12.4, but no success. It only logins to 2d. The 3.3 kernel works fine with the propriety drivers.

---

### Post by pressureman on 2012-05-07
Anyone else suddenly start having boot problems with this linux-image-3.4.0-1-generic? I installed it last week, and had a couple of boot hangs, but otherwise it was working.

This morning however, my Thinkpad T500 was consistently freezing, just before lightdm appeared - sometimes I'd get a mouse cursor just before it hung. Booting failsafe mode (and continuing with normal boot once prompted) worked fine - but of course was running in VESA mode. So it would appear to be something gfx-related (running "Integrated Graphics Chipset: Intel(R) GM45" here).

I booted the older 3.2.0 kernel, and had no problems. It's weird that this has only just started happening several days after installing 3.4.0.

---

### Post by Harry33 on 2012-05-07
> **pressureman said:**
> Anyone else suddenly start having boot problems with this linux-image-3.4.0-1-generic? I installed it last week, and had a couple of boot hangs, but otherwise it was working.

This morning however, my Thinkpad T500 was consistently freezing, just before lightdm appeared - sometimes I'd get a mouse cursor just before it hung. Booting failsafe mode (and continuing with normal boot once prompted) worked fine - but of course was running in VESA mode. So it would appear to be something gfx-related (running "Integrated Graphics Chipset: Intel(R) GM45" here).

I booted the older 3.2.0 kernel, and had no problems. It's weird that this has only just started happening several days after installing 3.4.0.

This is perhaps in a wrong thread, as this concerns only the official 3.4.0 kernel in Quantal repos.
Anyways, it would help to know which updates you run before these problems with booting.

---

### Post by pressureman on 2012-05-07
> **Harry33 said:**
> This is perhaps in a wrong thread, as this concerns only the official 3.4.0 kernel in Quantal repos.
Anyways, it would help to know which updates you run before these problems with booting.

It's simply a fully up to date quantal amd64 install. At first I suspected libxv1, as that was one of the most recent updates, so I downgraded that, but to no avail.

It's not a big deal, as I have a workaround for now. Hopefully the next 3.4.0 rc will fix it. I was just curious if anybody else had noticed the same symptoms.

---

### Post by jerrylamos on 2012-05-07
?  One of my pc's, the tower, running -2D, updated to 3.4.  It has an ATI radeon xpress 200 and booted to black screen no cli until repeated rescue mode "fix broken packages" got it going, running O.K. (for a pre-Alpha).

This notebook running quantal lubuntu, is still at 3.2 after update/upgrade.

My netbook, running -2D, repeated update/upgrade still at 3.2.

?

Now I know I could fiddle around and get 3.4 going, I did that on another install, but I'm really trying to test whatever the usual update/upgrades do, i.e. I run whatever ubuntu throws over the wall with a rock tied to it.

Jerry

p.s. updated my wide screen notebook with 1280x1024 external monitor and update brought in 3.4 running O.K.  Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6310].  I'll give another go on my netbook and lubuntu quantal tomorrow to see if 3.4 comes in on them.

---

### Post by xebian on 2012-05-07
> **pressureman said:**
> It's simply a fully up to date quantal amd64 install. At first I suspected libxv1, as that was one of the most recent updates, so I downgraded that, but to no avail.

It's not a big deal, as I have a workaround for now. Hopefully the next 3.4.0 rc will fix it. I was just curious if anybody else had noticed the same symptoms.

Not seeing them here with 302.07, and also rc6 is working fine too.

---

### Post by VinDSL on 2012-05-07
> **xebian said:**
> Not seeing them here with 302.07, and also rc6 is working fine too.
Dittos... ;)

---

### Post by Miykel on 2012-05-08
G'Day  Could someone please explain this, I seem to have version 3.4.0.1.3 along with all these other kernels, should I remove the older ones.

miykel@miykel:~$ dpkg -l | grep linux-image
rc  linux-image-3.2.0-23-generic           3.2.0-23.36                                                     Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.4.0-1-generic            3.4.0-1.3                                                       Linux kernel image for version 3.4.0 on 64 bit x86 SMP
rc  linux-image-3.4.0-999-generic          3.4.0-999.201205070447                                          Linux kernel image for version 3.4.0 on 32 bit x86 SMP
ii  linux-image-generic                    3.4.0.1.1                                                       Generic Linux kernel image

Kind Regards Miykel

---

### Post by pressureman on 2012-05-08
The 'rc' at the start of the line indicates 'removed' and 'configured', so the bulk of the backage is already removed - only config files remain. You can 'sudo apt-get purge foopackagename' to clean this up.

---

### Post by VinDSL on 2012-05-08
I always keep a fallback *DISTRO* on this machine (in a separate partition)... currently, Ubu 10.10 (even though it's been orphaned).  After all, I *need* something to boot into, in case of Unity borkage... and to test Conky scripts in Gnome 2.  :D

As far as "testing" kernels are concerned... I usually wait until I've collected 3-4 of them (about 7-10 days), keep the latest and greatest kernel (singular), then I purge the old ones, and start the cycle all over again.

Thus, if you will, I always maintain:
[LIST=1]
[*]The latest "testing" kernel
[*]A few 7-10 days old kernels
[*]And, a fallback distro
[/LIST].
I digress: I have any number of bootable thumb-drives (with persistence) laying around, but using them adds a level of unnecessary complexity.  I mostly use them for "testing" my lappy and netbook, and don't like to boot my desktop machine with them.

Anyway... it's really up to you.  Loading up your HD with kernels won't hurt anything, but I try to keep a handle on the cruft, you know?!?!?  ;)

---

