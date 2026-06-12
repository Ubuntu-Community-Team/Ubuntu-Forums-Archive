---
title: "Just noticed Kernel 3.3-rc1 is here"
date: 2012-01-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by paul_in_london on 2012-01-19
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-rc1-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-rc1-precise/)

---

### Post by paul_in_london on 2012-01-19
Hmm. Not completely unexpected, but haven't had an nvidia build failure with an rc kernel for a while.

```
paul@precise-64:~/3.3$ cat /var/lib/dkms/nvidia-current/290.10/build/make.log
DKMS make.log for nvidia-current-290.10 for kernel 3.3.0-030300rc1-generic (x86_64)
Fri Jan 20 00:10:01 GMT 2012
If you are using a Linux 2.4 kernel, please make sure
you either have configured kernel sources matching your
kernel or the correct set of kernel headers installed
on your system.

If you are using a Linux 2.6 kernel, please make sure
you have configured kernel sources matching your kernel
installed on your system. If you specified a separate
output directory using either the "KBUILD_OUTPUT" or
the "O" KBUILD parameter, make sure to specify this
directory with the SYSOUT environment variable or with
the equivalent nvidia-installer command line option.

Depending on where and how the kernel sources (or the
kernel headers) were installed, you may need to specify
their location with the SYSSRC environment variable or
the equivalent nvidia-installer command line option.

*** Unable to determine the target kernel version. ***

make: *** [select_makefile] Error 1
paul@precise-64:~/3.3$
```

EDIT: Tried this:

```
paul@precise-64:~$ cd /var/lib/dkms/nvidia-current/290.10/build/
paul@precise-64:/var/lib/dkms/nvidia-current/290.10/build$ sudo make -f Makefile.nvidia

gcc-version-check failed:

The compiler used to compile the kernel (gcc
4.4) does not exactly match the current compiler
(gcc 4.6).  The Linux 2.6 kernel module loader
rejects kernel modules built with a version of gcc
that does not exactly match that of the compiler
used to build the running kernel.

If you know what you are doing and want to override
the gcc version check, you can do so by setting the
IGNORE_CC_MISMATCH environment variable to "1".

In any other case, set the CC environment variable
to the name of the compiler that was used to compile
the kernel.

*** Failed CC version check. Bailing out! ***

In file included from /lib/modules/3.2.1-030201-generic/build/include/linux/kernel.h:13:0,
                 from /lib/modules/3.2.1-030201-generic/build/include/linux/sched.h:55,
                 from /lib/modules/3.2.1-030201-generic/build/include/linux/utsname.h:35,
                 from nv-linux.h:38,
                 from nv.c:13:
/lib/modules/3.2.1-030201-generic/build/include/linux/linkage.h:5:25: fatal error: asm/linkage.h: No such file or directory
compilation terminated.
make: *** [nv.o] Error 1
paul@precise-64:/var/lib/dkms/nvidia-current/290.10/build$
```

---

### Post by xyzzyman on 2012-01-19
It kind of stinks but there won't be ubuntu patches for these 3.3 mainline kernels. I've liked using the 3.2 code from launchpad, so I get the best of ubuntu plus optimizing for my system. Luckily they are backporting some good parts of the 3.3 code though.

---

### Post by paul_in_london on 2012-01-19
> **xyzzyman said:**
> It kind of stinks but there won't be ubuntu patches for these 3.3 mainline kernels. I've liked using the 3.2 code from launchpad, so I get the best of ubuntu plus optimizing for my system. Luckily they are backporting some good parts of the 3.3 code though.

Didn't know that. Usually (as far as I remember) when this happens it comes together after a few rc's. May not be a good idea to try and force the nvidia module build in these circumstances. And I prefer to use debs instead of nvidia's own installer.

---

### Post by Bobhuber on 2012-01-20
It won't compile using Nvidia's installer either .

---

### Post by paul_in_london on 2012-01-20
> **Bobhuber said:**
> It won't compile using Nvidia's installer either .

