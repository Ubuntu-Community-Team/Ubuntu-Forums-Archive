---
title: "utopic development 14.10: kernel = 3.13?"
date: 2014-09-02
forum: Ubuntu Development Version
---

### Post by ivo-welch on 2014-09-02
I just folded space to gnome ubuntu 14.10 (with update-manager -d), well yesterday, presumably with enough delay for the beta to trickle to my archives.  I now see

```
# cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.10
DISTRIB_CODENAME=utopic
DISTRIB_DESCRIPTION="Ubuntu Utopic Unicorn (development branch)"
NAME="Ubuntu"
VERSION="14.10 (Utopic Unicorn)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu Utopic Unicorn (development branch)"
VERSION_ID="14.10"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"

# cat /proc/version
Linux version 3.13.0-35-generic (buildd@panlong) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014

```



I am surprised by two aspects:  first, that it tells me I am running the development branch, but not that I am running the beta.  second, that I am running kernel 3.13.  I thought 14.10 was switched to kernel 3.16.   (I am having some trouble with an AMD card driving two monitors, one of which is 4K, so I want to try the later kernels.)

/iaw

---

### Post by grahammechanical on 2014-09-02
Let me confuse you even more. :) Ubuntu does not have alpha and beta version any more. The flavours do but not Ubuntu. Furthermore, whether it is alpha 1 or beta 2 or release candidate, they are all development branch and that is what the "release" file will read until the OS officially becomes 14.10.

You can try

```
sudo apt-get update
sudo apt-get upgrade
```

and see what that gets you and then try

```
sudo apt-get dist-upgrade
```

Regards.

---

### Post by Ian_Worrall on 2014-09-02
Funny, mine is currently installing 3.16.0-12. Have you rebooted since upgrading?

---

### Post by ivo-welch on 2014-09-02
nothing...what kernel is 14.10 development supposed to be on now?

---

### Post by Elfy on 2014-09-02
3.16.0-12

---

### Post by ivo-welch on 2014-09-02
then there must be something wrong with the updater.  I am looking at my /boot/ directory, and it contains only vmlinuz-3.13.0-35-generic.  so, it ain't a reboot problem.

```

dpkg -l | grep linux-image-
rc  linux-image-3.13.0-32-generic               3.13.0-32.57                             amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-34-generic               3.13.0-34.60                             amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-generic               3.13.0-35.62                             amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP

```

but I am running 14.10 on the amd64 architecture.  this was ascertained by the etc release as well as obviously newer versions of other utilities (e.g., fdisk is now colorized).

is there a 14.10 manifest that would allow me to check what packages there should be in it, and a utility to compare the official manifest with what I currently have installed?

/iaw

---

### Post by ivo-welch on 2014-09-02
this may do it:

[http://unix.stackexchange.com/questions/3595/list-explicitly-installed-packages](http://unix.stackexchange.com/questions/3595/list-explicitly-installed-packages)

---

### Post by ivo-welch on 2014-09-02
definitely a broken updater.  I have a long update log, but it omitted updating 736 out of 2115 files.

so update-manager -d on gnome-ubuntu is flawed.

fresh install needed.

/iaw

---

### Post by arthur-widetschek on 2014-09-28
same problem with ubuntu and kubuntu.
upgrade from 14.04 to 14.10 (sudo do-release-upgrade --devel).
got kernel 3.13 :-(
will there be any bugfix. i don't want to do an fresh install every six month...

---

### Post by craig10x on 2014-09-28
@arthur: did you do the updates after you did your upgrade?  Just wondering, because i recall when i upgraded from 13.10 to 14.04, initially, the 13.10 kernel was installed but the when i did the updates afterward, the current 14.04 kernel was installed...if you did not, then i would say it says like a bug, as you mentioned...

---

### Post by arthur-widetschek on 2014-09-30
@craig10x, thanks for your quick reply.
I did an sudo aptitude update and an sudo aptitude dist-upgrade after upgrade to 14.10. --> kernel 3,13...
(I use aptitude instead of apt-get)
I'll try it again and let you know my results. 
Will there be any bugfix? I don't want to do an fresh install.

---

### Post by jerrylamos on 2014-09-30
Utopic 14.10 is in development.  It's unstable so expect to do installs maybe often.  If you don't want to do installs then wait until final release.

On this pc, Lenovo M58p Intel Core 2 Duo 3 gHz, screen compiz/unity was broken all of Augunst into first week of September couldn't run anything.  I did a bunch of installs including Jully levels of the linux-image the last ones that worked.  Expect busted .iso levels during development.

Now there is an intent of "rolling release" by doing updates of released code but this wouldn't apply to code in development, my opinion.

I keep the last released level running in one partition and do the development level in a separate partition.  I'm set up to boot the development .iso and apply my usual customization with an exec.

My opinion, if you don't want to do installs wait until the final release.  This is a development forum and anything can and does happen....

Have fun.

BTW, current image here is 3.16.0-18 although there are experimental levels of 3.17 available.

---

### Post by craig10x on 2014-09-30
You're welcome, arthur...From what i remember, when i did the upgrade from 13.10 to 14.04, which was still in development at the time (as 14.10 is now) it first had only the kernel from 13.10 but a short time later, when the software updater came up, there was a bunch of updates including the actual kernel that 14.04 was using...not sure what would happen when you update using the terminal as you do, but my suggestion would normally be that one should let the software updater do the updating (at least for the first time) after doing an upgrade...

Even in development, i prefer using the software updater unless it has a problem, in which case i get it to straighten out by using your method of updating in the terminal...

By the way, it's possible that the next development kernel update might bring it in for you...you might ask that anyone using development, post to the thread here when the next one comes in, so you can check to see if you got it also....and i think i'd let the software updater bring it in, to play it safe...

---

### Post by grahammechanical on 2014-10-01
There are two times during a development cycle when I would consider upgrading from a stable release to the development version. 1) during the first month of the development cycle. We do not get daily images until the second or third week of the cycle. 2) during the last two (maybe three) weeks of the development cycle and I would do that to test the upgrade process. In between times I would not expect the upgrade scripts to be accurate as the development is still continuing.

But all of that has nothing to do with the fact that you are now on 14.10 but not on Linux kernel 3.16. An upgrade will leave the last valid kernel of the old Ubuntu and add the latest kernel of the new Ubuntu. Or it should have done. It may be a case of Phased Updates holding back the latest kernel.

[https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)

I have been in situations where most on this section of the forum have said that they now had such and such a kernel and I was still stuck on the old kernel for a few days. I have had a new installation on the latest kernel and an old, daily updated Ubuntu still on the old kernel.

Regards.

---

### Post by jerrylamos on 2014-10-01
Several times "reboot" into .iso would not work.  My opinion grub screws up.  Full shutdown, power off, and boot usually works for me....

---

### Post by craig10x on 2014-10-01
Upgraded from 14.04 to 14.10 this morning...100% perfect and the 3.16 was installed (plus it removed all the 3.13 kernels and saved me extra work)...I was going to wait to RC but was anxious to get off the 3.13 kernel which was troublesome on my hardware...It does a nice job of cleaning out no longer need packages too...It's running smooth, zippy and nice and cool too...

---

### Post by arthur-widetschek on 2014-10-11
Hi, for those who have problems with kernel upgrade:
i found out, that the /boot/vmlinuz file was not generated.
this post helped me: 
[http://askubuntu.com/questions/150691/missing-vmlinuz-from-boot](http://askubuntu.com/questions/150691/missing-vmlinuz-from-boot)
so i did:
aptitude -V install linux-generic linux-image-generic linux-headers-genericand kernel 3.16 was generated in /boot..
YES!

---

