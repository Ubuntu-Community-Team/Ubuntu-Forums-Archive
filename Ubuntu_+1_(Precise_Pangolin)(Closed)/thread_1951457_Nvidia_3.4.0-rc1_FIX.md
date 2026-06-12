---
title: "Nvidia 3.4.0-rc1 FIX"
date: 2012-04-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Bobhuber on 2012-04-02
Haven't tried it yet but heres the latest fix to install the nvidia drivers on the newest 3.4.0-rc1  Kernel.
[http://weltall.heliohost.org/wordpress/2012/04/01/3-4-0-rc1-and-nvidia-drivers/](http://weltall.heliohost.org/wordpress/2012/04/01/3-4-0-rc1-and-nvidia-drivers/)

Edit > I can't get it to work. Anyone else try ??

---

### Post by drbcladd on 2012-04-02
Make the two recommended changes in source directory, not the build directory. Rather than 

/var/lib/dkms/nvidia-current/295.33/build/nv-linux.h

make the change in 

/var/lib/dkms/nvidia-current/295.33/source/nv-linux.h

That's where the files are copied FROM at the beginning of the build process. The build directory is actually deleted and recreated at the beginning of the dkms operation.

I can still install for 3.2.0 kernels, too.

---

### Post by Bobhuber on 2012-04-02
> **drbcladd said:**
> Make the two recommended changes in source directory, not the build directory. Rather than 

/var/lib/dkms/nvidia-current/295.33/build/nv-linux.h

make the change in 

/var/lib/dkms/nvidia-current/295.33/source/nv-linux.h

That's where the files are copied FROM at the beginning of the build process. The build directory is actually deleted and recreated at the beginning of the dkms operation.

I can still install for 3.2.0 kernels, too.
I'm using kpkg to compile the  kernel. The source and build directories are the same and  are referenced with symlinks in /lib/modules. I'm not using nvidia-current. I'm using the nvidia.run file from there site and installing it manually. There is no nv-linux.h file on my computer after compiling the kernel. I've had no problem using the last patch for the 3.3 kernel and am running the 3.3.1 right now. What am I missing here ?
Appreciate the help.

---

### Post by Bobhuber on 2012-04-03
> **Bobhuber said:**
> Haven't tried it yet but heres the latest fix to install the nvidia drivers on the newest 3.4.0-rc1  Kernel.
[http://weltall.heliohost.org/wordpress/2012/04/01/3-4-0-rc1-and-nvidia-drivers/](http://weltall.heliohost.org/wordpress/2012/04/01/3-4-0-rc1-and-nvidia-drivers/)

Edit > I can't get it to work. Anyone else try ??
Ok I got it to work by doing a bit of research on this fellows original post with the file copy trick for the 3.3 kernel. If your using a driver earlier than 295.33 (I'm using 285.05.09 because of compatibility problems with my card) you need to do the following for the 3.4.0-rc1 kernel . If your using the 295.33 drivers you should be able to skip Step 1.

Compile the kernel .
Change to the source directory and apply the original fix for the 3.3 kernel.

STEP 1
```
cd <sourcedirectory>/arch/x86/include/
cp generated/asm/unistd*.h ./asm/
```THEN RUN the script found in the above post as part of the nvidia install.Make sure both files are marked as executable.

STEP 2
```
sudo ./nvidiafixandrun.sh ./<nvidiarunfile.run> <options>
```The files this fellow mentions in the fix are actually a part of the extracted nvidia.run file and not a part of the source files or which had me going for a while.
Hope this helps someone else.

---

### Post by paul_in_london on 2012-04-08
This didn't work at all for me - kept getting an almost instant kernel panic when I tried to boot 3.4.0-rc1.

Better news is that 3.4.0-rc2 is now available:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-rc2-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-rc2-precise/)

and I was able to install and boot that without a hitch. No work-arounds needed. This is 64 bit with nvidia-current 295.33.

```
paul@precise-64:~$ uname -a
Linux precise-64 3.4.0-030400rc2-generic #201204072235 SMP Sun Apr 8 02:36:11 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by VinDSL on 2012-04-08
> **paul_in_london said:**
> This didn't work at all for me - kept getting an almost instant kernel panic when I tried to boot 3.4.0-rc1.

Better news is that 3.4.0-rc2 is now available:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-rc2-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-rc2-precise/)

and I was able to install and boot that without a hitch. No work-arounds needed. This is 64 bit with nvidia-current 295.33.
Dittos!

Except, I'm running 32-bit pae...  ;)

```
Linux Zuul 3.4.0-030400rc2-generic-pae #201204072235 SMP Sun Apr 8 02:50:00 UTC 2012 i686 i686 i386 GNU/Linux

```

---

### Post by paul_in_london on 2012-04-08
> **VinDSL said:**
> Dittos!

Except, I'm running 32-bit pae...  ;)

```
Linux Zuul 3.4.0-030400rc2-generic-pae #201204072235 SMP Sun Apr 8 02:50:00 UTC 2012 i686 i686 i386 GNU/Linux

```

Hi Vin,

Nice one. Yeah, even with all the OP's steps it was no-go for me so I had my fingers crossed when I saw that 3.4.0-rc2 had turned up!

Cheers,

Paul

---

### Post by xebian on 2012-04-08
> **paul_in_london said:**
> Hi Vin,

Nice one. Yeah, even with all the OP's steps it was no-go for me so I had my fingers crossed when I saw that 3.4.0-rc2 had turned up!

Cheers,

Paul

It works like a charm for me.  rc2 still needs this fix btw.

---

### Post by VinDSL on 2012-04-08
> **paul_in_london said:**
> I had my fingers crossed when I saw that 3.4.0-rc2 had turned up!
Pretty stable for an early rc.  And, certainly much better than rc1. LoL!  :D

I read that, somewhere upstream, "they" goofed up the rc1 release... but, they didn't discover it for a few hours... and since it was the weekend... and Palm Sunday... et cetera, et cetera, blah, blah, blah... they decided to wait until the weekday(s) to patch the problem.

Anyway, I'm pleased with the results of all this fussing around.  I've had a couple of error dialogs pop up, in the past three hours, but no show-stoppers.  ;)

---

### Post by VinDSL on 2012-04-08
> **xebian said:**
> rc2 still needs this fix btw.
This meandering post got me on the right path: [http://ubuntuforums.org/showthread.php?t=1952729](http://ubuntuforums.org/showthread.php?t=1952729)

Basically:

[LIST]
[*]Install the edgers nvidia-current.
[*]Upgrade to the edgers xserver 1.12.0 (and all the vid drivers, of course).
[*]Wait for Linux 3.4rc2 to be released.
[/LIST]


The 3.4rc2 mainline kernel .debs now install (on this machine), error-free, just like any other kernel.  ;)

---