Doh! :(

---

### Post by zika on 2012-01-21
kernel.ubuntu.com is down?
3.3 works nicely...
Update: It's back!

---

### Post by rockorequin on 2012-01-23
There's a manual fix for the nvidia issue at [http://weltall.heliohost.org/wordpress/2012/01/20/linux-kernel-3-3-rc1-and-nvidia-drivers/](http://weltall.heliohost.org/wordpress/2012/01/20/linux-kernel-3-3-rc1-and-nvidia-drivers/).

I followed the second option and ran:

```
sudo cd /lib/modules/$(uname -r)/source/arch/x86/include
sudo cp generated/asm/unistd*.h ./asm

``` 

and after this the nvidia module compiled fine.

---

### Post by paul_in_london on 2012-01-23
> **rockorequin said:**
> There's a manual fix for the nvidia issue at [http://weltall.heliohost.org/wordpress/2012/01/20/linux-kernel-3-3-rc1-and-nvidia-drivers/](http://weltall.heliohost.org/wordpress/2012/01/20/linux-kernel-3-3-rc1-and-nvidia-drivers/).

I followed the second option and ran:

```
sudo cd /lib/modules/$(uname -r)/source/arch/x86/include
sudo cp generated/asm/unistd*.h ./asm

``` 

and after this the nvidia module compiled fine.

Ah - thanks a lot. I'll try that later when I get home!

---

### Post by teh603 on 2012-01-23
Tried it, and it not only didn't fix the touchcreen issue on my Dell Duo, it also re-broke ACPI on it.

Nice breaking it, hero.

---

### Post by Bobhuber on 2012-01-23
> **rockorequin said:**
> There's a manual fix for the nvidia issue at [http://weltall.heliohost.org/wordpress/2012/01/20/linux-kernel-3-3-rc1-and-nvidia-drivers/](http://weltall.heliohost.org/wordpress/2012/01/20/linux-kernel-3-3-rc1-and-nvidia-drivers/).

I followed the second option and ran:

```
sudo cd /lib/modules/$(uname -r)/source/arch/x86/include
sudo cp generated/asm/unistd*.h ./asm

```and after this the nvidia module compiled fine.
That worked great - Thanks for the post

---

### Post by zika on 2012-01-23
No kernel yesterday, no kernel today... ?

---

### Post by xyzzyman on 2012-01-23
> **zika said:**
> No kernel yesterday, no kernel today... ?

Mainline release candidates are usually a week in between at the earliest.

---

### Post by paul_in_london on 2012-01-23
> **xyzzyman said:**
> Mainline release candidates are usually a week in between at the earliest.

I think we're talking about the daily build here:

```
http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/
```

(latest one seems to be 20th Jan).

---

### Post by zika on 2012-01-23
> **xyzzyman said:**
> Mainline release candidates are usually a week in between at the earliest.&#8222;Daily&#8220; and &#8222;current&#8220; are (usually) daily and current...
For us, &#8222;kernel junkies&#8220;...

---

### Post by xyzzyman on 2012-01-23
The mainline kernel's aren't part of the PP development cycle when it comes to 'daily' & 'current'. PP is using 3.2 kernel and backporting some things from 3.3, and 3.2 now that it's final will see less updates except for bug fixes and security, so the Ubuntu kernel team at this point has less to update. I was using the PP source to compile my oneirc kernel all through the RC phase for 3.2 but now I started paying more attention at the change logs. And the last few 3.2's have been extremely minor.

If it makes you feel better they are expecting another release candidate for 3.3 in a day or two.

For reference as it came up earlier in the thread and in others, here's the actual description of what mainline is what it's purpose is:

[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000542.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000542.html)
> Hi Everyone,

The Ubuntu Kernel Team is pleased to announce the availability of
mainline kernel builds for testing [1].  This will allow users to run
the unmodified upstream vanilla kernel.  This can be useful for
verifying fixes upstream, testing for regressions introduced by Ubuntu
specific changes, or confirming bugs exist upstream and subsequently
help to report bugs upstream.

The mainline kernels are packaged for each stable release (and stable
release update) as well as the current -rc releases.  They are available
as .deb files for easy installation.  Keep in mind that even though they
are built using the Ubuntu kernel config files, they do not contain any
Ubuntu specific drivers.  Also, there are no restricted modules for
these kernels.  They are strictly the vanilla mainline kernel source.
That being said, the Ubuntu kernel team does not support these kernels
so use at your own risk.

Thanks,
The Kernel Team

---

### Post by zika on 2012-01-23
> **xyzzyman said:**
> The mainline kernel's aren't part of the PP development cycle when it comes to 'daily' & 'current'. PP is using 3.2 kernel and backporting some things from 3.3, and 3.2 now that it's final will see less updates except for bug fixes and security, so the Ubuntu kernel team at this point has less to update. I was using the PP source to compile my oneirc kernel all through the RC phase for 3.2 but now I started paying more attention at the change logs. And the last few 3.2's have been extremely minor.

If it makes you feel better they are expecting another release candidate for 3.3 in a day or two.

For reference as it came up earlier in the thread and in others, here's the actual description of what mainline is what it's purpose is:

[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000542.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000542.html)As a &#8222;kernel junkie&#8220; that uses daily for years I've surely read all that. I'm (just) lazy to compile it every day... ;) Thank You...

---

### Post by paul_in_london on 2012-01-23
Got it working in the end :)

