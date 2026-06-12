---
title: "Pondering Switch from Gentoo to Ubuntu"
date: 2005-01-12
forum: The Cafe
---

### Post by Boiler98 on 2005-01-12
Hello all.

I am currently using Gentoo, which I really like.  The only thing I can really complain about with Gentoo is the fact that I'm well aware of the fact that I don't know nearly enough to be able to use the "tunable" features of a source distribution to make it meaningful. :)  Okay that, and compiling everything sometimes gets on my nerves when I know I'm not getting anything more out of it.

Has anyone else switched from Gentoo to Ubuntu, or is currently using both?

My most immediate concern is how configure the system is and how easy/hard it is to modify the system as needed.  I've already run across one mention that I will need to install a new kernel (686 kernel, possibly the smp for hyperthreading) after installing Ubuntu.  What are my option for rolling my own kernel if I need to?

Based on screen shots, it appears Ubuntu has a GUI installer for packages.  Is there a mass update capability similar to Gentoo's 'emerge --update world'?

I guess the short of it, after all of that, is that I like to be able to tinker with things such as the kernel when it suits me or when I have to.  But I really don't need the granularity per package that Gentoo gives me, and I certainly can do w/o the time required to compile everything (like now, as my system crawls while compiling the latest library sets).

How can Ubuntu help me with general ease of use, while satisfy my occasional need to express my geekiness (i.e.: rolling my own kernel and maybe tinkering with a few apps here and there)?

Oh, and one last thing I just noticed.  I saw that the latest release of Ubuntu goes with XFree86 -- what is involved in switching to x11.org in the current release?

Thanks for any input!  I've heard a lot of nice things about Ubuntu and would like to try it out soon.

---

### Post by Rancoras on 2005-01-12
First of all, welcome to the forum.  Yes, you can roll your own kernel if you want.  In fact, there's a great howto about that on the ubuntu wiki site.

[http://www.ubuntulinux.org/wiki/KernelCompileHowto](http://www.ubuntulinux.org/wiki/KernelCompileHowto)

The gui package manager you refer to is synaptic.  It will do update like emerge as well.  The first time you reload and upgrade it will ask you if you want to do a "smart upgrade".  This is analagous to apt-get dist-upgrade from the command line.

Upping to x.org in the current release (warty) is no trivial process.  I wouldn't recommend it.  X.org is working well, however, in the testing release (hoary).  If you're a tinkerer, maybe hoary is a good fit for you.  It still gets broken from time to time, but not too bad.

---

### Post by jdodson on 2005-01-12
welcome.

[QUOTE=Boiler98]Based on screen shots, it appears Ubuntu has a GUI installer for packages.  Is there a mass update capability similar to Gentoo's 'emerge --update world'?[/QUOTE]

this is where ubuntu breaks ranks with gentoo.  unbutu stabalizes a debian snapshots of packages.  these packages only recieve updates for security and the occasional stability update.  you can perform a "update world" of sorts that updates the packages for security and stability, however ubuntu does not upgrade them to the latest versions.  there is, however a new version of ubuntu called hoary that is a testing/bleeding edge version.  this is prone to many packages breaking and unstability, so use at your own risk.  when the new version of unbuntu is released that is stabalized you can upgrade to the new version by running "apt-get dist-updade" this is very similar to --update world.

[QUOTE=Boiler98]I guess the short of it, after all of that, is that I like to be able to tinker with things such as the kernel when it suits me or when I have to.  But I really don't need the granularity per package that Gentoo gives me, and I certainly can do w/o the time required to compile everything (like now, as my system crawls while compiling the latest library sets).[/QUOTE]

ubuntu does not stop the user from doing anything such as recompiling the kernel.  it does give you a very robust package system that allows you to build from source or use the precompiled packages.

[QUOTE=Boiler98]How can Ubuntu help me with general ease of use, while satisfy my occasional need to express my geekiness (i.e.: rolling my own kernel and maybe tinkering with a few apps here and there)?[/QUOTE]

ubuntu provides gnome 2.8 and will keep up on the latest version of gnome it can stabalize.  it also provides synaptic for ease of package installation and many more new graphical tools in the next version.

[QUOTE=Boiler98]Oh, and one last thing I just noticed.  I saw that the latest release of Ubuntu goes with XFree86 -- what is involved in switching to x11.org in the current release?[/QUOTE]

to do this you must move to the latest development release of ubuntu called hoary.  xorg will be included in the new ubuntu due out in a few months.

[QUOTE=Boiler98]Thanks for any input!  I've heard a lot of nice things about Ubuntu and would like to try it out soon.[/QUOTE]

we welcome you to the club! :mrgreen:

---

### Post by HiddenWolf on 2005-01-12
[QUOTE=Rancoras]First of all, welcome to the forum.  Yes, you can roll your own kernel if you want.  In fact, there's a great howto about that on the ubuntu wiki site.

[http://www.ubuntulinux.org/wiki/KernelCompileHowto](http://www.ubuntulinux.org/wiki/KernelCompileHowto)

The gui package manager you refer to is synaptic.  It will do update like emerge as well.  The first time you reload and upgrade it will ask you if you want to do a "smart upgrade".  This is analagous to apt-get dist-upgrade from the command line.

Upping to x.org in the current release (warty) is no trivial process.  I wouldn't recommend it.  X.org is working well, however, in the testing release (hoary).  If you're a tinkerer, maybe hoary is a good fit for you.  It still gets broken from time to time, but not too bad.[/QUOTE]
He's running gentoo, that makes him a tinkerer.

I find apt a far easier and faster tool then emerge, but it's all up to preference.
I've compiled a few gentoo systems, and altho I loved them all dearly, I'd rather not spend so much time setting up my Os, and rather play around with it, and use all sorts of exiting software besides getting some work done.

One is not really productive if one is compiling the new version of say xfce just for the fun of looking at it. :-)

---

### Post by Boiler98 on 2005-01-13
Don't assume I'm a tinkerer just because I use Gentoo. :)  I kind of forced myself into Gentoo, with the idea that I would have to learn the inner workings of everything.  I just end up reading HOW-TO guides 3 times over and then bookmark them so I can figure it out the next time.

