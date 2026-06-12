---
title: "NVidia 295.20 is officially out"
date: 2012-02-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by xebian on 2012-02-14
just what the title says, and working fine here.

---

### Post by VinDSL on 2012-02-15
Which xserver branch are you running?

---

### Post by pqwoerituytrueiwoq on 2012-02-15
nice to know it works in 12.04 but, it screwed up my compiz (Illegal instruction) on 10.04
edit:reinstalling the driver seems to have fixed it on my lucid install

---

### Post by xebian on 2012-02-15
> **VinDSL said:**
> Which xserver branch are you running?

 xserver-xorg-core                   2:1.11.4-0ubuntu3

---

### Post by VinDSL on 2012-02-16
Alrighty, then...

So far, so good!  ;)


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-16-feb-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-16-feb-2012-1.png")[/INDENT]


Thanks!

---

### Post by IPEX-731BA5DD06 on 2012-02-16
@VinDSL off topic, but how did you get that cool system specs to show on the right.

2ndly How did you get your processor to work without resorting to nolapic as I've had to do. If it just works, well, maybe mines a bit older, and slower.

---

### Post by VMC on 2012-02-16
> **IPEX-731BA5DD06 said:**
> @VinDSL off topic, but how did you get that cool system specs to show on the right.

2ndly How did you get your processor to work without resorting to nolapic as I've had to do. If it just works, well, maybe mines a bit older, and slower.

The first question, maybe Conky. Here's [several views]("https://www.google.com/search?q=conky+ubuntu&hl=en&prmd=imvns&tbm=isch&tbo=u&source=univ&sa=X&ei=oiM9T5W0DcWfiQLVo5WsAQ&sqi=2&ved=0CCwQsAQ&biw=1280&bih=909").

The second question, it just works on my integrated nvidia.

---

### Post by Linuxisfast on 2012-02-16
nvidia latest via xswat ppa on Lucid 10.04.3 LTS.

---

### Post by VinDSL on 2012-02-16
> **IPEX-731BA5DD06 said:**
> @VinDSL off topic, but how did you get that cool system specs to show on the right.
That's simply Conky, mixed with a little Lua code and XSLT style sheets.  

There's a link to the data dump in my sig... ;)

> **IPEX-731BA5DD06 said:**
> 2ndly How did you get your processor to work without resorting to nolapic as I've had to do. If it just works, well, maybe mines a bit older, and slower.
Here's the content of my /etc/default/grub file. 
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **[COLOR="DarkRed"]nomodeset nouveau.modeset=0[/COLOR]**"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```
Not sure if that will help you, or not.

If you try this, make sure to update grub before rebooting.

I do this mostly for running Liquorix kernels in Ubu.

---

### Post by VinDSL on 2012-02-16
> **VMC said:**
> [...] it just works on my integrated nvidia.
Surprisingly, it's working just fine on my ancient rig too (specs in sig).

Usually, I have to switch back n' forth between versions, while they're working out the bugs.

---

### Post by IPEX-731BA5DD06 on 2012-02-17
on 2, I've actually solved it.

1) I suddenly decided on a whim, go google nolapic and look.
2) Sent me to a thread, where is was suggested for a i3 processor to use the following;

noapic pci=assign-busses apicmaintainer idle=poll reboot=cold,hard

3) I edited the above into the grub config, and I now have access to both processors.

another suggestion was to disable hyperthreading, but never tried that.

It works and I so happy.

on 1) Hmm I'll have a looksee at cronky...

Thanks

---

### Post by VinDSL on 2012-02-18
> **xebian said:**
> just what the title says, and working fine here.
Just hit the precise "restricted" ppa.

I was using the xedgers package before...

---

### Post by Harry33 on 2012-02-18
> **VinDSL said:**
> Just hit the precise "restricted" ppa.

I was using the xedgers package before...

You cannot install the Precise build, if you have xserver 1.12 (from xorg-edgers).
And because of the different ABI and dependencies, force installing Precise nvidia-current on a system with xserver 1.12 will lead to breakage and uninstallation of the whole graphics driver set.