Was getting a checksum error to start with when I tried to run the nvidia installer until I resorted to grabbing the .run file with wget.

The next problem was where to find **generated/asm/unistd*.h**. After a bit of head-scratching I got it:

```
cd /usr/src/linux-headers-3.3.0-030300rc1-generic/arch/x86/include
cp generated/asm/unistd*.h ./asm
```

Then the 295.09 driver installed ok.

---

### Post by rodercot on 2012-01-31
hey all,

 I have been playing around on a test machine with mythbuntu I am trying to figure out how you got the 295.90-0 driver activated from the ppa. I installed the ppa 290.10 from the x-swat ppa is installed. I cannot get the 295.09 driver to even make itself known to the system and no matter what as soon as I installed ANY restricted driver I get a black screen on reboot with 11.10. I rolled back to lucid and installed the daily kernel on it with no issues, updated to 290.10 reboots fine just did alsa 1.0.25 no issues but I still cannot get the system to find the 295.09-0 from the ppa.

 thanks,

 Dave

---

### Post by paul_in_london on 2012-01-31
> **rodercot said:**
> hey all,

 I have been playing around on a test machine with mythbuntu I am trying to figure out how you got the 295.90-0 driver activated from the ppa. I installed the ppa 290.10 from the x-swat ppa is installed. I cannot get the 295.09 driver to even make itself known to the system and no matter what as soon as I installed ANY restricted driver I get a black screen on reboot with 11.10. I rolled back to lucid and installed the daily kernel on it with no issues, updated to 290.10 reboots fine just did alsa 1.0.25 no issues but I still cannot get the system to find the 295.09-0 from the ppa.

 thanks,

 Dave

If (like me) you're using the xorg-edgers ppa which only has the 290.10 nvidia driver you can add this ppa to get 295.09:

```
sudo add-apt-repository ppa:portis25/test
```

Your boot problems may be caused by unity-greeter segfaulting. See my posts here:

[http://ubuntuforums.org/showpost.php?p=11646788&postcount=16](http://ubuntuforums.org/showpost.php?p=11646788&postcount=16)
[http://ubuntuforums.org/showpost.php?p=11648207&postcount=44](http://ubuntuforums.org/showpost.php?p=11648207&postcount=44)

---

### Post by rodercot on 2012-01-31
Thanks,

 I will try those out tonight. The only thing, I know mythbuntu uses lightdm on 11.10 but I look in the lightdm.conf file and did not see unity or greeter mentioned at all. I will check the logs tonight. I also noticed that 3.3rc1 borks a working 11.10 3.0.15 lirc configuration after upgrade. No Output from irw nothing, no output from ir-keytable -t (which I have to run as root to work) seems strange.

---

### Post by mylittletom on 2012-02-22
> **rockorequin said:**
> There's a manual fix for the nvidia issue at [http://weltall.heliohost.org/wordpress/2012/01/20/linux-kernel-3-3-rc1-and-nvidia-drivers/](http://weltall.heliohost.org/wordpress/2012/01/20/linux-kernel-3-3-rc1-and-nvidia-drivers/).

I followed the second option and ran:

```
sudo cd /lib/modules/$(uname -r)/source/arch/x86/include
sudo cp generated/asm/unistd*.h ./asm

```and after this the nvidia module compiled fine.

Thank you rockerequin and other "Ubunteers"  !
It solved my case with kernel 3.3-rc4 !

---

### Post by shuttleworthwannabe on 2012-02-22
Hi guys--just butting in--any idea when the rc4 will become mainline kernel and be part of 12.04 LTS?? 

I rather wait till it is available in the regular updates and dev's have tested and worked with it a while.

Thanks
SwB

---

### Post by dino99 on 2012-02-23
> **shuttleworthwannabe said:**
> Hi guys--just butting in--any idea when the rc4 will become mainline kernel and be part of 12.04 LTS?? 

I rather wait till it is available in the regular updates and dev's have tested and worked with it a while.

Thanks
SwB

no need to wait, Precise will continue to use 3.2 kernel but with some patches from 3.3

---

### Post by VinDSL on 2012-02-23
> **dino99 said:**
> no need to wait [...]
Heh!  I'll never use Linux 3.2 again!  :D

Linux 3.3 is the best invention, since water...

---

### Post by teh603 on 2012-02-23
> **dino99 said:**
> no need to wait, Precise will continue to use 3.2 kernel but with some patches from 3.3Think they'll bring back the Dell Inspiron Duo ACPI patch? It was functional in early Precise despite picking the phantom power adapter instead of the real one, but now...

---

### Post by shuttleworthwannabe on 2012-02-23
> **VinDSL said:**
> Heh!  I'll never use Linux 3.2 again!  :D

Linux 3.3 is the best invention, since water...

How so VinDSL?

Faster? leaner? battery freindly and laptop friendly? Just curious, I am happy with 3.2 (with the minor adjustment to the parameters to extend my battery life and screen brightness adjustment).

---

### Post by VinDSL on 2012-02-23
> **shuttleworthwannabe said:**
> How so VinDSL?
Primarily...

[LIST=1]
[*]I use an older 32-bit computer (a former high-end gaming machine, circa 2005)
[*]Linux 3.3 uses less memory (I run 1GB Crucial Ballistix Tracers - every bit counts)
[*]Flash games, videos, et cetera run MUCH smoother under 3.3
[/LIST]

All the usual Ubu alpha 1 foibles are still there, but Linux 3.3 makes the whole package look n' feel better -- and, it's not my imagination, e.g. wishful thinking, on my part.  With all the problems I had during installation, I *expected* the worst.  LoL!

I've been trying to figure out WHY Linux 3.3 is working so good.

In the official rc4 release notes, it said something about them having fixed a long-standing floating point error problem.  All the problems that they listed, associated with the floating error problem, were present on this machine, for years -- and they're gone now.

Supposedly, these problems only affected certain, recently released processors... which begs the question: "If it only affects recently released high-end processors, why did they mention that the floating error problem has been plaguing them for years?"

My *theory* is, they knew about the floating point error for years, but it didn't become critical until recently -- and, the fix has been beneficial to a lot more machines than they realize.

Regardless, Linux 3.3-rc4 is working like a champ -- feels like a different machine -- and, I know it will only get better, so I'm rolling with it.  ;)

---

### Post by shuttleworthwannabe on 2012-02-24
@VinDSL--okay, convinced. So how do I install this on 12.04 LTS current build? I have an nividia system, so I am wary off things breaking because it does not compile the DKMS well. Any pointers on getting this working on my Dell Vostro 3700 Nvidia GForce 330m?
[If I am side  tracking, point me in the right direction and I will follow those instructions]

---

### Post by VinDSL on 2012-02-24
> **shuttleworthwannabe said:**
> @VinDSL--okay, convinced. So how do I install this on 12.04 LTS current build? I have an nividia system, so I am wary off things breaking because it does not compile the DKMS well. Any pointers on getting this working on my Dell Vostro 3700 Nvidia GForce 330m?
[If I am side  tracking, point me in the right direction and I will follow those instructions]
Okay, let's see if I can do this, without too much keyboarding...  :)


Here are my (personal) Tomboy notes:

> Download the Linux 3.3-rc4 .deb files

cd Downloads/Kernel

sudo dpkg -i *.deb

If nVidia module fails to build...

cd /usr/src/linux-headers-3.3.0-030300rc4-generic/arch/x86/include

sudo cp generated/asm/unistd*.h ./asm

Reinstall...


Also, I just responded to a PM, a few minutes ago (which I don't normally do -- sorry).  This is how I replied:

> What I did was:

[LIST]
[*]Install the rc4 kernel using the "sudo dpkg -i *.deb" technique (nVidia module build will fail)


[*]Perform the cp trick:
```
cd /usr/src/linux-headers-3.3.0-030300rc4-generic/arch/x86/include
sudo cp generated/asm/unistd*.h ./asm
```

[*]Then, immediately re-install the rc4 kernel using the "sudo dpkg -i *.deb" technique, again (this time nVidia module should compile)


[*]Reboot
[/LIST]


I don't know how familiar you are with installing kernels.  I do it all the time (sort of a hobby, turned fetish).  It's become about as routine as shaving my beard, or brushing my teeth.  I could install a kernel faster than it takes to type this message.  LoL!

Hopefully, you know which .deb files to download (for your PC), so I won't waste space here.

Personally, I download the .deb files to... ~/Downloads/Kernel (you can download them wherever YOU want).

Then, I install them using dpkg from CLI

Normally, that's all it takes, but... Linux 3.3 was a stinkerpot.  The nVidia module wouldn't compile.  And, it wasn't until recently that I read about the "cp" workaround.  That was the missing piece of the puzzle!

So, to recap, all I did was:

[LIST]
[*]Download and install the kernel .debs, like I've done hundreds of times.

[*]Let the nVidia build fail.

[*]Invoke the "CP" trick.

[*]Then install Linux 3.3 a second time
[/LIST]. 
Bingo!  nVidia module compiles.  And, you're off to the races!  ;)

Make sense?!?!?

---

### Post by bmbaker on 2012-02-24
well i tried following the instruction but no joy! not sure if it is because i am using the xorg-edgers ppa or because of the pae kernel!!

---

### Post by VinDSL on 2012-02-24
> **bmbaker said:**
> well i tried following the instruction but no joy! not sure if it is because i am using the xorg-edgers ppa or because of the pae kernel!!
I'm using the non-pae i386-generic mainline kernel:[INDENT][http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-rc4-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-rc4-precise/)[/INDENT]

And, nvidia-current 295.20, from the precise/restricted ppa.

If you use something else, you need to change the path in the "cp" trick.  ;)

---

### Post by shuttleworthwannabe on 2012-02-24
> **VinDSL said:**
> Okay, let's see if I can do this, without too much keyboarding...  :)


Here are my (personal) Tomboy notes:




Also, I just responded to a PM, a few minutes ago (which I don't normally do -- sorry).  This is how I replied:




I don't know how familiar you are with installing kernels.  I do it all the time (sort of a hobby, turned fetish).  It's become about as routine as shaving my beard, or brushing my teeth.  I could install a kernel faster than it takes to type this message.  LoL!

Hopefully, you know which .deb files to download (for your PC), so I won't waste space here.

Personally, I download the .deb files to... ~/Downloads/Kernel (you can download them wherever YOU want).

Then, I install them using dpkg from CLI

Normally, that's all it takes, but... Linux 3.3 was a stinkerpot.  The nVidia module wouldn't compile.  And, it wasn't until recently that I read about the "cp" workaround.  That was the missing piece of the puzzle!

So, to recap, all I did was:

[LIST]
[*]Download and install the kernel .debs, like I've done hundreds of times.

[*]Let the nVidia build fail.

[*]Invoke the "CP" trick.

[*]Then install Linux 3.3 a second time
[/LIST]. 
Bingo!  nVidia module compiles.  And, you're off to the races!  ;)

Make sense?!?!?

Makes perfect sense--will give it a try. Thanks much appreciated.

---

### Post by bmbaker on 2012-03-01
> **VinDSL said:**
> I'm using the non-pae i386-generic mainline kernel:[INDENT][http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-rc4-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-rc4-precise/)[/INDENT]

And, nvidia-current 295.20, from the precise/restricted ppa.

If you use something else, you need to change the path in the "cp" trick.  ;)

hmmm ya actually i did try that too but for some reason it failed!
i play some more on the wkend and see if i can get it wking :-) thanks though :-)