I'm so close to jumping ship for Ubuntu... so very close!  But not there yet. ;)

Just tossing out a few questions as I go along here:

How are the updates to the major releases handled?  More specifically, how are the application default changes handled -- like XFree->X.Org?

Is it possible to use a preview release of the new release?  I thought I saw that in one of the msgs above, but can't seem to parse it out now (the fact that I'm really tired right now might be why).  If so, how can I do that?

From the FAQ/Wiki, it sounds like the package system can install newer versions of packages that aren't considered stable yet, but might be needed by something I'm using.  Did I read that correctly?

When installing, does the installers partitioning tool allow me to install the system on a pre-partitioned drive?  I already have every chopped up, and I want to make sure that /home isn't killed (or be absolutely sure to back it up first).

One last (really off-topic and petty question)... how's Cedega work on Ubuntu?  Figure I should ask since I've got it running in the background right now. ;)

Thanks again all!  I appreciate the help.  I'll probably be trying it out by the end of the week. :)

---

### Post by nocturn on 2005-01-13
> **Boiler98]Hello all.

I am currently using Gentoo, which I really like.  The only thing I can really complain about with Gentoo is the fact that I'm well aware of the fact that I don't know nearly enough to be able to use the "tunable" features of a source distribution to make it meaningful. :)  Okay that, and compiling everything sometimes gets on my nerves when I know I'm not getting anything more out of it.

Has anyone else switched from Gentoo to Ubuntu, or is currently using both?
[/QUOTE]

I used to run Gentoo over 3 machines.  I installed Ubuntu on mine in a dual boot to test it out.  Well, I never went back.  I only need to convert one more machine.

One thing I have noticed, for all the tuning and tweaking (and compiling specificly for my CPU), Gentoo is not notably faster then Ubuntu.  
If you count the endless compile times (arround 18 hours for KDE), I now have a desktop I use as a means instead of an end.

> 
My most immediate concern is how configure the system is and how easy/hard it is to modify the system as needed.  I've already run across one mention that I will need to install a new kernel (686 kernel, possibly the smp for hyperthreading) after installing Ubuntu.  What are my option for rolling my own kernel if I need to?

Based on screen shots, it appears Ubuntu has a GUI installer for packages.  Is there a mass update capability similar to Gentoo's 'emerge --update world'?


Yes, this feature was largly based on Debian's apt in the first place.
One thing you need to realise is that Ubuntu features a stable and unou stable version.
The stable version is frozen and only gets security (and optional important) updates.   No new versions.

There is a new stable release every six months, you can use 'apt-get update said:**
> 
I guess the short of it, after all of that, is that I like to be able to tinker with things such as the kernel when it suits me or when I have to.  But I really don't need the granularity per package that Gentoo gives me, and I certainly can do w/o the time required to compile everything (like now, as my system crawls while compiling the latest library sets).

How can Ubuntu help me with general ease of use, while satisfy my occasional need to express my geekiness (i.e.: rolling my own kernel and maybe tinkering with a few apps here and there)?


There is no problem building your own kernel or compiling your own apps on Ubuntu.  I do not do this if it is not needed, but you can.

> 
Oh, and one last thing I just noticed.  I saw that the latest release of Ubuntu goes with XFree86 -- what is involved in switching to x11.org in the current release?

Thanks for any input!  I've heard a lot of nice things about Ubuntu and would like to try it out soon.

Ubuntu is switching to Xorg, this will be the new X server in Hoary (scheduled for april 2005).  I would not recommend installing it in Warty, you will break a lot of things.

This type of thing is the main difference between Ubuntu and Gentoo.  You have to wait a little longer for newer versions/software, but everything is tested very well.

---

