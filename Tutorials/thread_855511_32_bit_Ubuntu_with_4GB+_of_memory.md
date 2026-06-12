---
title: "32 bit Ubuntu with 4GB+ of memory"
date: 2008-07-10
forum: Tutorials
---

### Post by sdennie on 2008-07-10
**Overview**

This guide is to explain how Ubuntu handles 4 or more gigabytes of memory and the options you have for utilizing all your memory.

By default, the 32bit versions of Ubuntu support up to 4GB of memory however, in practice, if you have 4GB of memory, you will generally only see somewhere between 3GB and 3.5GB.  The reason for this is that various devices on your computer need large chunks of the memory address space to work properly and so the system maps them into the highest parts of memory. When that happens on a machine with 4GB of memory and a 32bit kernel, it limits the amount addressable physical memory.

The options you have for running Ubuntu with 4G+ of memory are:

**1) Use a 64bit version of Ubuntu**
If your machine supports it, the easiest way to make use of 4GB+ of memory on Ubuntu is to simply use a 64bit version of Ubuntu which can inherently handle [ large amounts of memory]("http://en.wikipedia.org/wiki/64-bit#Memory_limitations").  For some motherboards, you may have to enable a feature called "Map around memory hole" in the BIOS for this to work (it may be called something different depending on the BIOS however, it should be named something similar to this).

Pros:
- Requires no extra setup
- No inherent performance hit for using 4GB+ of RAM

Cons:
- Not supported on all hardware
- Not all software/drivers may be supported for 64bit versions of Ubuntu.  However, this is far less of an issue than it used to be and most users will have no problems whatsoever running 64bit.

**2) Use a PAE enabled kernel**
[PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension") is a way to allow a 32bit kernel to address up to 36bits of memory (64GB).  The kernel documentation says that there is a slight performance hit when using PAE however, in practice, you are not likely to notice any difference in performance.  The default Ubuntu kernel does not have PAE enabled however, there are two ways to get a PAE enabled kernel:

**2.1) Ubuntu server kernel**
[The Ubuntu server kernel]("http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel") has PAE enabled and can be installed by doing:

```

sudo apt-get install linux-server linux-headers-server linux-restricted-modules-server

```

After the server kernel has been installed, you can select it from the grub boot menu.

Pros:
- Easy to setup and maintain on an existing 32bit install
- Works on machines that cannot use a 64bit version of Ubuntu but support 4GB+ of RAM.

Cons:
- The server kernel is not optimized for desktop usage (see link above).  However, depending on how you use your machine you may not notice any difference.
- There can be issues with third party drivers and the server kernel (specifically, nvidia drivers).

**2.2) Build a PAE enabled kernel**
It's very easy to enable PAE in a custom compiled kernel.  From "make menuconfig", the option to enable it is:

```

-> Processor type and features
  -> High Memory Support
    -> 64GB

```

There are many guides to building a kernel for an Ubuntu machine:
- [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)
- [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)
- [http://ubuntuforums.org/showthread.php?t=618563](http://ubuntuforums.org/showthread.php?t=618563)
- [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) (from Ubuntu source)

Pros:
- Better desktop performance than the Ubuntu server kernel
- Building a custom kernel helps you learn about the system

Cons:
- Building a custom kernel can be difficult and time consuming.  
- You may have to manually install some drivers for your hardware.
- By not using an Ubuntu kernel, you become responsible for keeping your kernel up to date with security patches.

**3) Do nothing**
If your machine is not capable of running a 64bit version of Ubuntu, the performance of the server kernel isn't to your liking and you aren't willing to build a custom kernel, your last option is to simply do nothing.  This will limit you to around 3GB to 3.5GB of memory however, it shouldn't cause any system instability or problems.

Comments/questions/suggestions welcome.

---

### Post by atlas95 on 2008-07-11
Thanks man !

---

