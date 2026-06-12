---
title: "Kernel 2.6.33"
date: 2010-02-26
forum: Ubuntu Studio
---

### Post by Snocrash on 2010-02-26
Well... 2.6.33 was released a few days ago. I noticed some more real time stuff was added to the main tree and was wondering if anyone has tried it yet??. I am wondering if enough of the rt patch has been moved into it know to make it usable for recording????

Anyone know?????


Thanks,

-Sno

---

### Post by trulan on 2010-02-26
I've played with it but it's been in the context of experimenting with nvidia and nouveau drivers in the alpha 2 phase of Lucid Lynx.  Never got as far as attempting to start Jack with my Firepod.

The generic answer to the question, "Will it work for recording?" is, it depends on:
1. Your hardware, and
2. How you will be using it.

While I'm a big fan of RT kernels, and I think there's a benefit, especially of you're using a high-demand audio interface (like recording 16 tracks with two firepods ;) ), for basic recording you can almost always set your latencies a bit higher, with very good results.  Plus, I've seen reports of the generic kernel outperforming the rt kernel even on 2.6.31, with certain hardware.

One thing is for sure, not enough of RT stuff has moved in to the main kernel to satisfy the guys who code the RT patches.  There is an RT patch for 2.6.33 out as well.  (I tried to build it today, my first-ever attempt at rolling a kernel. It seemed to build and install properly but it refuses to boot.  Oh well...)

---

### Post by Snocrash on 2010-02-27
Thanks for the reply....

My hardware is pretty basic.....

Cheap Nvidia mobo and AMD X2 proc with 4G ram....
M-Audio 2496 sound card and Audio Buddy pre-amp for audio in and midi...
M-Audio keyrig 49 for a keyboard....
The rest is all software....Hydrogen, Q-Synth, Ardour, JACK, etc....

Works O.K. for solo/Duo stuff.....

Guess I will try patching 33 and rolling it today.....

Let you know how it goes.....




-Sno

---

### Post by trulan on 2010-02-27
Well, you can always test 2.6.33 generic from here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

I'm giving rolling it another shot as well, but I'll be the first to admit that I don't know what I'm doing.  Maybe I'll be able to learn something (which is my main purpose for doing it anyway.)  And maybe with a little luck I'll get it working. ;)

Edit:  Success!  I installed 2.6.33-rc8 generic and built the rt-patched kernel from there.  Running 2.6.33-rc8-rt2.  Testing with ffado..
I posted my findings over here:
[http://ubuntuforums.org/showthread.php?p=8890552#post8890552](http://ubuntuforums.org/showthread.php?p=8890552#post8890552)
It seemed more appropriate to put it in the Lucid Testing forum.

---

### Post by Snocrash on 2010-03-01
> **trulan said:**
> 
Edit:  Success!  I installed 2.6.33-rc8 generic and built the rt-patched kernel from there.  Running 2.6.33-rc8-rt2.  Testing with ffado..
I posted my findings over here:
[http://ubuntuforums.org/showthread.php?p=8890552#post8890552](http://ubuntuforums.org/showthread.php?p=8890552#post8890552)
It seemed more appropriate to put it in the Lucid Testing forum.

Hmmmmm... I downloaded the 33 source and rt4 patch from kernel.org. Followed the instructions here.. [http://www.nescivi.nl/?p=111]("http://www.nescivi.nl/?p=111")....except I did it all in /usr/src as root like I normally do. The kernel compiles fine. But make-kpkg fails at packaging with a version match issue...

----------------------------
====== making target debian/stamp/install/linux-image-2.6.33-rt4-sno1 [new prereqs: ]======
This is kernel package version 11.015.
echo "The UTS Release version in include/linux/version.h"; echo "	   \"\" "; echo "does not match current version:"; echo "	   \"2.6.33-rt4-sno1\" "; echo "Please correct this."; exit 2
The UTS Release version in include/linux/version.h
	   "" 
does not match current version:
	   "2.6.33-rt4-sno1" 
Please correct this.
make[1]: *** [debian/stamp/install/linux-image-2.6.33-rt4-sno1] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.33-rt4'
make: *** [kernel_image] Error 2
-----------------------------

Never ran into this one before.....

Anyone know how to fix this????

Thanks,


-Sno

---

### Post by Snocrash on 2010-03-01
I went poking around for answers and found this [_Bug Report_]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=561569")....

Seems they moved some of the header stuff around in 2.6.33 and karmic has not caught up with the new make-kpkg yet. They list a patch or two for 33 that should solve it as well. I may try that when I get home tomorrow (on the road). Or I may see if I can find/build the new make-kpkg.

Will let ya know.

-Sno

Edit: On further inspection, the patches seem to be for the deb kpkg system, not the kernel. One way or the other, I will see what I can do....

-Sno

---

### Post by Snocrash on 2010-03-08
Well.... It was a bit of a pain, but 33-rt4 is now compiled and running. I updated my kernel-package to 12.033 from debian. That one will compile the 2.6.33 kernel, but there was no initrd.img file and the installation of the kernel_image.deb file fails during post install configure. After further poking around, I found that the new kernel-package does not automatically put the initrd scripts in /etc/kernel so you have to copy them over from /usr/share/kernel-package/examples for it to build the initrd image. After that you need to edit your /etc/kernel-img.conf file and comment out the "update-grub" lines. With all that done, the kernel and headers build, install and configure fine. Then you just need to run "update-grub" manually to update it.

This kernel seems very quick and is running smoothly with JACK, Ardour, Hydrogen, qsynth, etc.....

I have not found anything that does not work for me yet. :)

On a side note, the NVIDIA 3D drivers would not build. That took even more poking around, but I hate having to re-boot between normal use and recording. I found a patch for the nvidia 190.53 drivers for the 2.6.33 kernel. But it dose not work for rt4. I applied that patch, ran a few diffs, and ended up extracting the driver package and modifying the nv-linux.h file by hand. It did compile and seems to be working fine.

As I said.... Bit of a pain, but it works... :guitar:


-Sno

---