---

### Post by paul_in_london on 2012-02-18
> **Harry33 said:**
> You cannot install the Precise build, if you have xserver 1.12 (from xorg-edgers).
And because of the different ABI and dependencies, force installing Precise nvidia-current on a system with xserver 1.12 will lead to breakage and uninstallation of the whole graphics driver set.

I'm using xorg-edgers, but you can now. aptitude safe-upgrade (correctly) allows nvidia-current to be upgraded to **[COLOR="Red"]295.20-0ubuntu1.1[/COLOR]**.

```
paul@precise-64:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 295.20-0ubuntu1.1
  Candidate: 295.20-0ubuntu1.1
...

```

```
paul@precise-64:~$ apt-cache show nvidia-current
...
Depends: x11-common (>= 1:7.0.0), make, sed (>> 3.0), dkms, linux-libc-dev, libc6-dev,
linux-headers-generic | linux-headers, patch, acpid, libc6 (>= 2.2.5),
libgcc1 (>= 1:4.1.1), libx11-6, libxext6, libxv1, libxvmc1, zlib1g (>= 1:1.1.4),
**[COLOR="Red"]xorg-video-abi-12, xserver-xorg-core (>= 2:1.11.99)[/COLOR]**
...

```

The nvidia module wouldn't build at first with the 3.3-rc3 kernel (*** Unable to determine the target kernel version. ***), but when I did this:

```
cd /usr/src/linux-headers-3.3.0-030300rc3-generic/arch/x86/include
sudo cp generated/asm/unistd*.h ./asm
```

and reinstalled nvidia-current it worked ok.

---

### Post by Harry33 on 2012-02-18
> **paul_in_london said:**
> I'm using xorg-edgers, but you can now. aptitude safe-upgrade (correctly) allows nvidia-current to be upgraded to **[COLOR=Red]295.20-0ubuntu1.1[/COLOR]**.

```
paul@precise-64:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 295.20-0ubuntu1.1
  Candidate: 295.20-0ubuntu1.1
...

``````
paul@precise-64:~$ apt-cache show nvidia-current
...
Depends: x11-common (>= 1:7.0.0), make, sed (>> 3.0), dkms, linux-libc-dev, libc6-dev,
linux-headers-generic | linux-headers, patch, acpid, libc6 (>= 2.2.5),
libgcc1 (>= 1:4.1.1), libx11-6, libxext6, libxv1, libxvmc1, zlib1g (>= 1:1.1.4),
**[COLOR=Red]xorg-video-abi-12, xserver-xorg-core (>= 2:1.11.99)[/COLOR]**
...

```The nvidia module wouldn't build at first with the 3.3-rc3 kernel (*** Unable to determine the target kernel version. ***), but when I did this:

```
cd /usr/src/linux-headers-3.3.0-030300rc3-generic/arch/x86/include
sudo cp generated/asm/unistd*.h ./asm
```and reinstalled nvidia-current it worked ok.

Paul,

That is not the Precise version (295.20-0ubuntu1).
Precise version depends on xorg-video-abi-11.
And that will break xserver 1.12 installation.
The xorg-edgers xserver (1.12) version is 1.11.99.903+git20120214.d53235af-0ubuntu0ricotz2
and that has the xorg-video-abi-12. Actually it is xserver 1.12-rc3.

