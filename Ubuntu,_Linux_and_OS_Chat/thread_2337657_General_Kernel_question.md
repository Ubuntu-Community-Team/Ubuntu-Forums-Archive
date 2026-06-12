---
title: "General Kernel question"
date: 2016-09-20
forum: Ubuntu, Linux and OS Chat
---

### Post by simonsaysthis on 2016-09-20
Hi all

Since I am at beginner Linux level there is one thing I always wondered about. Why does Ubuntu not update to the latest stable Kernel (like Fedora for example). So while everything works fine on 16.04, I have the issue of poor Skylake and Intel HD video acceleration. Is that that all Kernels that are not LTS are theoretically unstable?

Ubuntu does update the kernel sometimes because yesterday I got version 38 of 4.4. Are these just security patches or does a newer version of the same Kernel also mean that you might get better hardware support?

Lastly, is there a reason why software like Libreoffice is also not updated. I would presume why there is no reason why the latest version would not the stable?

Would really love to understand these things

---

### Post by mörgæs on 2016-09-20
If everything in, say 14.04 were updated to 16.04 level it would be another 16.04. 

It's possible to arrange updates that way (and called a rolling release) but it's not what Ubuntu has decided to do. Here only browsers are updated in 14.04, and all other applications are kept as they are. Only security bug fixes are provided. 

Development (as in adding new functionality) is only done in the development version. 

Better hardware support may eventually trickle down to old releases but it's better to keep focus on the development release if you have new hardware.

---

### Post by ian-weisser on 2016-09-20
> **simonsaysthis said:**
> Lastly, is there a reason why software like Libreoffice is also not updated. I would presume why there is no reason why the latest version would not the stable?

You misunderstand the meaning of 'stable'.
Stable does not mean 'it has no critical bugs at all'
Stable merely means 'no critical bugs were reported during the short testing period by a small set of testers on their limited set of equipment'

You also misunderstand the purpose of a Linux distro.
A Linux distro is not primarily a 'brand' of Linux.
A Linux distro is a snapshot of software that uses *exactly* the same shared libraries, and is usually tested together.
In the old days before distros and apt, upgrading one lib or application could break your entire system...and really ruin your day.

---

### Post by simonsaysthis on 2016-09-20
> **ian-weisser said:**
> You misunderstand the meaning of 'stable'.
Stable does not mean 'it has no critical bugs at all'
Stable merely means 'no critical bugs were reported during the short testing period by a small set of testers on their limited set of equipment'

You also misunderstand the purpose of a Linux distro.
A Linux distro is not primarily a 'brand' of Linux.
A Linux distro is a snapshot of software that uses *exactly* the same shared libraries, and is usually tested together.
In the old days before distros and apt, upgrading one lib or application could break your entire system...and really ruin your day.

Thanks, I get the first part but not sure how the second part relates to the question. Is a distro not a brand in a way that it decides how to treat packages from a larger pool such as AUR or Debian?

---

### Post by ajgreeny on 2016-09-20
You can add what are known as PPA repositories for some applications; they allow you to upgrade to a newer version of the application such as Libreoffice.

As a result I have been using a more up to date version of LO for a very long time, and currently in my Xubuntu 14.04 I have LO 5.2.1~rc2-0ubuntu1~trusty0 which works absolutely fine, and that repo has done for a very long time.

If you wish to try it go to [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa) and follow the instructions to enable those repos. If for some reason you have any problems with that version of LO you can disable that PPA repository and uninstall LO then reinstall it.

Do remember, however, that more up to date is not always better and there could be more bugs in the applications.  In the case of this version of LO I have not come across any so far.

---

### Post by ian-weisser on 2016-09-20
> **simonsaysthis said:**
> Is a distro not a brand in a way that it decides how to treat packages from a larger pool such as AUR or Debian?

The 'decides how to treat packages' is not the important part. That's an effect.
The cause of that effect is the snapshotting of, say, LibreOffice on a certain date.

A 'distro' is an assembly of those snapshots (especially the snapshots of deep dependencies)...and the community that grows around the assembly.

Before distros: When you upgraded one application, the upgrade only worked if was compiled against the *original** version *of those dependencies. If not, the result might be incompatible with your system, which is compiled against the older dependencies. It made upgrading any application or OS component a *huge* pain. and caused much teeth-gnashing about 20 years ago, and led directly to the creation of modern distros.

Distros cured the pain by snapshotting the entire universe of dependencies at once, and compiling everything against the same version of each dependency. You update your applications AND os at the same time. Note that this is *very* different from the way the Windows ecosystem works, and that difference confuses a lot of new users with strong Windows skills.

....And now we come to the part that is relevant to your original question about LTS and kernels.

Big organizations didn't want to upgrade their entire OS and all applications every six months (Ubuntu's release schedule). It was risky and expensive - new workflows, new bugs, and little new gain. To address their needs, Ubuntu introduced LTS.

Myth: LTS is magically somehow 'more stable' than non-LTS.
Reality: In the LTS context, 'stable' does NOT mean 'fewer bugs'. 'stable' means 'the software stack is always consistent'

Example: Ubuntu 12.04 was released in April 2012 (hence the release number) with Kernel 3.2.0 and LibreOffice 3.5. 
Today, since the software stack is deliberately kept consistent, a brand new, updated 12.04.4 iso will include Kernel 3.2.0 and LibreOffice 3.5.

Can you update the Kernel? Yes. It's your system. You can do anything you wish.
Is it easy to do? No, because that would defeat the explicit purpose of that LTS release. Any expert *could* do it, but it's generally not worthwhile when newer versions of Ubuntu (14.04, 16.04) are easy to test and install. Once you move away from the distro-provided packages, you're off-trail - bring your own compass and map. 