### Post by forger on 2008-07-11
this is a keeper :) great information!
It would be good to add a link to the memory limitations to 64-bit Ubuntu too:
[http://en.wikipedia.org/wiki/64-bit#Memory_limitations](http://en.wikipedia.org/wiki/64-bit#Memory_limitations)

---

### Post by sdennie on 2008-07-12
> **forger said:**
> this is a keeper :) great information!
It would be good to add a link to the memory limitations to 64-bit Ubuntu too:
[http://en.wikipedia.org/wiki/64-bit#Memory_limitations](http://en.wikipedia.org/wiki/64-bit#Memory_limitations)

Updated the 64bit section with this link.

---

### Post by yct on 2008-07-24
Went with the 2.1 option - server kernel - works like a *charm* - maybe even better than the desktop one.
Thanks! (EDIT: nope, problems with compiz (the eye candy))

(had to do 'apt-get update' cos dependencies were b0rken)

Default 32-bit Ubuntu should really have PAE enabled - 64-bit version really makes sense only in a very few cases, actually in only one case: when you need to run a *single* application that needs more than 3 GB memory.
The catch is, that 64-bit applications also take more memory than 32-bit apps with the same data/code set (in the case of Java it's two times more - means 1gb 32bit app == 2gb 64bit app), so you may need to start with 8 GB ram for the 32 to 64 bit upgrade to make any sense.

---

### Post by gurkburk on 2008-07-24
Well im getting a new computer soon (tossing stationary+laptop for ûber laptop) and thinking about getting 6-8GB of ram (I wanto run 1-2 OS's in VMWARE from time to time, for experimental purposes.).
Now, I dont wanto sit there without security patches and whatnot.. is there any new version of ubuntu around the corner (say 3-4 months?) that will support this? 
Shouldnt be so hard, if we can just build it in ourself, and they even have it enabled by default in server-version?

---

### Post by sdennie on 2008-07-24
> **gurkburk said:**
> Well im getting a new computer soon (tossing stationary+laptop for ûber laptop) and thinking about getting 6-8GB of ram (I wanto run 1-2 OS's in VMWARE from time to time, for experimental purposes.).
Now, I dont wanto sit there without security patches and whatnot.. is there any new version of ubuntu around the corner (say 3-4 months?) that will support this? 
Shouldnt be so hard, if we can just build it in ourself, and they even have it enabled by default in server-version?

The -generic kernel in Intrepid doesn't have PAE enabled and I haven't seen any new kernel types added so, no, I don't think there are any plans to have a desktop tuned PAE kernel for the near future.  Depending on how you use the machine, the -server kernel might work just fine for you though.

---

### Post by yct on 2008-07-25
I've edited my post above, because later in the day Compiz had crashed on me.
However right after the edit, I did notice that I'm now actuallly running on the server kernel again (as it's the default in my grub), and I'm still fine. Besides the server kernel, I've also installed Vmware Server, so that might've been the problem too.
I will let you know if I'll be having more probs with server kernel on the desktop.

---

### Post by mbsullivan on 2008-07-27
First off, thanks for a great tutorial!

One comment...

> 
- By not using an Ubuntu kernel, you become responsible for keeping your kernel up to date with security patches.

I believe you can get (and modify) the kernel source with Ubuntu patches through apt. For example:

```
sudo aptitude install linux-source-2.6.26
```

Will get the patched code and place it in /usr/src/. You can then modify this kernel to enable PAE in order to get 4+ GB of memory support.

Mike

---

### Post by sdennie on 2008-07-27
> **mbsullivan said:**
> First off, thanks for a great tutorial!

One comment...



I believe you can get (and modify) the kernel source with Ubuntu patches through apt. For example:

```
sudo aptitude install linux-source-2.6.26
```

Will get the patched code and place it in /usr/src/. You can then modify this kernel to enable PAE in order to get 4+ GB of memory support.

Mike

Yes, you can use the Ubuntu source to build a PAE kernel.  However, it's still not completely automatic in that when the kernel source changes it will still be up to the user to rebuild the new kernel source.  I'll update the first post with a link to point to a tutorial on how to build a kernel from the Ubuntu source.

---

### Post by yct on 2008-07-30
Hi, please vote for this idea to have a PAE enabled kernel as an option in further releases of Ubuntu:
[http://brainstorm.ubuntu.com/idea/11653/](http://brainstorm.ubuntu.com/idea/11653/)

---

### Post by tirosa on 2008-08-14
>2.1) Ubuntu server kernel
>The Ubuntu server kernel has PAE enabled and can be installed by >doing:

>Code:

>sudo apt-get install linux-server linux-headers-server linux- >restricted-modules-server
>
>After the server kernel has been installed, you can select it >from the grub boot menu.

hi thx for those informations just to be sur can I do the kernel server install on top of a desktop version ?

BR

---

### Post by sdennie on 2008-08-14
> **tirosa said:**
> >2.1) Ubuntu server kernel
>The Ubuntu server kernel has PAE enabled and can be installed by >doing:

>Code:

>sudo apt-get install linux-server linux-headers-server linux- >restricted-modules-server
>
>After the server kernel has been installed, you can select it >from the grub boot menu.

hi thx for those informations just to be sur can I do the kernel server install on top of a desktop version ?

BR

Yes, there is no problem installing the server kernel with the desktop version of Ubuntu.

---

### Post by naszaklasa on 2008-11-29
I am getting this error:

desktop:~$ sudo apt-get install linux-server linux-headers-server linux-restricted-modules-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-restricted-modules-server


Also, I am on 8.10 desktop, uname -a is desktop 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

---

### Post by jenkinbr on 2008-12-09
> **yct said:**
> Hi, please vote for this idea to have a PAE enabled kernel as an option in further releases of Ubuntu:
[http://brainstorm.ubuntu.com/idea/11653/](http://brainstorm.ubuntu.com/idea/11653/)
Wow, the Idea poster in that link sure started a war.

Anyways, I had always assumed that 3-3.5GB was the max for 32bit.  Never knew this...

EDIT: btw, why am I unable to thank vom (or anyone in this thread)?

---

### Post by yct on 2008-12-11
> **jenkinbr said:**
> Wow, the Idea poster in that link sure started a war.

Anyways, I had always assumed that 3-3.5GB was the max for 32bit.  Never knew this...

EDIT: btw, why am I unable to thank vom (or anyone in this thread)?

wow, I considered that cause lost and did not come back to that page anymore:)

I have solved it by buying 8 GB ram (after Gigabyte suddenly updated the specs for my mainboard from 4 to 8 GB - probably a courtesy of AMD CPU built-in DDR controllers, and now I'm running quite happily on 64-bit (as far as the horrible 2D support of ATI binary driver goes).
I'm also running the 64-bit Flash (the alpha version), and it's very good - but that is just very recent development.

That said, if I could not stuff my mainboard with 8 GB ram, I would have to go PAE with other distro, or own compiled kernel (or a new mainboard).

---

### Post by lukjad on 2008-12-16
Hey, thanks. I really am learning a lot. ;)

---

### Post by jamesisin on 2008-12-28
I am trying option 2.1 (adding the server kernel).  Here is my output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-restricted-modules-server
```

Is that normal or is something amiss?

(I am running 8.10.)

---

### Post by MusicMastaMike on 2008-12-29
I'm runnning 32 bit Ubuntu 8.04 with a Core Duo processor (32 bit) and 4 GB of memory.  I installed and am running the server kernel, but *free* is still showing the same amount of memory as the generic kernel, ~3.2 GB.  Ideas?

---

### Post by Cracauer on 2008-12-29
PAE is really not that much slower.

Yes, (useless) artificial memory bandwidth tests suffer a little, but for real-world applications there is just a random +- 1%:

[http://www.cons.org/cracauer/crabench/pae.user.html](http://www.cons.org/cracauer/crabench/pae.user.html)

```

ummary of results
------------------

User CPU speed relative to Opteron DC 2.60 GHz, 2x 216 MHz 2T 3-4-4-8 -5B D 4096 MB, Via A8V-E SE [2 CPUs]

Opteron DC 2.60 GHz, 2x 216 MHz 2T 3-4-4-8 -5B D 4096 MB, Via A8V-E SE [2 CPUs]:
            Normal C compilation:  100.6 ( 100.2)
                 C++ compilation:   99.9 (  99.4)
               Linux compilation:  100.6 ( 100.1)
                            gzip:  100.1 (  99.6)
                            Lisp:   99.5 (  99.0)
                          python:   99.9 (  99.4)
                          php/bs:    0.0 (   0.0)
              High quality mpeg4:  100.5 ( 100.0)
          Constant bitrate mjpeg:  101.3 ( 100.8)
                      Fast mjpeg:  101.9 ( 101.4)
                         SuperPi:    0.0 (   0.0)
                         Overall:  100.5

```

Pretty chart in link above.

---

### Post by jamesisin on 2008-12-29
> **jamesisin said:**
> I am trying option 2.1 (adding the server kernel).  Here is my output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-restricted-modules-server
```

Is that normal or is something amiss?

(I am running 8.10.)

Answer?  Anybody?

---

### Post by SlonUA on 2008-12-30
After installing and booting from server image

type
sudo apt-get install linux-restricted-modules-$(uname -r)

---

### Post by aspenhawk on 2008-12-31
I have a Toshiba P105 S9722 running Ubuntu 8.10 Intrepid.  I have 4GB installed, however Ubuntu only sees the following.  total mem is 3015--used 1037--free 1978--shared 0--buffers 33--cashed 445---/+ buffers/cashe--used 558--free 2456--Swap 0. I have tried a number of procedures listed on the forum to no avail.  I have the latest bios updates and have read several articles that say the transition processors, such as the T7200 with the 945pm express chipset cannot map above 4gb of memory. Any other solutions out there???????

---

### Post by sdennie on 2008-12-31
> **aspenhawk said:**
> I have a Toshiba P105 S9722 running Ubuntu 8.10 Intrepid.  I have 4GB installed, however Ubuntu only sees the following.  total mem is 3015--used 1037--free 1978--shared 0--buffers 33--cashed 445---/+ buffers/cashe--used 558--free 2456--Swap 0. I have tried a number of procedures listed on the forum to no avail.  I have the latest bios updates and have read several articles that say the transition processors, such as the T7200 with the 945pm express chipset cannot map above 4gb of memory. Any other solutions out there???????

My last laptop was a P105 series.  Apart from various other problems, it wouldn't even boot with more than 2G of RAM and with more than 2GB the BIOS would only report 3GB.  I would check your BIOS and, if it's only reporting 3GB, then what you are seeing is normal.

---

### Post by Cracauer on 2008-12-31
> **aspenhawk said:**
> I have a Toshiba P105 S9722 running Ubuntu 8.10 Intrepid.  I have 4GB installed, however Ubuntu only sees the following.  total mem is 3015--used 1037--free 1978--shared 0--buffers 33--cashed 445---/+ buffers/cashe--used 558--free 2456--Swap 0. I have tried a number of procedures listed on the forum to no avail.  I have the latest bios updates and have read several articles that say the transition processors, such as the T7200 with the 945pm express chipset cannot map above 4gb of memory. Any other solutions out there???????

The cheap Intel chipsets like the 945 don't support the required remapping, sorry.

---

### Post by jaygo on 2009-01-02
Thanks for the walkthrough. I deactivated the restricted nvidia driver from the hardware driver GUI before adding the server kernels, then reactivated it after a reboot. All is peachy now with 6GB RAM + nvidia driver. I didn't try installing the restricted modules you list.

+1 for releasing a PAE-enabled desktop (generic) Ubuntu kernel. Like he said, hit up the site and vote for it so we don't have to do so much legwork. Took me about two hours total, including 30 min to tweak LILO to boot from a new kernel, 45 min to reconfigure xorg.conf, all of which can be avoided once they release a PAE kernel.

---

### Post by diaa on 2009-01-26
> **Cracauer said:**
> PAE is really not that much slower.

Yes, (useless) artificial memory bandwidth tests suffer a little, but for real-world applications there is just a random +- 1%:

[http://www.cons.org/cracauer/crabench/pae.user.html](http://www.cons.org/cracauer/crabench/pae.user.html)



Pretty useful, thanks.

For me, I give up the 2-3% for the extra 1G of memory(or more), I was suspicious about the performance of the kernel server in a Desktop environment because of [its tuning]("http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel") not because of PAE's performance hit, does it work well with games, downloads, movies, everything.
I couldn't find a definitive answer so I installed the server kernel to find out, all I'm going to lose is a couple of hours and it's doing well up till now, I will follow up with updates if any.

---

### Post by sdennie on 2009-01-26
> **diaa said:**
> Pretty useful, thanks.

For me, I give up the 2-3% for the extra 1G of memory(or more), I was suspicious about the performance of the kernel server in a Desktop environment because of [its tuning]("http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel") not because of PAE's performance hit, does it work well with games, downloads, movies, everything.
I couldn't find a definitive answer so I installed the server kernel to find out, all I'm going to lose is a couple of hours and it's doing well up till now, I will follow up with updates if any.

The only difference you are really likely to notice is in games.  Where you may or may not see a performance hit.  Most people probably won't notice the difference between the -server and -generic kernel.

---

### Post by jamesisin on 2009-01-26
> **SlonUA said:**
> After installing and booting from server image

type
sudo apt-get install linux-restricted-modules-$(uname -r)

I'm afraid that the error message I received above in some way prevented me from downloading/installing the server kernel.

---

### Post by OnsoSan on 2009-01-26
Using the option 2.1, with minor modification added the kernel version ***linux-restricted-modules-[B]2.6.27-9**-server*[/B] everything works fine for me, including compiz
mem: 6076 MiB

Thank you

---

### Post by Luk_Deisler on 2009-01-29
I've got Ubuntu x64 and 4GB ram, but I can see just 3GB

```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          2952       2017        934          0        202        712
-/+ buffers/cache:       1102       1849
Swap:         5883          0       588
```


In Vista x64 I can see all 4GB, so where the hell is the problem?

---

### Post by SlonUA on 2009-05-29
[http://ubuntuforums.org/showthread.php?p=7369718](http://ubuntuforums.org/showthread.php?p=7369718)

---

### Post by N1c0_ds on 2009-06-01
"Do nothing" does it for me. With Ubuntu's 200-500mb of RAM usage, I'll never reach the 3GB limit Vista can barely play with. You might aswell want to install from a minimal version instead, as the performance will always be noticeable.

---

### Post by guppygould on 2009-07-20
Hey all! Sorry for the almighty bump but I think it'll be better than starting a new topic. I just changed to the server kernel on my 32-Bit install and the was a bit of a drop in performance. How can I change it back?

Thanks,

-Leo

---

### Post by guppygould on 2009-07-20
Bump.

---

### Post by Cracauer on 2009-07-20
> **guppygould said:**
> Hey all! Sorry for the almighty bump but I think it'll be better than starting a new topic. I just changed to the server kernel on my 32-Bit install and the was a bit of a drop in performance. How can I change it back?


How did you measure that drop in performance?

---

### Post by guppygould on 2009-07-20
> **Cracauer said:**
> How did you measure that drop in performance?

Well, I didn't 'measure' it as such but it is noticeably slower to load applications, especially when using multiple apps.

---

### Post by Cracauer on 2009-07-20
> **guppygould said:**
> Well, I didn't 'measure' it as such but it is noticeably slower to load applications, especially when using multiple apps.

There's no way that you can interactively notice the slowdown from PAE. It is much too small for this, in fact it pretty is only visible in useless memory bandwidth benchmarks. And for interactive work like GUI applications the very noticeable speedup from having more memory would be much bigger.

Did you try rebooting into the old kernel to see whether it actually reverts to "feel fast"?

---

### Post by guppygould on 2009-07-20
Yes I'm posting from the standard kernel and it is definately faster. I suppose I don't need to remove the server kernel from my laptop in case I ever needed to use the full 4GB of RAM. How can I set it so that it loads the standard kernel by default?

---

### Post by Cracauer on 2009-07-20
> **guppygould said:**
> Yes I'm posting from the standard kernel and it is definately faster. I suppose I don't need to remove the server kernel from my laptop in case I ever needed to use the full 4GB of RAM. How can I set it so that it loads the standard kernel by default?

And you are sure you got more memory with the new (slower) kernel according to `free`?

Can you do any form of hard timing that would give us some numbers?

---

### Post by guppygould on 2009-07-20
> **Cracauer said:**
> And you are sure you got more memory with the new (slower) kernel according to `free`?

Can you do any form of hard timing that would give us some numbers?

Yeah I have 4GB on the new one. I've just timed from opening Firefox in each one. In the standard kernel it's approximately 0.25 seconds whereas in the server kernel it's about 0.4 seconds. -Those are just times I got using my mobile phone so obviously there will be some error in there. If you have a better way of comparing them I'm open to suggestions.

---

### Post by Cracauer on 2009-07-20
> **guppygould said:**
> Yeah I have 4GB on the new one. I've just timed from opening Firefox in each one. In the standard kernel it's approximately 0.25 seconds whereas in the server kernel it's about 0.4 seconds. -Those are just times I got using my mobile phone so obviously there will be some error in there. If you have a better way of comparing them I'm open to suggestions.

No, that's convincing. But there is no way that this is caused by PAE, something else is different, possible some disk driver options, cache defaults or the like.

At this point I would build my own kernel starting from the desktop kernel you like and only activating PAE.

If you want to debug this, post the dmesg from both kernels.

---

### Post by SlonUA on 2009-07-20
> **guppygould said:**
> Yeah I have 4GB on the new one. I've just timed from opening Firefox in each one. In the standard kernel it's approximately 0.25 seconds whereas in the server kernel it's about 0.4 seconds. -Those are just times I got using my mobile phone so obviously there will be some error in there. If you have a better way of comparing them I'm open to suggestions.

Could U post following information:

1. > sudo dmidecode -t memory
2. > free
3. > sudo dkms status

Also,do U have **compiz** enabled !?!

---

### Post by Paulmoore on 2009-07-24
Hmmm...

I've followed all options. Recompiled a new kernel, downloaded and installed the server kernel. Even downloaded, compiled and installed from Kernel.org. 

free -m still shows:
```
             total       used       free     shared    buffers     cached
Mem:          3213       3115         98          0         20       2610
-/+ buffers/cache:        483       2729
Swap:        15257          1      15255

```

I've even modified the grub install as per [these]("http://www.howtoforge.com/make-your-xen-pae-kernel-work-with-more-than-4gb-ram-debian-etch-grub") instrustions.

Mobo: ASRock P45TS-R
Mem: 4x2gig sticks DDR2 1066


What else could be going wrong?

---

### Post by SlonUA on 2009-07-25
> **Paulmoore said:**
> Hmmm...

I've followed all options. Recompiled a new kernel, downloaded and installed the server kernel. Even downloaded, compiled and installed from Kernel.org. 

free -m still shows:
```
             total       used       free     shared    buffers     cached
Mem:          3213       3115         98          0         20       2610
-/+ buffers/cache:        483       2729
Swap:        15257          1      15255

```

I've even modified the grub install as per [these]("http://www.howtoforge.com/make-your-xen-pae-kernel-work-with-more-than-4gb-ram-debian-etch-grub") instrustions.

Mobo: ASRock P45TS-R
Mem: 4x2gig sticks DDR2 1066


What else could be going wrong?

Man .. R U kidding ...

[I]How To Make Your Xen-PAE Kernel Work With More Than 4GB RAM (**[COLOR="red"]Debian Etch With GRUB[/COLOR]**)
Version 1.0 
Author: Falko Timme <ft [at] falkotimme [dot] com> 
Last edited **[COLOR="Red"]12/13/2007[/COLOR]** [/I]

U must just install 

sudo apt-get install linux-server linux-headers-server linux-restricted-modules-server

That's another for Ubuntu

---

### Post by Paulmoore on 2009-07-25
> **SlonUA said:**
> Man .. R U kidding ...

[I]How To Make Your Xen-PAE Kernel Work With More Than 4GB RAM (**[COLOR="red"]Debian Etch With GRUB[/COLOR]**)
Version 1.0 
Author: Falko Timme <ft [at] falkotimme [dot] com> 
Last edited **[COLOR="Red"]12/13/2007[/COLOR]** [/I]

U must just install 

sudo apt-get install linux-server linux-headers-server linux-restricted-modules-server

That's another for Ubuntu

Not kidding at all. I have tried all of those options separately, as I have stated, and none of them have worked. However, asking me to do the same thing again and expecting a different outcome is quite funny.

---

### Post by SlonUA on 2009-07-25
> **Paulmoore said:**
> Not kidding at all. I have tried all of those options separately, as I have stated, and none of them have worked. However, asking me to do the same thing again and expecting a different outcome is quite funny.

So, I see U R online. U can contact to me by ICQ:74707158 or Skype:slonskype or GTalk:skonua@gmail.com directly.
BTW, about kidding .. I just mean that U not need to compile kernel =)).

EDIT: 
>> Swap:        15257          1      15255
U have 15 Gb for SWAP !?!?

---

### Post by Cracauer on 2009-07-26
> **Paulmoore said:**
> Hmmm...

I've followed all options. Recompiled a new kernel, downloaded and installed the server kernel. Even downloaded, compiled and installed from Kernel.org. 

free -m still shows:
```
             total       used       free     shared    buffers     cached
Mem:          3213       3115         98          0         20       2610
-/+ buffers/cache:        483       2729
Swap:        15257          1      15255

```

I've even modified the grub install as per [these]("http://www.howtoforge.com/make-your-xen-pae-kernel-work-with-more-than-4gb-ram-debian-etch-grub") instrustions.

Mobo: ASRock P45TS-R
Mem: 4x2gig sticks DDR2 1066


What else could be going wrong?

What kernel options did you activate?

I don't have any 32 bit Linux left, but according to my file archive this is what you need to get PAE:

```

# CONFIG_NOHIGHMEM is not set
# CONFIG_HIGHMEM4G is not set
CONFIG_HIGHMEM64G=y

```

If you have continued trouble please make your kernel .config available.

---

### Post by HeirPixel on 2009-08-23
I've tried solution 2.1 and booted with the server kernel (2.6.28-15-server) and I'm still not getting more than 3 gigs.
```

$ free -m
             total       used       free     shared    buffers     cached
Mem:          3015        852       2162          0         41        254
-/+ buffers/cache:        555       2459
Swap:         2996          0       2996

```

My BIOS sees all 4 gigs as 2048 * 2 = 4096. If my BIOS sees it but the server kernel doesn't, what can I do to get the rest...? :confused:

---

### Post by sdennie on 2009-08-23
> **HeirPixel said:**
> I've tried solution 2.1 and booted with the server kernel (2.6.28-15-server) and I'm still not getting more than 3 gigs.
```

$ free -m
             total       used       free     shared    buffers     cached
Mem:          3015        852       2162          0         41        254
-/+ buffers/cache:        555       2459
Swap:         2996          0       2996

```

My BIOS sees all 4 gigs as 2048 * 2 = 4096. If my BIOS sees it but the server kernel doesn't, what can I do to get the rest...? :confused:

You may need to set something in the BIOS to allow this to work.  Usually it's called something like, "Map around memory hole".

---

### Post by Cracauer on 2009-08-24
> **HeirPixel said:**
> I've tried solution 2.1 and booted with the server kernel (2.6.28-15-server) and I'm still not getting more than 3 gigs.
```

$ free -m
             total       used       free     shared    buffers     cached
Mem:          3015        852       2162          0         41        254
-/+ buffers/cache:        555       2459
Swap:         2996          0       2996

```

My BIOS sees all 4 gigs as 2048 * 2 = 4096. If my BIOS sees it but the server kernel doesn't, what can I do to get the rest...? :confused:

You need the remapping of the memory from 3-4 GB to 4-5 GB. That remapping should be in the BIOS but it can be named pretty much anything. If you have one of the cheapo Intel chipsets there will be none. And even if the chipset does it you can have bad luck that the mainboard vendor didn't put it into the BIOS.

---

### Post by tuxxy on 2009-08-24
My advice go 64-bit :D that way you can run 4GB+ and we all will do one day hehe

---

### Post by Cracauer on 2009-08-24
> **tuxxy said:**
> My advice go 64-bit :D that way you can run 4GB+ and we all will do one day hehe

If he has 4 GB RAM installed and does not activate the remapping then he will get his 3.0-3.2 GB with the 64 bit kernel, too.

---

### Post by HeirPixel on 2009-08-25
> **Cracauer said:**
> If you have one of the cheapo Intel chipsets there will be none.
Ah, nail on the head there. Too bad I can't replace it with coreboot :(

---

### Post by Cracauer on 2009-08-25
> **HeirPixel said:**
> Ah, nail on the head there. Too bad I can't replace it with coreboot :(

It is a chipset, not a BIOS, limitation in the cheaper Intel chipsets. Coreboot won't help.

---

### Post by yakupm on 2009-11-20
**2) Use a PAE enabled kernel**
[PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension") is a way to allow a 32bit kernel to address up to 36bits of memory (64GB).  The kernel documentation says that there is a slight performance hit when using PAE however, in practice, you are not likely to notice any difference in performance.  The default Ubuntu kernel does not have PAE enabled however, there are two ways to get a PAE enabled kernel:

**2.1) Ubuntu server kernel**
[The Ubuntu server kernel]("http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel") has PAE enabled and can be installed by doing:

```

sudo apt-get install linux-server linux-headers-server linux-restricted-modules-server

```After the server kernel has been installed, you can select it from the grub boot menu.

Pros:
- Easy to setup and maintain on an existing 32bit install
- Works on machines that cannot use a 64bit version of Ubuntu but support 4GB+ of RAM.

Cons:
- The server kernel is not optimized for desktop usage (see link above).  However, depending on how you use your machine you may not notice any difference.
- There can be issues with third party drivers and the server kernel (specifically, nvidia drivers).

Thanks for the guide, sdennie.  I used step 2 modified for **Ubuntu 9.10**, using synaptic to install linux-server linux-headers-server only.  Works well and my 4 GB is now accurately reported by top (was 3 GB earlier) :D.  Note that ubuntu 9.04 did not have that problem.

---

### Post by bdoe on 2010-01-09
> **sdennie said:**
> **2.2) Build a PAE enabled kernel**
It's very easy to enable PAE in a custom compiled kernel.  From "make menuconfig", the option to enable it is:

```

-> Processor type and features
  -> High Memory Support
    -> 64GB

```There are many guides to building a kernel for an Ubuntu machine:
- [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)
- [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)
- [http://ubuntuforums.org/showthread.php?t=618563](http://ubuntuforums.org/showthread.php?t=618563)
- [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) (from Ubuntu source)

Pros:
- Better desktop performance than the Ubuntu server kernel
- Building a custom kernel helps you learn about the system

Cons:
- Building a custom kernel can be difficult and time consuming.  
- You may have to manually install some drivers for your hardware.
- By not using an Ubuntu kernel, you become responsible for keeping your kernel up to date with security patches.
Looking in Synaptic, I can see that PAE kernels are now available without the need to build one. So, here's my question:

I am currently running Ubuntu 9.10 Karmic with the 32-bit generic kernels. How do I install and switch over to the PAE kernel and remove the generic kernels?

I *assume* it is as simple as running:```

sudo apt-get install linux-generic-pae linux-headers-generic-pae
```
then booting into the new kernel from GRUB, and then removing the non-PAE kernel stuff, right?

Is this right? Or am I putting myself on the road to borking my system?

---

### Post by SlonUA on 2010-01-11
correct ;)

---

### Post by speedwell68 on 2010-03-17
Yesterday I upgraded my RAM from 2GB to 4GB.  My existing install of Karmic 9.10 i386 would only recognise 3.1 GB of the 4GB available.  So I decided to give 64 bit a try.  TBH I found 64 bit to be a right royal PITA so I decided to go back to 32 bit and try and add the PAE kernel myself.  When I reinstalled 32 bit I discovered that it installed the PAE kernel by default.  I suppose it recognises that my machine has 4GB already installed and installs the PAE kernel.

---

### Post by alexandrius on 2010-04-22
> **speedwell68 said:**
> Yesterday I upgraded my RAM from 2GB to 4GB.  My existing install of Karmic 9.10 i386 would only recognise 3.1 GB of the 4GB available.  So I decided to give 64 bit a try.  TBH I found 64 bit to be a right royal PITA so I decided to go back to 32 bit and try and add the PAE kernel myself.  When I reinstalled 32 bit I discovered that it installed the PAE kernel by default.  I suppose it recognises that my machine has 4GB already installed and installs the PAE kernel.

Ubuntu Gurus please answer this guy i'm also interested
EDIT: Recently i've found this article [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE) and it says that installing from DVD will automatically detect if there's more than 3 gbs of ram and install the PAE enabled kernel

---

### Post by moonport on 2013-03-25
Great and usefull info. Thanks.

---

### Post by oldfred on 2013-03-25
Old thread closed.

---