> Precise version depends on:
[LIST]
[*]                  [             acpid                       ]("https://launchpad.net/ubuntu/precise/amd64/acpid")
[*]                  [             dkms                       ]("https://launchpad.net/ubuntu/precise/amd64/dkms")
[*]                  [             libc6                            (>=                2.2.5)                       ]("https://launchpad.net/ubuntu/precise/amd64/libc6")
[*]                  [             libc6-dev                       ]("https://launchpad.net/ubuntu/precise/amd64/libc6-dev")
[*]                  [             libgcc1                            (>=                1:4.1.1)                       ]("https://launchpad.net/ubuntu/precise/amd64/libgcc1")
[*]                  [             libx11-6                       ]("https://launchpad.net/ubuntu/precise/amd64/libx11-6")
[*]                  [             libxext6                       ]("https://launchpad.net/ubuntu/precise/amd64/libxext6")
[*]                  [             libxv1                       ]("https://launchpad.net/ubuntu/precise/amd64/libxv1")
[*]                  [             libxvmc1                       ]("https://launchpad.net/ubuntu/precise/amd64/libxvmc1")
[*]                  [             linux-headers-generic                       ]("https://launchpad.net/ubuntu/precise/amd64/linux-headers-generic")
[*]                  [             linux-libc-dev                       ]("https://launchpad.net/ubuntu/precise/amd64/linux-libc-dev")
[*]                  [             make                       ]("https://launchpad.net/ubuntu/precise/amd64/make")
[*]                  [             patch                       ]("https://launchpad.net/ubuntu/precise/amd64/patch")
[*]                  [             sed                            (>>                3.0)                       ]("https://launchpad.net/ubuntu/precise/amd64/sed")
[*]                  [             x11-common                            (>=                1:7.0.0)                       ]("https://launchpad.net/ubuntu/precise/amd64/x11-common")
[*]                             xorg-video-abi-11
[*]                  [             xserver-xorg-core                            (>=                2:1.10.99.901)                       ]("https://launchpad.net/ubuntu/precise/amd64/xserver-xorg-core")
[*]                  [             zlib1g                            (>=                1:1.1.4]("https://launchpad.net/ubuntu/precise/amd64/zlib1g")
[/LIST]
  


---

### Post by paul_in_london on 2012-02-18
> **Harry33 said:**
> Paul,

That is not the Precise version (295.20-0ubuntu1).
Precise version depends on xorg-video-abi-11.
And that will break xserver 1.12 installation.
The xorg-edgers xserver (1.12) version is 1.11.99.903+git20120214.d53235af-0ubuntu0ricotz2
and that has the xorg-video-abi-12. Actually it is xserver 1.12-rc3.

Thanks Harry. I see what's happened. I forgot that I had this ppa enabled:

```
https://launchpad.net/~portis25/+archive/test
```

and when I didn't see a reference to any ppa in the version name I assumed that 295.20-0ubuntu1.1 was the latest precise version.

Sorry about that. :)

---

### Post by Harry33 on 2012-02-18
> **paul_in_london said:**
> Thanks Harry. I see what's happened. I forgot that I had this ppa enabled:

```
https://launchpad.net/~portis25/+archive/test
```and when I didn't see a reference to any ppa in the version name I assumed that 295.20-0ubuntu1.1 was the latest precise version.

Sorry about that. :)

No problem, at all.
BTW, you may install package nvidia-settings from Precise repos. It works fine in xserver 1.12 environment too.
Then again, Precise has higher xserver-xorg-input-evdev ATM, but that (like no other driver either) may not be installed on xserver 1.12.

---

### Post by paul_in_london on 2012-02-18
> **Harry33 said:**
> No problem, at all.
BTW, you may install package nvidia-settings from Precise repos. It works fine in xserver 1.12 environment too.
Then again, Precise has higher xserver-xorg-input-evdev ATM, but that (like no other driver either) may not be installed on xserver 1.12.

Hi Harry. In my lubuntu install I only have these ppas enabled:

```
paul@lubuntu-64:~$ history | grep ppa
    7  sudo add-apt-repository ppa:xorg-edgers/ppa
    9  sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
  216  sudo add-apt-repository ppa:chromium-daily/ppa
```

So nvidia-current is held back:

```
paul@lubuntu-64:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 295.20-0ubuntu1~xedgers~precise1
  Candidate: 295.20-0ubuntu1
```

but nvidia-settings is up to date:

```
paul@lubuntu-64:~$ apt-cache policy nvidia-settings
nvidia-settings:
  Installed: 295.20-0ubuntu1
  Candidate: 295.20-0ubuntu1
```

