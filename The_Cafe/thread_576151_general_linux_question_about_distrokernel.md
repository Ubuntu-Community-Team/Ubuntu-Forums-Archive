---
title: "general linux question about distro/kernel"
date: 2007-10-14
forum: The Cafe
---

### Post by skunkrecords on 2007-10-14
Lately I've been looking into linux. While researching the linux kernel, I had a tough time finding the relationship between the kernel and the distro itself. Does the distro use the kernel as an API after it boots? Is there an actual function in the kernel that loads the distro? 
I understand the basic function of the kernel and how it interacts with the hardware, but where exactly the distro and its gui come in, im confused :confused:
If you could point me to some good resources that address this issue, that would be great. Thanks for the help in advance!

-Ruddy

---

### Post by kidders on 2007-10-18
Hi there,

There are a few ways of approaching your question. One is to start by saying that the kernel is a piece of software, just like any other, provided to Ubuntu (or any other distro) by a group of third-party developers.

Consider KDE, for instance. Although it's used by a large number of distros, none of them has any control over its development. Having said that, many distro developers tweak & hack KDE to alter its behaviour slightly, make it more accommodating of the particular quirks of their own OSs, or correct bugs. Many also use KDE's API to create new components for the platform.

The relationship between a distro and the official Linux kernel is quite similar. Try this, to reveal your current kernel version...```
$ uname -r
2.6.17-12-386
```Essentially, Ubuntu's version 2.6.17 (or whatever you happen to have) is the same as that used by Red Hat, Gentoo, Mandriva, and so on, except that...[LIST]
[*]The Ubuntu devs have patched it to remove certain features, and correct well-known bugs that adversely affect the OS, or programs that commonly run on it.
[*]Some minor additional features, unique to Ubuntu, have been added.
[*]Most applications have a two-step build process ... configuration & compilation. Just like any other app, the kernel's optimal build-time configuration is determined by the developers, and is not necessarily the same as any other distro's.
[/LIST]

> Does the distro use the kernel as an API after it boots?Sort of. The Linux kernel provides various well-defined interfaces to itself, and the hardware operating underneath it. Examples include devfs, sysfs & procfs, all of which reflect various aspects of your system using filesystem-like structures. This, for example, is where CPU monitors get information about how hot your processor is, and how your firewall can keep track of network activity.

At a lower level, the kernel developers provide C header files, and other material, designed to allow third parties to build against it, and interact with its libraries ... something else that the kernel has in common with KDE, and a variety of other software. Proprietary graphics drivers, for example, require this level of interaction with the kernel, to function correctly, and (for lack of a better way of putting it) need to take a look at your kernel, before they can build themselves correctly.

> Is there an actual function in the kernel that loads the distro?No. A Linux distro isn't something that physically exists. If you'll forgive the inane analogy, Ubuntu is a bit like a herd of cattle. The software (cows) that make it up are essentially the same as those in any other herd ... except, I suppose, that one software package might have a particularly attractive rump, or a peculiar-sounding moo (oh god, do I regret this analogy!). The point is though, that without the cows, there is no herd. I'm not sure if that answers your question.

> I understand the basic function of the kernel and how it interacts with the hardware, but where exactly the distro and its gui come in, im confusedThe distro, kernel & GUI don't really have that kind of relationship. It's not helpful to think of them as interacting with one another. It occurs to me though, that you might be describing the relationship between the kernel, a core set of system utilities, and the user interfaces that people interact with. The classic *-nix relationship between these three is that one operates "on top" of the other.

Consider Gparted (a disk partitioner/filesystem manager) or K3B (an optical disc writer) for example. These are dependent on lower-level utilities eg:
[LIST]
[*]"mkfs" & friends (for creating filesystems)
[*]"cdrecord" (for writing data to optical discs)
[*]"fdisk" (for manipulating disk partitions)
[/LIST]Although these utilities are advanced enough to use quite easily without the help of a graphical interface, many users choose not to interact with them directly. K3B and Gparted are essentially graphical shells ... they have very little internal functionality, and rely on other applications to do their work for them. These lower-level applications are the things that tend to interact directly with the kernel.

So, when you burn a CD, your graphical environment invokes "mkisofs" to create a disc image, and passes it to "cdrecord", to burn it. Essentially, it does nothing more than provide a pretty-looking way of achieving something you could have done just as well without its help ... an approach more like the way MacOS does things, and less like the way Windows does, I suppose.

Your last question, about reading material, is a tough one. Your post covers an enormously wide range of topics. A good search engine is perhaps your best bet. It's at least worth taking a look at [www.kernel.org](www.kernel.org) though ... the home of the Linux kernel.

I hope some of this helps answer your questions.

---

