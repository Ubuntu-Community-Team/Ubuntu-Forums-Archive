---
title: "Hardy's kernel -- terrible wireless support -- Horrible LTS!"
date: 2008-05-08
forum: Ubuntu Brainstorm
---

### Post by kevdog on 2008-05-08
I'm making a plea to the developers to release a new kernel (if possible) for hardy to fix the numerous wireless problems associated with the hardy kernel.  I've read from other forums a lot of changes were made in the vanilla kernel used by hardy but later corrected in more recent releases.  The networking and wireless forums are flooded with issues of broken drivers, sloppy workarounds, etc, just to get wireless working.  These problems were never present with gutsy.  HH can never be a LTS if these problems are not rectified.  One way of doing this would be to possibly update the kernel.  A large plea indeed, but the HH associated kernel just plain stinks for wireless support.  Definitely a step backwards in terms of support.

---

### Post by Whoopie on 2008-05-08
Did you try the new -17 kernel in hardy-proposed? If not, did you try the linux-backports-modules-2.6.24-16-generic package?  Perhaps, the situation is not that good, but normally, I don't answer to such threads because I don't like people complaining like this.

---

### Post by quickshade on 2008-05-08
Problem is there is no one solution thats going to fix everyones wireless problem. Wireless seems to be a mess right now because so much work is being done. You have kernel work to get better wireless support, ndiswrapper and others reworking stuff, then you have network manager that is undergoing work, not to mention KDE4 and Knetwork manager. So it's just a weakpoint in linux right now (like 3D support 1-2 years ago) until we get some polish on these applications.

---

### Post by plun on 2008-05-08
> **kevdog said:**
>  The networking and wireless forums are flooded with issues of broken drivers, sloppy workarounds, etc, just to get wireless working.  These problems were never present with gutsy. Definitely a step backwards in terms of support.

Yup... its a total worldwide mess.

Your work and your thread is a saver...  Tanks for that ! Great work  :)

I also don't know if the proposed kernel can be a good solution
for a user with problems  :confused:

Launchpad is a terrible slow mess to find good info.

Hardy Changes for the moment
[https://lists.ubuntu.com/archives/hardy-changes/2008-May/thread.html](https://lists.ubuntu.com/archives/hardy-changes/2008-May/thread.html)

---

### Post by kevdog on 2008-05-08
Dont confuse this for complaining -- take a look at the networking forums if you don't believe.  Broadcom support is worse than ever.  Intel chipsets have changed.  Ra seems to be status quo.  Network Manager -- from what I had read when Gutsy was out that it was going to be vastly improved with the HH release -- Not So!.  Linus for a while was going to drop ndiswrapper support -- has since reconsidered this option.  RTL chipsets -- another mess.  

I'm no developer so I really don't understand the complexities or interaction between the various kernel modules and the linux kernel.  I do however volunteer a lot of my time helping others with their wireless problems.  The entire Hardy kernel however has opened pandora's box.  So many changes -- so many unsupported changes -- so many changes that simply don't wore -- Broadcom with the entire ssb module seems to be the worst culprit.  No good documentation for workarounds except sloppily put together scripts, and module unloads, etc put together by users are workarounds.  

Possibly I'll try with another vanilla kernel again to see.  I just can't believe the HH was released as a LTS with so many wireless problems.  How could this be considered to be a long term release, when it seems in terms of wireless its taken a step backwards (way backwards)?

---

### Post by yelo3 on 2008-05-08
There is a workaround for broadcom and ssb:
download [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)
extract it, go into the newly created directory and run:
make
sudo make install
sudo make load
sudo depmod -a
sudo update-initramfs -k all -u

---

### Post by 23meg on 2008-05-08
[QUOTE=kevdog]I'm making a plea to the developers to release a new kernel (if possible) for hardy to fix the numerous wireless problems associated with the hardy kernel.[/QUOTE]

The problems with your plea are 1) that this isn't the place to do it, as few developers frequent this website 2) that simply rolling out a new kernel doesn't magically fix all problems for everyone.

You need to be specific in terms of what you want fixed. The best way to do that is to file bug reports, and/or contribute information to existing ones. There's no doubt that there are serious issues with networking (I've had my share of them and had to compile a module from source, as a Realtek 8111 user), and new kernels will definitely be rolled out (there's a proposed update that's waiting for verification; testing is appreciated) but simply saying "we need a new kernel" doesn't help; filing good bug reports, providing extra information for existing ones, and submitting patches (which are already out there in many cases and just need merging) does.

---