---

### Post by VinDSL on 2012-02-18
> **Harry33 said:**
> You cannot install the Precise build, if you have xserver 1.12 (from xorg-edgers).[...]

> **paul_in_london said:**
> 
The nvidia module wouldn't build at first with the 3.3-rc3 kernel (*** Unable to determine the target kernel version. ***), but when I did this:

```
cd /usr/src/linux-headers-3.3.0-030300rc3-generic/arch/x86/include
sudo cp generated/asm/unistd*.h ./asm
```
OMG!!!  You guys are f'ing brilliant!!!  :D

I've tried (unsuccessfully) to install Linux 3.3 / nVidia on this 32-bit / xserver 1.11 machine thrice, but was always missing a piece of the puzzle.

You're prattling, back n' forth, rang a bell in my mind, and B-I-N-G-O!


[INDENT](Click image to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-18-feb-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-18-feb-2012-1.png")[/INDENT]


Thank you, so much!!!  ;)

---

### Post by paul_in_london on 2012-02-18
> **VinDSL said:**
> OMG!!!  You guys are f'ing brilliant!!!  :D

I've tried (unsuccessfully) to install Linux 3.3 / nVidia on this 32-bit / xserver 1.11 machine thrice, but was always missing a piece of the puzzle.

You're prattling, back n' forth, rang a bell in my mind, and B-I-N-G-O!


[INDENT](Click image to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-18-feb-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-18-feb-2012-1.png")[/INDENT]


Thank you, so much!!!  ;)

No wukkas (you can google that)!

I used that work-around with 3.3-rc1 originally I think. Don't remember having to do it with 3.3-rc2, but then earlier today when I inadvertently upgraded to nvidia 295.20-0ubuntu1.1 from the portis25/test ppa the module wouldn't build with 3.3-rc3 until I did that. :)

---

### Post by paul_in_london on 2012-02-18
Just installed 3.3-rc4 and didn't have to do anything extra with nvidia. 

The fact that I still had:

```
paul@lubuntu-64:~$ ls -la /usr/src/linux-headers-3.3.0-030300rc4-generic/arch/x86/include/asm/uni*
-rw-r--r-- 1 root root 1512 Feb 19 00:35 /usr/src/linux-headers-3.3.0-030300rc4-generic/arch/x86/include/asm/unistd.h
```

after installing 3.3-rc4 seemed to be enough. :)

---

### Post by VinDSL on 2012-02-18
> **paul_in_london said:**
> Just installed 3.3-rc4 [...]
That's hilarious!

After I got done installing 3.3-rc3 (had it stored in my download folder) I checked for a newer version... nothing in the mainline kernel ppa.

Now, I guess I'll be installing Linux 3.3, for the second time today. LoL!  :D

Thanks, for the heads-up!

---

### Post by paul_in_london on 2012-02-18
> **VinDSL said:**
> That's hilarious!

After I got done installing 3.3-rc3 (had it stored in my download folder) I checked for a newer version... nothing in the mainline kernel ppa.

Now, I guess I'll be installing Linux 3.3, for the second time today. LoL!  :D

Thanks, for the heads-up!

I'm a bit of an update addict, so always on the lookout for the latest and greatest, :lolflag:

---

### Post by VinDSL on 2012-02-18
Alrighty, then...  Got Linux 3.3-rc4 / nVidia 295.20 loaded.

I used i686 generic, since a non-pae version is available now.

nVidia module wouldn't build, so I had to use the "cp" workaround again.

```
cd /usr/src/linux-headers-3.3.0-030300rc4-generic/arch/x86/include
sudo cp generated/asm/unistd*.h ./asm
```

Anyway, working great!  I used 3.3-rc3 for 2-3 hours with no anomalies noted.

Actually, Linux 3.3 is using 100MiB less mem (than Linux 3.2) sitting idle at the desktop. ;)

---