If you want to experiment with new kernels to test or improve your hardware support, your target should be the development release of Ubuntu (currently 16.10). WARNING - there is breakage, it's not for beginners, it's not for production systems, it's 'pre-release' in big red flashing unfriendly letters. You need skills to navigate the tweaks and issues of pre-release software.

---

### Post by simonsaysthis on 2016-09-20
> **ian-weisser said:**
> The 'decides how to treat packages' is not the important part.. 

Thanks so much for the great explanation. Now it makes sense. It now also makes sense that adding a repository with current graphics drivers worked on the one hand by giving me better Skylake support. But on the other hand since I installed those packages Ubuntu had been behaving strangely. It seems it is really better to stick with what is provided to get the most out of a LTS distro.

---

### Post by mastablasta on 2016-09-21
you could also use a PPA to patch your current kernel with new drivers (oibaf, xorg edgers...). if they were tested wlel it should mean breakage in the system, but would "save it" instead.

in future it might be possible what you want with "snaps". at least with apps. 

Fedora is a testing ground for RedHat/CentOS which have similar policy as Ubuntu and would patch only securityfor 8-10 years. 

similary windows has/had same kernel and only patches. this might change with 10. but driver there are outside the kernel so it didn't matter as much.

---

### Post by buzzingrobot on 2016-09-21
> **simonsaysthis said:**
> Hi all

Since I am at beginner Linux level there is one thing I always wondered about. Why does Ubuntu not update to the latest stable Kernel (like Fedora for example).

Fedora's release and support cycle takes a bit of explanation:

1.  Two releases are supported at any given time.  Currently supported releases are F23 and F24. A release is supported for about 13 months -- until the release of the second subsequent new version.  For example, support for F23 will end about 30 days after F25 is released. (The date isn't absolutely fixed  because it depends on the actual date of that second subsequent release.) Support for F24 will end approx. 30 days after release of F26.

2. Fedora's development follows two tracks.  Currently, Rawhide is what will become F26.  F25 is in a late-alpha stage.  When F25 is released, development in Rawhide will continue and, at some point in that cycle, it will "branch" off to become F26, while Rawhide itself keeps going with what will be F27.

3.  So, right now, you can download iso's and install F23, F24, the F25 development release, and a Rawhide snapshot. 

4. The current F23 kernel is 4.7.3-100. The current F24 kernel is 4.7.3-200. F25 & Rawhide: 4.8.0-0.rc7.  (Mesa, Xorg/Wayland and the rest of the video stack are typically also very current.) Like most kernels from well-supported distros, Fedora's is not necessarily the unmodified stock kernel from Linus.)

5. Periodically, Red Hat takes an existing Fedora release, typically a release or two behind the current release, works on it for perhaps a year or so, then does a public alpha/beta cycle, and eventually turns loose a new Red Hat release. It's more than an well-tested Fedora release.  There are typically significant changes.

Fedora follows a stricter FOSS policy than Canonical. This means that Canonical tests, packages and distributes proprietary drivers.  Fedora does not. Those drivers are available to Fedora users from unofficial third parties. Breakage, especially in new video driver/new kernel interactions, that Canonical may catch in its testing is typically caught be Fedora end users.

---

### Post by simonsaysthis on 2016-09-24
> **mastablasta said:**
> you could also use a PPA to patch your current kernel with new drivers (oibaf, xorg edgers...). if they were tested wlel it should mean breakage in the system, but would "save it" instead.

in future it might be possible what you want with "snaps". at least with apps. 

Fedora is a testing ground for RedHat/CentOS which have similar policy as Ubuntu and would patch only securityfor 8-10 years. 

similary windows has/had same kernel and only patches. this might change with 10. but driver there are outside the kernel so it didn't matter as much.


So this is what just happened. I had a standard installation of 16.04 and the only thing I did was adding the oibaf repo to get the latest graphics drivers. After that Unity broke completely and I had black windows everyewhere. I couldn't even open the terminal and had to reinstall everything. I appreciate not having the latest kernel and packages for a good and stable system but if one can't get Skylake and Intel HD to work well enough without adding external firmware at the risk of breaking the system, then maybe LTS really isnt for everyone. Maybe better for businesses.

---

### Post by mastablasta on 2016-09-25
you could have just booted into text mode ran purge PPA and then reboot you would be back at where you started.

the other thing is that it is strange to get such bad output. even beta drivers should be presentable. 

if it all works on Fedora just use that.

intel used to have some sort of driver installer (e.g. for manual driver install). i wonder if they still have it and if that could be used to patch it?

---

### Post by simonsaysthis on 2016-09-25
> **mastablasta said:**
> you could have just booted into text mode ran purge PPA and then reboot you would be back at where you started.

the other thing is that it is strange to get such bad output. even beta drivers should be presentable. 

if it all works on Fedora just use that.

intel used to have some sort of driver installer (e.g. for manual driver install). i wonder if they still have it and if that could be used to patch it?


Ah this would have been much easier. Need to write down the steps on how to purge a PPA for next time. Intel does indeed have a relatively new graphics driver installer for 16.04 but after reading all the negative comments I was very hesitant. I will definitely try this though and then update to Yakkety once its released. Thanks a mil

---

### Post by mastablasta on 2016-09-26
re: intel gpu driver installer - just make sure to note down first how to uninstall it then you can give it a go.

i had an nVidia GT 730 - it should all work well but for some reason it didn't on my PC. the opensoruce driver worked in some strange resolution, but not nVidia. so i did plenty of driver install/reinstall, driver PPA...  and now that i think back it could be that display was on the other port (it does this on Windows), but then why i got blinking cursor.... eh never mind. in any case it helps a lot to note down how to uninstall. then there is no need for system wide reinstalling.

---

