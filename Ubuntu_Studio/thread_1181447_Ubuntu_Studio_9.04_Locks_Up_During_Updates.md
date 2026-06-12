---
title: "Ubuntu Studio 9.04 Locks Up During Updates"
date: 2009-06-07
forum: Ubuntu Studio
---

### Post by deepee_oz on 2009-06-07
Hi

I have been trialling the 64 bit version (with the RT kernel).
I had been getting random lockups that seemed to be related to network tasks, e.g. copying a sound font file from the server to my desktop.

I saw a thread that suggested it was an RT kernel issue and it suggested installing a generic kernel.
Tried that from command line in both normal mode and recovery mode. Both times the download process started and then froze.
Tried using synaptic to download latest updates (to see if there were any fixes)and the same thing happens.

This is running as a dual boot installation on an Athlon dual core machine. The WinXP installation has no problem with the network.
Ubuntu 9.04 32bit on my laptop is running fine on the same network.

Any ideas would be appreciated.

Thanks

---

### Post by luctor on 2009-06-08
it's a kernel bug, definitily :

> system freeze when using network with linux-rt on smp amd64 machines
[https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/354816](https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/354816)

if you haven't got a generic kernel to boot from , than i think you are screwed :-/
I suggest downloading the generic kernel packages via windows and install them manually from ubuntu

Sad to say but Ub-studio with rt-kernel isn't usable for me at the moment.
Some people, (look at this post) [https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/290498](https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/290498), are building their own rt-kernel.
Doing so, breaks up my pulseaudio and that's not what I want, although some people say pulseaudio has no place on a audio workstation.

---

### Post by deepee_oz on 2009-06-08
Thanks for the feedback luctor.
I'm going to try the suggestion I found in in the following thread and see how it goes:-

[http://ubuntuforums.org/showpost.php?p=7380975&postcount=26](http://ubuntuforums.org/showpost.php?p=7380975&postcount=26)

---

### Post by deepee_oz on 2009-06-19
I tried the suggestion of installing the Studio 64 kernel but dpkg returns an error.

Also tried installing the 32 bit version of Ubuntu Studio 9.04 and experience exactly the same issues as my oiriginal post.

---

### Post by sgx on 2009-06-21
> **deepee_oz said:**
> I tried the suggestion of installing the Studio 64 kernel but dpkg returns an error.

Also tried installing the 32 bit version of Ubuntu Studio 9.04 and experience exactly the same issues as my oiriginal post.
I would use the newest kubuntu, and just add the apps/kernel you want with synaptic, or go with the 8.04 ubuntu studio, where the RT works well,
and tunes are recorded, instead of sysadmin chronicles :)

---

### Post by ardugh on 2009-06-24
@sgx

> go with the 8.04 ubuntu studio, where the RT works well

- would this be 32 or 64bit?

Cheers,

---