### Post by paul_in_london on 2012-02-18
> **VinDSL said:**
> Alrighty, then...  Got Linux 3.3-rc4 / nVidia 295.20 loaded.

I used i686 generic, since a non-pae version is available now.

nVidia module wouldn't build, so I had to use the "cp" workaround again.

```
cd /usr/src/linux-headers-3.3.0-030300rc4-generic/arch/x86/include
sudo cp generated/asm/unistd*.h ./asm
```

Anyway, working great!  I used 3.3-rc3 for 2-3 hours with no anomalies noted.

Actually, Linux 3.3 is using 100MiB less mem (than Linux 3.2) sitting idle at the desktop. ;)

Yep, ran into the same thing again on my main GS install which has nvidia 295.20-0ubuntu1.1.

That's the problem with multiple installs (and old age) - trying to juggle everything in my head! :)

---

### Post by Harry33 on 2012-02-19
> **paul_in_london said:**
> Yep, ran into the same thing again on my main GS install which has nvidia 295.20-0ubuntu1.1.
...


Yep, that Mingming Ren test PPA package is versioned higher in ranking (1.1) than the Precise version (1).
Thus you do not have to lock it.

---

### Post by portis on 2012-02-19
It doesn't work for me. The kernel module compilation has failed.
I just deleted it from my ppa.

> **Harry33 said:**
> Yep, that Mingming Ren test PPA package is versioned higher in ranking (1.1) than the Precise version (1).
Thus you do not have to lock it.

---

### Post by Harry33 on 2012-02-19
> **portis said:**
> It doesn't work for me. The kernel module compilation has failed.
I just deleted it from my ppa.

Perhaps you did not use a default Precise kernel or other one with the same patches.
Here your build works just fine.

---

### Post by portis on 2012-02-19
My kernel is 3.3rc3, but the nvidia-current from xorg-edgers works without a problem.


> **Harry33 said:**
> Perhaps you did not use a default Precise kernel or other one with the same patches.
Here your build works just fine.

---

### Post by VinDSL on 2012-02-19
Gotta say...

I don't know if it's Linux 3.3-rc4 or nVidia 295.20 or a combination of same, but...

Flash games on Facebook (Cafe World, Farmville, et cetera) play much, much, smoother now!

Before (and I'm talking about the past couple of years) my PC would lag out while loading these flash games -- music player (in the background) would stutter -- cursor would momentarily hang, then pop into the corner of the screen -- slow, partial, display draws, and so forth, and so on. I grew used to it, but that's all gone now.

I'm totally happy with the result(s), so far... even with the occasional, but unrelated, 12.04 alpha 2 error dialogs popping up here n' there.  ;)

---

### Post by rv65 on 2012-02-19
I have yet to see Youtube crash due to Flash since I have Flash player v11.2.202.197 (64 bit).

---

### Post by paul_in_london on 2012-02-19
> **rv65 said:**
> I have yet to see Youtube crash due to Flash since I have Flash player v11.2.202.197 (64 bit).

I'm also using v11.2.202.197 of Adobe Flash (64 bit) and it's been crashing all too frequently for me on one particular uk website that I use all the time (tvcatchup.com). Every beta of 11.2 has been awful with that site, whereas earlier flash versions have been ok. The number of times it's trashed my whole FF session really isn't funny. At least using the Session Manager FF add-on has helped to take the edge off losing a large number of open tabs.

I've probably had the odd youtube crash with 11.2.x.y, but it pales into insignificance compared with the other site.

---

### Post by paul_in_london on 2012-02-25
> **VinDSL said:**
> Alrighty, then...  Got Linux 3.3-rc4 / nVidia 295.20 loaded.

I used i686 generic, since a non-pae version is available now.

nVidia module wouldn't build, so I had to use the "cp" workaround again.

```
cd /usr/src/linux-headers-3.3.0-030300rc4-generic/arch/x86/include
sudo cp generated/asm/unistd*.h ./asm
```

Anyway, working great!  I used 3.3-rc3 for 2-3 hours with no anomalies noted.