### Post by twstd3bc on 2005-01-18
I've been using Gentoo for more than 3 years, and just recently installed Ubuntu on an iMac.  I have to say Ubuntu is pretty awesome, especially the painless install (it's more difficult to install Gentoo on Macs than on x86), but I do think Gentoo gives you a lot more control, and has a lot more packages available (without effort) such as feh, rox, ...  Also, compiling a kernel for PPC took some work to figure out on Ubuntu, but I think it's easier than on Gentoo because of the config files provided in /boot.

I think you should use Ubuntu now, and move to Gentoo later.  You don't have to compile the big packages on Gentoo-- and later on you may realize you don't need humongous packages like KDE.  When you use Gentoo, waiting on releases is nonexistent, which is really a highly underrated feature.  I used to always install the latest RedHat and Mandrake back in the day, but once you use Gentoo all of it seems unnecessary.

---

### Post by nocturn on 2005-01-18
[QUOTE=twstd3bc] When you use Gentoo, waiting on releases is nonexistent, which is really a highly underrated feature.  I used to always install the latest RedHat and Mandrake back in the day, but once you use Gentoo all of it seems unnecessary.[/QUOTE]

That is true and I have been happy running Gentoo for 1-2 years.
But now I'm on Ubuntu, I realize just how much time went into maintaining my Gentoo boxes each week.  Time I now spend with my 5 months old son.
When Ubuntu releases a new version, I can set aside a day or a weekend and do the upgrades.

Gentoo often required moving to a newer version for security updates, a lot of the time these newer versions broke things which I would spend hours fixing (stressed out because I had other things to do that evening, but I try not to skip security updates).

---

### Post by jdodson on 2005-01-18
[QUOTE=twstd3bc]I've been using Gentoo for more than 3 years, and just recently installed Ubuntu on an iMac.  I have to say Ubuntu is pretty awesome, especially the painless install (it's more difficult to install Gentoo on Macs than on x86), but I do think Gentoo gives you a lot more control, and has a lot more packages available (without effort) such as feh, rox, ...  Also, compiling a kernel for PPC took some work to figure out on Ubuntu, but I think it's easier than on Gentoo because of the config files provided in /boot.

I think you should use Ubuntu now, and move to Gentoo later.  You don't have to compile the big packages on Gentoo-- and later on you may realize you don't need humongous packages like KDE.  When you use Gentoo, waiting on releases is nonexistent, which is really a highly underrated feature.  I used to always install the latest RedHat and Mandrake back in the day, but once you use Gentoo all of it seems unnecessary.[/QUOTE]

you can configure your system in the same manner as gentoo using apt-build.  ubuntu provides the sources to ALL of its packages per archetecture.  you can configure the apt-build much like portage to compile per your proccessor, etc.

[http://julien.danjou.info/article-apt-build.html](http://julien.danjou.info/article-apt-build.html)

---

### Post by Lovechild on 2005-01-18
Welcome aboard

---

### Post by Daniel G. Taylor on 2005-01-21
Well, I'm a bit late but I switched from Gentoo to Ubuntu about six months ago.

I haven't really looked back since. I have all the neat software I had before (with Hoary, the current unstable version of Ubuntu) and I am just happy with it.

I think there are quite a few of us here, and as Lovechild said, welcome!

---

### Post by mark on 2005-01-21
Again, welcome to the forum.

I come from "the other side" - I was a Red Hat/Fedora user for several years.  After deciding that RH/FC was getting a bit "bulky", I looked around...heard good things about Debian and, lo and behold, here was this spiffy new distro called Ubuntu that was Debian-based with Gnome as the default environment (KDE & I have never gotten on<g>).  So, I tried it and liked it so much that I'm still here...

I've tried (twice!) to do a bare-metal Gentoo install and have never been able to get a workable system out of it.  I've not given up - I still want to be able to say (someday), "Yeah, I did a Stage 1 install..." - but for now, I'd rather *use* the benefits of free and open software than spend all of my time compiling...while enjoying the fact that there's still plenty of opportunity to "tinker".

Regards,

Mark

---

### Post by poofyhairguy on 2005-01-21
[QUOTE=mark]Again, welcome to the forum.

I come from "the other side" - I was a Red Hat/Fedora user for several years.  After deciding that RH/FC was getting a bit "bulky", I looked around...heard good things about Debian and, lo and behold, here was this spiffy new distro called Ubuntu that was Debian-based with Gnome as the default environment (KDE & I have never gotten on<g>).  So, I tried it and liked it so much that I'm still here...

I've tried (twice!) to do a bare-metal Gentoo install and have never been able to get a workable system out of it.  I've not given up - I still want to be able to say (someday), "Yeah, I did a Stage 1 install..." - but for now, I'd rather *use* the benefits of free and open software than spend all of my time compiling...while enjoying the fact that there's still plenty of opportunity to "tinker".

Regards,

Mark[/QUOTE]

My favorite thing about debian is how you don't have to compile anything!

---