---

### Post by mylittletom on 2012-03-25
> **bmbaker said:**
> hmmm ya actually i did try that too but for some reason it failed!
i play some more on the wkend and see if i can get it wking :-) thanks though :-)


Like VinDSL did as "*shaving my beard*"  ,  I've just updated with the lastest official kernel version 3.3.0-999  even though my ubuntu is Natty , not Precise .

If someone is still interested in updating new kernel .  Here are my detailed steps (you can just do "copy and paste" )

1.  download  3 files from 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2012-03-21-precise/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/daily/2012-03-24-precise/")     
or 
     [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/daily/current/")      (then you have to edit the number in the following commands)
    
     I prefer the normal generic version over generic-pae.  The PAE version doesn't work on my laptop.

2.  "cd"   to your folder which contains these 3 files 

3.  then:

$ sudo dpkg -i linux-headers-3.3.0-999-generic_3.3.0-999.201203210406_i386.deb  linux-headers-3.3.0-999_3.3.0-999.201203210406_all.deb linux-image-3.3.0-999-generic_3.3.0-999.201203210406_i386.deb

4.  nVidia build will report fail with any version , then do this:

$ sudo cd /usr/src/linux-headers-3.3.0-999-generic/arch/x86/include
$ sudo cp generated/asm/unistd*.h ./asm

5.   "cd"   to your folder which contains these 3 files  as step 2 , then 

$ sudo dpkg -i  linux-headers-3.3.0-999-generic_3.3.0-999.201203210406_i386.deb 

6. At this time, you may see some old nVidia build failed, but the current version will be 'OK"  , then do the rest

$ sudo dpkg -i linux-headers-3.3.0-999_3.3.0-999.201203210406_all.deb  
$ sudo dpkg -i linux-image-3.3.0-999-generic_3.3.0-999.201203210406_i386.deb



Hope it works and enjoy the faster linux kernel (but longer booting time) !

---

### Post by Starks on 2012-03-25
Shouldn't Nvidia 295.33 should work with 3.3 out of the box?

> [LIST]
[*]Improved compatibility with recent Linux kernels.
[/LIST]

---

### Post by mylittletom on 2012-03-25
> **Starks said:**
> Shouldn't Nvidia 295.33 should work with 3.3 out of the box?

Oh ,  at last , Thank God They Here !

Thanks Starks , I updated nVidia without any pain !

---

### Post by VinDSL on 2012-03-26
> **Starks said:**
> Shouldn't Nvidia 295.33 should work with 3.3 out of the box?

> **mylittletom said:**
> Thanks Starks , I updated nVidia without any pain !
Sweet!  :D

nVidia module built just fine!  And, it survived a restart...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-25-mar-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-25-mar-2012-1.png")[/INDENT]

---

### Post by mylittletom on 2012-03-26
Hi "Ubunteers"

I believe that there are some problems with Wireless Connection & Bluetooth device with the current linux kernel 3.3 at dates from 2012-03-21 to 2012-03-25.

Then , I reinstalled the package at date of 2012-03-14.  So far , I have found no problem with this version.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2012-03-14-precise/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/daily/2012-03-14-precise/")

I'm not sure about the other versions from  2012-03-15  to  2012-03-20.

Does anyone confirm this ?

---

### Post by VinDSL on 2012-03-27
I tend to steer clear of daily mainline kernels.

I'm currently running (Linux 3.3 Precise): [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-precise/)

---

### Post by mylittletom on 2012-03-27
Thanks for the tip .

I'll avoid testing their buggy versions .

---