Actually, Linux 3.3 is using 100MiB less mem (than Linux 3.2) sitting idle at the desktop. ;)

3.3-rc5 is here, but you'll need the same nvidia work-around. :)

---

### Post by VinDSL on 2012-02-25
> **paul_in_london said:**
> 3.3-rc5 is here, but you'll need the same nvidia work-around. :)
I just got done removing all of my old kernels.

Time to start filling it up, again... LoL!  :D

Thanks!

**Edit**

Whoops!  64-bit only.

Guess I'll have to wait...

---

### Post by paul_in_london on 2012-02-26
> **VinDSL said:**
> I just got done removing all of my old kernels.

Time to start filling it up, again... LoL!  :D

Thanks!

**Edit**

Whoops!  64-bit only.

Guess I'll have to wait...

Sorry about that. I forgot to say 3.3-rc5 had only been built for 64 bit. Just checked and it's the same with the daily at the moment.

---

### Post by paul_in_london on 2012-03-04
> **VinDSL said:**
> I just got done removing all of my old kernels.

Time to start filling it up, again... LoL!  :D

Thanks!

**Edit**

Whoops!  64-bit only.

Guess I'll have to wait...

Hi Vin. You're in luck this time. 3.3-rc6 is out (32 and 64 bit builds):

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-rc6-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-rc6-precise/)

After I installed the debs and booted rc6 I still needed to do:

```
cd /usr/src/linux-headers-3.3.0-030300rc6-generic/arch/x86/include/
sudo cp -v generated/asm/unistd* ./asm
sudo aptitude reinstall nvidia-current
```

before the nvidia module would build.

Then it was ok as before. :)

---

### Post by VinDSL on 2012-03-04
> **paul_in_london said:**
> Hi Vin. You're in luck this time. 3.3-rc6 is out (32 and 64 bit builds)
Good to know.  Thanks!

I'll install it this afternoon...  ;)

---

### Post by bmbaker on 2012-03-04
was trying again and still it didn't wk! when i was un-installing the kernel i saw this error anyone know how to fix this?```
bb@Dream-Test:~$ sudo apt-get remove linux-image-3.3.0-030300rc6-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.3.0-030300rc6-generic
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 117 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 418610 files and directories currently installed.)
Removing linux-image-3.3.0-030300rc6-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.3.0-030300rc6-generic /boot/vmlinuz-3.3.0-030300rc6-generic
dkms: removing: nvidia-current 295.20 (3.3.0-030300rc6-generic) (i686)

-------- Uninstall Beginning --------
Module:  nvidia-current
Version: 295.20
Kernel:  3.3.0-030300rc6-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia_current.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.3.0-030300rc6-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod........

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.3.0-030300rc6-generic /boot/vmlinuz-3.3.0-030300rc6-generic
update-initramfs: Deleting /boot/initrd.img-3.3.0-030300rc6-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.3.0-030300rc6-generic /boot/vmlinuz-3.3.0-030300rc6-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-17-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-17-generic...
P: Writing config for /boot/vmlinuz-3.2.0-16-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-16-generic...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.3.0-030300rc6-generic /boot/vmlinuz-3.3.0-030300rc6-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-17-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-17-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-17-generic
Found initrd image: /boot/initrd.img-3.2.0-17-generic
Found linux image: /boot/vmlinuz-3.2.0-16-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-16-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-16-generic
Found initrd image: /boot/initrd.img-3.2.0-16-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 11.10 (11.10) on /dev/sda1
grep: input file `/boot/grub/grub.cfg.new' is also the output
done
The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz 
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
```

---

### Post by VinDSL on 2012-03-04
Worked great...


[INDENT](Click image to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-4-mar-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-4-mar-2012-1.png")[/INDENT]


I like the refinement(s) to the "cp" command (more inclusive and verbose than what I used before).

I took a more circuitous route, too...  ;)

```

cd Downloads/Kernel [COLOR="Blue"][SIZE="1"](go to local .deb storage)[/SIZE][/COLOR]
sudo dpkg -i *.deb [COLOR="Blue"][SIZE="1"](nvidia module failed, of course)[/SIZE][/COLOR]
cd /usr/src/linux-headers-3.3.0-030300rc6-generic/arch/x86/include
sudo cp -v generated/asm/unistd* ./asm
cd Downloads/Kernel [COLOR="Blue"][SIZE="1"](back to .deb storage and reinstall)[/SIZE][/COLOR]
sudo dpkg -i *.deb [COLOR="Blue"][SIZE="1"](reinstall kernel - nvidia module compiled properly, this time)[/SIZE][/COLOR]

```
Thanks, again, for the heads up!

---

### Post by paul_in_london on 2012-03-04
> **bmbaker said:**
> was trying again and still it didn't wk! when i was un-installing the kernel i saw this error anyone know how to fix this?```
bb@Dream-Test:~$ sudo apt-get remove linux-image-3.3.0-030300rc6-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.3.0-030300rc6-generic
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 117 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 418610 files and directories currently installed.)
Removing linux-image-3.3.0-030300rc6-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.3.0-030300rc6-generic /boot/vmlinuz-3.3.0-030300rc6-generic
dkms: removing: nvidia-current 295.20 (3.3.0-030300rc6-generic) (i686)

-------- Uninstall Beginning --------
Module:  nvidia-current
Version: 295.20
Kernel:  3.3.0-030300rc6-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia_current.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.3.0-030300rc6-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod........

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.3.0-030300rc6-generic /boot/vmlinuz-3.3.0-030300rc6-generic
update-initramfs: Deleting /boot/initrd.img-3.3.0-030300rc6-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.3.0-030300rc6-generic /boot/vmlinuz-3.3.0-030300rc6-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-17-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-17-generic...
P: Writing config for /boot/vmlinuz-3.2.0-16-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-16-generic...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.3.0-030300rc6-generic /boot/vmlinuz-3.3.0-030300rc6-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-17-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-17-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-17-generic
Found initrd image: /boot/initrd.img-3.2.0-17-generic
Found linux image: /boot/vmlinuz-3.2.0-16-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-16-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-16-generic
Found initrd image: /boot/initrd.img-3.2.0-16-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 11.10 (11.10) on /dev/sda1
grep: input file `/boot/grub/grub.cfg.new' is also the output
done
The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz 
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
```

Normally /vmlinuz and /vmlinuz.old are symlinked to your current and previous (penultimate) kernels respectively. I have:

```
paul@precise-64:~$ ls -la /vml*
lrwxrwxrwx 1 root root 36 Mar  4 14:19 /vmlinuz -> boot/vmlinuz-3.3.0-030300rc6-generic
lrwxrwxrwx 1 root root 36 Feb 26 00:24 /vmlinuz.old -> boot/vmlinuz-3.3.0-030300rc5-generic
paul@precise-64:~$
```

So you probably want to recreate these symlinks to point to the two kernels you want (you may need to use **[COLOR="Red"]ln -sf[/COLOR]**)

Once you've done that run:

```
sudo update-grub
```

from your "controlling" install if you're dual-booting.

HTH.

---

### Post by paul_in_london on 2012-03-04
> **VinDSL said:**
> Worked great...


[INDENT](Click image to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-4-mar-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-4-mar-2012-1.png")[/INDENT]


I like the refinement(s) to the "cp" command (more inclusive and verbose than what I used before).

I took a more circuitous route, too...  ;)

```

cd Downloads/Kernel [COLOR="Blue"][SIZE="1"](go to local .deb storage)[/SIZE][/COLOR]
sudo dpkg -i *.deb [COLOR="Blue"][SIZE="1"](nvidia module failed, of course)[/SIZE][/COLOR]
cd /usr/src/linux-headers-3.3.0-030300rc6-generic/arch/x86/include
sudo cp -v generated/asm/unistd* ./asm
cd Downloads/Kernel [COLOR="Blue"][SIZE="1"](back to .deb storage and reinstall)[/SIZE][/COLOR]
sudo dpkg -i *.deb [COLOR="Blue"][SIZE="1"](reinstall kernel - nvidia module compiled properly, this time)[/SIZE][/COLOR]

```
Thanks, again, for the heads up!

You're welcome mate. :)

---

### Post by bmbaker on 2012-03-04
@ paul_in_london hmmmm ok i have a bash at that in the morning. thanks for the pointers :-)

---

### Post by paul_in_london on 2012-03-10
You can give it a go with 3.3-rc7 now guys.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-rc7-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-rc7-precise/)

Working ok here. This 64 bit install has:

```
paul@precise-64:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 295.20-0ubuntu1.2
  Candidate: 295.20-0ubuntu1.2
```

(which was removed from the portis25/test ppa a while back) and I had to use the "cp work-around".

My other 64 bit install on the same box (lubuntu) is using the xorg-edgers version of nvidia-current. No jiggery-pokery with the kernel upgrade was required there.

---

### Post by VinDSL on 2012-03-10
> **paul_in_london said:**
> You can give it a go with 3.3-rc7 now guys.
Interesting!

Working great here, but I'm not sure if it's Linux 3.3-rc7, or the 173 upgrades that I just performed.  LoL!  :D

I've been putting off updating, the past few days, because this-or-that was being held back.  Today, the only package being held was Gimp 2.0, so I decided to get, while the getting was good.

Anyway, all's well that ends well, yes?

---

### Post by Harry33 on 2012-03-11
> **VinDSL said:**
> Interesting!

Working great here, but I'm not sure if it's Linux 3.3-rc7, or the 173 upgrades that I just performed.  LoL!  :D

I've been putting off updating, the past few days, because this-or-that was being held back.  Today, the only package being held was Gimp 2.0, so I decided to get, while the getting was good.

Anyway, all's well that ends well, yes?

What version of Gimp is 2.0?
We have 2.6.12 in Precise repos and 2.7.5 is already out there (PPA).

---

### Post by VinDSL on 2012-03-11
> **Harry33 said:**
> What version of Gimp is 2.0?
We have 2.6.12 in Precise repos and 2.7.5 is already out there (PPA).
I'm using version 2.7.5-2012020902~oo from Matt Walker's PPA.

There isn't a "~pp" version (in his repo) and the current glib and/or gtk is causing the upgrade to be held back.

Maybe, I'll designate a different repo...  ;)

---

### Post by bmbaker on 2012-03-12
so i took another run at installing the rc7 kernel but again no joy!

but i did get some intersting output both when installing the kernel and reinstalling nvidia-current that i had not seen before

```
Setting up nvidia-current (295.20-0ubuntu1) ...
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-3.2.0-18-generic
INFO:Enable nvidia-current
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad
DEBUG:Processing quirk Latitude E6530
DEBUG:Matching "sys_vendor" with value "LENOVO"...
DEBUG:Success
DEBUG:Matching "product_version" with value "ThinkPad T420s"...
DEBUG:Failure
DEBUG:Quirk doesn't match
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Matching "sys_vendor" with value "LENOVO"...
DEBUG:Success
DEBUG:Matching "product_version" with value "ThinkPad T420s"...
DEBUG:Failure
DEBUG:Quirk doesn't match
Loading new nvidia-current-295.20 DKMS files...
Building for 3.2.0-18-generic and 3.3.0-030300rc7-generic
Building for architecture x86_64
Building initial module for 3.2.0-18-generic
Done.

nvidia_current:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-18-generic/updates/dkms/

depmod....

DKMS: install completed.
Building initial module for 3.3.0-030300rc7-generic
Done.

nvidia_current:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.3.0-030300rc7-generic/updates/dkms/

depmod....

DKMS: install completed.
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.3.0-030300rc7-generic

```

is this maybe why the kernel with nvidia-current fails??
my laptop is a lenovo T61p

---

