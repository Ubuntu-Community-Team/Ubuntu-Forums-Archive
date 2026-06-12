---
title: "Dapper 2.6.17 Kernels?"
date: 2006-06-20
forum: The Cafe
---

### Post by jdong on 2006-06-20
Is there any community interest in maintaining a set of updated kernels for Dapper, like Edgy kernel backports?

The reason I ask is that those with bleeding edge hardware will benefit from improved hardware support (i.e. the Core Duo CPU scheduler in 2.6.17) in newer kernels (Bugfixes are provided for Dapper kernels anyway, so that's not much of an argument).

I'd like to see these kernels packaged in the same way as Ubuntu's kernels (i.e. linux-image, linux-restricted-modules, etc) and that restricted modules are available. In addition, for the sake of stability, we must try to stay close to Edgy unless there is a good reason to deviate. The project should do its bug tracking on Launchpad so we can share appropriate bug reports with upstream.


Now, the other part... I absolutely do not have the time or resources to take on another project! So, if this is to progress beyond a discussion/wishlist, people will have to step up to the challenge :).

---

### Post by zachtib on 2006-06-20
i'd be interested, but i don't have the time to help with it...

---

### Post by xXx 0wn3d xXx on 2006-06-20
[QUOTE=jdong]Is there any community interest in maintaining a set of updated kernels for Dapper, like Edgy kernel backports?

The reason I ask is that those with bleeding edge hardware will benefit from improved hardware support (i.e. the Core Duo CPU scheduler in 2.6.17) in newer kernels (Bugfixes are provided for Dapper kernels anyway, so that's not much of an argument).

I'd like to see these kernels packaged in the same way as Ubuntu's kernels (i.e. linux-image, linux-restricted-modules, etc) and that restricted modules are available. In addition, for the sake of stability, we must try to stay close to Edgy unless there is a good reason to deviate. The project should do its bug tracking on Launchpad so we can share appropriate bug reports with upstream.


Now, the other part... I absolutely do not have the time or resources to take on another project! So, if this is to progress beyond a discussion/wishlist, people will have to step up to the challenge :).[/QUOTE]
I am interested. I have compilied many kernels. I have alot if time on my hands so I would be happy to help. I think that there should be seperat server and desktop kernels though.

---

### Post by christhemonkey on 2006-06-20
And a packaged realtime preemptible kernel, for all of us studio people out there.
(that is to say, a kernel patched with Ingo Molnars RT patch).

This sounds like an excellent idea.
Although, i dont think i would be much help at all.

---

### Post by jdong on 2006-06-20
[QUOTE=xXx 0wn3d xXx]I am interested. I have compilied many kernels. I have alot if time on my hands so I would be happy to help. I think that there should be seperat server and desktop kernels though.[/QUOTE]

The Ubuntu kernel packages already separate between desktops and servers.

---

### Post by ember on 2006-06-20
I am very interested - I hope it will solve my problems with the USB ports not working correctly.

EDIT:
And I could help packaging kernels (at least I think so), but I'm not clear about the restricted modules. How would I build that package?

---

### Post by WildTangent on 2006-06-20
I have the time, but I don't think I have the technical-knowhow for this :S

-Wild

---

### Post by zachtib on 2006-06-21
any update on the status of this?

---

### Post by jdong on 2006-06-21
well, I don't think we have enough developer power yet to do this.

---

### Post by tseliot on 2006-06-21
[QUOTE=jdong]I'd like to see these kernels packaged in the same way as Ubuntu's kernels (i.e. linux-image, linux-restricted-modules, etc) and that restricted modules are available.[/QUOTE]
Where can I find the documentation to compile kernels in that way, as well as to compile the restricted modules?

Or is it something like apt-get sources and dpkg-buildpackage -b -uc ?

---

### Post by Xylene on 2006-06-21
I was interested in setting up a site with up-to-date kernels patched with the CK patchset for 386, 686 and K7 in debian packages, ready to install. I don't have a 64bit box so I can't do K8 or any other 64bit, but the others I can do.

I have plenty of bandwidth and storage, so I could host such a project with a bit of help.

---

### Post by tseliot on 2006-06-21
I'm backporting a kernel (2.6.17-2-k7) just for fun. It hasn't finished compiling yet.

I'll try the headers and the restricted modules then.

---

### Post by tseliot on 2006-06-22
The following packages have beene generated:
```
/home/alberto/edgy/kernel/linux-doc-2.6.17_2.6.17-2.2_all.deb
/home/alberto/edgy/kernel/linux-headers-2.6.17-2_2.6.17-2.2_i386.deb
/home/alberto/edgy/kernel/linux-headers-2.6.17-2-386_2.6.17-2.2_i386.deb
/home/alberto/edgy/kernel/linux-headers-2.6.17-2-686_2.6.17-2.2_i386.deb
/home/alberto/edgy/kernel/linux-headers-2.6.17-2-k7_2.6.17-2.2_i386.deb
/home/alberto/edgy/kernel/linux-headers-2.6.17-2-server_2.6.17-2.2_i386.deb
/home/alberto/edgy/kernel/linux-headers-2.6.17-2-server-bigiron_2.6.17-2.2_i386.deb
/home/alberto/edgy/kernel/linux-image-2.6.17-2-386_2.6.17-2.2_i386.deb
/home/alberto/edgy/kernel/linux-image-2.6.17-2-686_2.6.17-2.2_i386.deb
/home/alberto/edgy/kernel/linux-image-2.6.17-2-k7_2.6.17-2.2_i386.deb
/home/alberto/edgy/kernel/linux-image-2.6.17-2-server_2.6.17-2.2_i386.deb
/home/alberto/edgy/kernel/linux-image-2.6.17-2-server-bigiron_2.6.17-2.2_i386.deb
/home/alberto/edgy/kernel/linux-kernel-devel_2.6.17-2.2_all.deb
/home/alberto/edgy/kernel/linux-source-2.6.17_2.6.17-2.2_all.deb

```

I have tried the kernel for k7 and it seems to be working just fine.

---

### Post by jdong on 2006-06-22
Excellent. Now, see if you can modify linux-restricted-modules (look at debian/control.in.in) to build for the 2.6.17-2 kernels.

---

### Post by tseliot on 2006-06-22
[QUOTE=jdong]Excellent. Now, see if you can modify linux-restricted-modules (look at debian/control.in.in) to build for the 2.6.17-2 kernels.[/QUOTE]

There's no debian/control.in.in

I've tried to modify:
debian/control
debian/control.stub
debian/control.stub.in
debian/d-i/kernel-versions
debian/d-i/kernel-versions.in


But it has compiled these packages:

```
avm-fritz-firmware-2.6.15-25_3.11+2.6.15.11-2_i386.deb
avm-fritz-kernel-source_3.11+2.6.15.11-2_i386.deb
fglrx-control_8.25.18+2.6.15.11-2_i386.deb
fglrx-kernel-source_8.25.18+2.6.15.11-2_i386.deb
linux-restricted-modules-2.6.15-25-386_2.6.15.11-2_i386.deb
linux-restricted-modules-2.6.15-25-686_2.6.15.11-2_i386.deb
linux-restricted-modules-2.6.15-25-k7_2.6.15.11-2_i386.deb
linux-restricted-modules-common_2.6.15.11-2_all.deb
nvidia-glx_1.0.8762+2.6.15.11-2_i386.deb
nvidia-glx-dev_1.0.8762+2.6.15.11-2_i386.deb
nvidia-glx-legacy_1.0.7174+2.6.15.11-2_i386.deb
nvidia-glx-legacy-dev_1.0.7174+2.6.15.11-2_i386.deb
nvidia-kernel-source_1.0.8762+2.6.15.11-2_i386.deb
nvidia-legacy-kernel-source_1.0.7174+2.6.15.11-2_i386.deb
xorg-driver-fglrx_7.0.0-8.25.18+2.6.15.11-2_i386.deb
xorg-driver-fglrx-dev_7.0.0-8.25.18+2.6.15.11-2_i386.deb

```

BUT their name is wrong (2.6.15-25)

---

### Post by jdong on 2006-06-22
As an update on this topic:

With the new Edgy Backports policy set by the Tech Board, it is possible (at least on the build system level) to do Edgy kernel backports to Dapper through dapper-backports, and if we don't backport linux-meta (I don't intend on it), then backported kernels will not install unless manually marked for installation (which would be the desired mode  of operation).

The other piece of the puzzle would be restricted modules, which will prove to be a pain if done via Backports, as you can see from tselliot's output, restricted modules also generates some packages that are not kernel version specific and could conflict with existing Dapper packages...

I will continue trying to think this through, and perhaps even contact Ben Collins and others on the Ubuntu kernel team / mdz and see if we can come up with a more official way of supplying version-upgraded Ubuntu kernels.

---

### Post by woedend on 2006-06-22
Right on.  With LTS kernel upgrades are a must.
How long did it take you to compile a single kernel package?

---

### Post by zachtib on 2006-06-22
[QUOTE=woedend]Right on.  With LTS kernel upgrades are a must.
How long did it take you to compile a single kernel package?[/QUOTE]

whoa, i never even thought about that.  3 (or is it 5) years without a kernel upgrade is sort of insane (i have trouble waiting 6 months)

---

### Post by tseliot on 2006-06-23
[QUOTE=woedend]Right on.  With LTS kernel upgrades are a must.
How long did it take you to compile a single kernel package?[/QUOTE]
A single kernel package? LOL

It took a night (I went to bed)

You can't just compile 1 kernel package but you need to compile them ALL (for all 32 architectures, etc.).


BTW I have installed only the kernel and the kernel headers and they work just fine.

---

### Post by woedend on 2006-06-23
all 32?  im afraid i dont understand why?  In any event...any chance of hosting/gmailing the K7 packages, or do you suspect they will be accepted into backports soon?  I'm eager to figure out if the clock issue is fixed (how it runs too fast since .16 came,) and also if my webcam will be supported natively.

---

### Post by mstlyevil on 2006-06-23
Awesome project. Let me know when you have a stable K7 kernel ready as my 7600 GT really needs this bad.

We just might make this an option in Automatix for Dapper if things work out.

---

### Post by tseliot on 2006-06-23
[QUOTE=jdong]The other piece of the puzzle would be restricted modules, which will prove to be a pain if done via Backports, as you can see from tselliot's output, restricted modules also generates some packages that are not kernel version specific and could conflict with existing Dapper packages...[/QUOTE]
I have installed the linux image (for k7) and the linux headers for k7 and 386 (the ones for 386 are needed by those for k7). Everything is working just fine. I didn't install the other packages.

[QUOTE=jdong]I will continue trying to think this through, and perhaps even contact Ben Collins and others on the Ubuntu kernel team / mdz and see if we can come up with a more official way of supplying version-upgraded Ubuntu kernels.[/QUOTE]
If you have any news, please let me know.

BTW perhaps we should just wait until they release the restricted modules for Edgy (so that I can backport them).

---

### Post by tseliot on 2006-06-23
[QUOTE=mstlyevil]Awesome project. Let me know when you have a stable K7 kernel ready as my 7600 GT really needs this bad.

We just might make this an option in Automatix for Dapper if things work out.[/QUOTE]
I'm using a k7 kernel. If you want to test it (with the headers and but without the restricted modules) I can upload it somewhere (unofficially).

---

### Post by jdong on 2006-06-23
It only takes a simple apt-get source -b linux-source-2.6.17 to regenerate those kernels.

linux-restricted-modules will take some source modification, but before doing it any unofficial way, I want to get a blessing from upstream kernel maintainers. In my experience from Backports, doing things like this behind their backs just leads to mass confusion later on, as all of a sudden people start filing bugs against a "2.6.17 kernel in Dapper" :D

---

### Post by tseliot on 2006-06-23
[QUOTE=jdong]linux-restricted-modules will take some source modification, but before doing it any unofficial way, I want to get a blessing from upstream kernel maintainers. In my experience from Backports, doing things like this behind their backs just leads to mass confusion later on, as all of a sudden people start filing bugs against a "2.6.17 kernel in Dapper" :D[/QUOTE]
You're right. And the developers dont' need that mess :)

---

### Post by pianoboy3333 on 2006-06-23
I have build a 2.6.17.1 kernel for myself, but I don't have the restricted-modules package, so my wifi isn't working in it, and I can help on this project if you want.

Tell me if you know a way to get a restricted-modules package.

---

### Post by jdong on 2006-06-23
I've started a thread on this at ubuntu-backports (mailing list on lists.ubuntu.com, like all the others :) )

Some of the Ubuntu developers who are involved with backports (siretart, crimsun, and others) are gonna shed light on the changes necessary, as long as their opinions. Already, we've identified the possibility of requiring to backport other packages (like udev) with newer kernels.

In addition, I posted the whole idea of restricted modules building as an open challenge to anyone willing to propose a method (or build some mock packages). Just use linux-restricted-modules sources (from dapper or edgy, whichever appropriate. Preliminarily, I'd say Dapper) and make it only build l-r-m-2.6.17*, not xorg-driver-fglrx, l-r-m-2.6.15, etc etc etc.

---

### Post by DJ_Max on 2006-06-24
[QUOTE=woedend]Right on.  With LTS kernel upgrades are a must.
How long did it take you to compile a single kernel package?[/QUOTE]
It depends on what your kernel configurations are, and your computer processor (note, not just how fast your CPU is, but the architecture). Usually it's 60mins. It also depends on whether you are doing anything on the computer while it's compiling. But it takes about 2hours on my iMac G3.

BTW, I can help compile PPC kernels. Right now I'm compiling the 2.6.17 kernel, but it's highly customized for my version mac. I have space and bandwidth and such, don't know how much time I'll have when I start college and my job part time.

---

### Post by DJ_Max on 2006-06-24
[QUOTE=pianoboy3333]I have build a 2.6.17.1 kernel for myself, but I don't have the restricted-modules package, so my wifi isn't working in it, and I can help on this project if you want.

Tell me if you know a way to get a restricted-modules package.[/QUOTE]
[http://ubuntuforums.org/showthread.php?t=104539&highlight=compile+ndiswrapper+source](http://ubuntuforums.org/showthread.php?t=104539&highlight=compile+ndiswrapper+source)
[http://ubuntuforums.org/showthread.php?t=85064&highlight=compile+kernel](http://ubuntuforums.org/showthread.php?t=85064&highlight=compile+kernel)

---

### Post by jdong on 2006-06-24
[QUOTE=DJ_Max]It depends on what your kernel configurations are, and your computer processor (note, not just how fast your CPU is, but the architecture). Usually it's 60mins. It also depends on whether you are doing anything on the computer while it's compiling. But it takes about 2hours on my iMac G3.

BTW, I can help compile PPC kernels. Right now I'm compiling the 2.6.17 kernel, but it's highly customized for my version mac. I have space and bandwidth and such, don't know how much time I'll have when I start college and my job part time.[/QUOTE]

Alright. These kernel packages will likely take around 5-6 hours to compile on the average modern CPU... My Core Duo can do it in about 2 hours, and my Athlon64 single-core takes the full 4 hours.

It goes through compiling all the various kernel flavors, and Ubuntu kernels are significantly bigger than vanilla kernels -- more than 50MB in patches.

---

### Post by DJ_Max on 2006-06-24
[QUOTE=jdong]Alright. These kernel packages will likely take around 5-6 hours to compile on the average modern CPU... My Core Duo can do it in about 2 hours, and my Athlon64 single-core takes the full 4 hours.

It goes through compiling all the various kernel flavors, and Ubuntu kernels are significantly bigger than vanilla kernels -- more than 50MB in patches.[/QUOTE]
Right, I should have stated I was referring to vanilla kernels from kernel.org.

---

### Post by pianoboy3333 on 2006-06-24
[QUOTE=DJ_Max][http://ubuntuforums.org/showthread.php?t=104539&highlight=compile+ndiswrapper+source](http://ubuntuforums.org/showthread.php?t=104539&highlight=compile+ndiswrapper+source)
[http://ubuntuforums.org/showthread.php?t=85064&highlight=compile+kernel](http://ubuntuforums.org/showthread.php?t=85064&highlight=compile+kernel)[/QUOTE]

Those look ok, it seems my TI (Texas Instruments) card needs the acx module to work, but when I boot into the 2.6.17.1 kernel, I can't modprobe it, is there a way to get the source for the acx module or something? Then I can compile it into the kernel.

---

### Post by zachtib on 2006-06-26
sounds like this is making progress, any news on when/if these will hit the repos?
and i could use a 686 build, btw... :D

---

### Post by bruce89 on 2006-06-26
[QUOTE=zachtib]sounds like this is making progress, any news on when/if these will hit the repos?
and i could use a 686 build, btw... :D[/QUOTE]
What about k8, k7, opteron and xeon ones as well?

---

### Post by ember on 2006-06-26
[QUOTE=pianoboy3333]Those look ok, it seems my TI (Texas Instruments) card needs the acx module to work, but when I boot into the 2.6.17.1 kernel, I can't modprobe it, is there a way to get the source for the acx module or something? Then I can compile it into the kernel.[/QUOTE]

From what I read, you need to get the newest source (0.9.1) from [http://www.madwifi.org]("http://www.madwifi.org") to build the module against kernel 2.6.17. Yet I have not tried it myself.

---

### Post by jdong on 2006-06-26
[QUOTE=zachtib]sounds like this is making progress, any news on when/if these will hit the repos?
and i could use a 686 build, btw... :D[/QUOTE]

Still working out the details; I wouldn't expect any packages within the next week or two... As I said, this is gonna be done carefully :)

---

### Post by The Noble on 2006-06-28
I'd be willing to help in this project, at least for a month or two(maybe more). I have followed one of the guides to install 2.6.16 and and still quite new to linux, but I have a few hours a day and I am definately willing to attempt some compiling of the new kernels. Leave a message in this thread or PM me, and I'll get be to those who need help.

---

### Post by savale on 2006-06-29
I should find the kernels in the backport repos when they are finished right?

---

### Post by The Soundophiliac on 2006-07-13
Any updates on the matter?

---

### Post by krazyd on 2006-07-14
Does anyone know if this is happening? I'd sure like to try a newer kernel. Hopefully it will fix my problem here:

[http://ubuntuforums.org/showthread.php?t=211138](http://ubuntuforums.org/showthread.php?t=211138)

---

### Post by matthew on 2006-07-14
jdong has been sick so the process has been delayed at best. Hopefully he will get well soon and have some time/strength to think about this.

---

### Post by philipacamaniac on 2006-07-14
A 2.6.17 kernel package would be extremely useful for me. I somehow managed to buy a new motherboard with an unsupported chipset (well, unsupported in 2.6.15, but supported in 2.6.16). So I won't have any 3D acceleration until that 2.6.17 dapper package shows up.

I'm an experienced Linux user, but not too experienced at compiling kernels. I have compiled a vanilla 2.6.17 with performance patches. I did it twice. First one didn't boot, and second one booted (without the yummy Ubuntu usplash) but couldn't complete the boot process. Then I downloaded the 2.6.17 source package from Edgy repos, and attempted to compile that sucker myself, using the 686 pre-made config. Of course, it wouldn't install because the module-init-tools dependency was compiled in, much like the already packaged 2.6.17 for Edgy.

It doesn't seem like too much work to make the modifications to get the Ubuntu Edgy 2.6.17 source compiled on Dapper, but I'm not experienced enough to know where to make those changes. I need it done, so I'll just be waiting for the backport, while in the meantime continuing my kernel compile experiements.

---

### Post by tseliot on 2006-07-15
> **philipacamaniac said:**
> It doesn't seem like too much work to make the modifications to get the Ubuntu Edgy 2.6.17 source compiled on Dapper,
Trust me, that's another kettle of fish... Backporting a kernel (for all the architectures) involves compiling the dependencies, the restricted modules the compilers (not always), etc. In other words it's not that easy

---

### Post by sebz2005 on 2006-07-15
Is there a single apt-get command that I can use to get the latest stable kernel?

---

### Post by matthew on 2006-07-15
> **sebz2005 said:**
> Is there a single apt-get command that I can use to get the latest stable kernel?sudo apt-get install linux-386

Keep that package installed and you will always have the latest stable kernel from the repos, including security updates. Note: you can also get linux-686, linux-686-smp, linux-k7, linux-k7-smp, linux-server, or linux-server-bigiron depending on your processor and its needs. If you aren't sure what you need, choose the 386 package.

---

### Post by ember on 2006-08-03
Any updates here? I tried Dapper point release and my problems with USB 2.0 are still not fixed.
I'd be able to compile a newer kernel myself, but the restricted modules trouble me.

---

### Post by hfdragon on 2006-08-04
I'm afraid you have olny two options to get 2.6.17 kernel :

- Wait for Edgy Eft (about 2 months from now).
- Compile yourself a new kernel (the option i choosed).

---

### Post by ember on 2006-08-04
The problem is not the kernel itself - it is building the corresponding restricted modules, i.e. I need both the nvidia module and the madwifi module.

---

### Post by skion on 2006-08-11
I compiled the kernel from git using this guide:

[https://wiki.ubuntu.com/KernelGitGuide](https://wiki.ubuntu.com/KernelGitGuide)
[https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)

which seems a great way to keep up-to-date while using an Ubuntu-patched kernel.

To solve a minor dependency problem for module-init-tools, you can point a deb-src line in sources.list to edgy and backport module-init-tools like this:

# apt-get build-dep module-init-tools
# apt-get --build source module-init-tools
# dpkg -i module-init-tools_3.2.2-3ubuntu3_amd64.deb

Seems to work so far...

---

### Post by saracen on 2006-08-12
If you want the latest patched kernel source from ubuntu all you have to do is change your /etc/apt/sources.list file to edgy instead of dapper.  Then do a:

```
sudo apt-get update
sudo apt-get install linux-source-`uname -r`
```

That will put the linux source as a tar.bz2 file in the /usr/src directory.  Change your sources back to dapper and then you can go ahead and recompile the kernel for your system [as per this thread]("http://ubuntuforums.org/showthread.php?t=217657").  Just skip the step where he downloads the vanilla kernel from kernel.org (the wget statement).

---

### Post by quik77 on 2006-08-29
just wondering if there is a guide anywhere that specifically covers the modules and patchs from Ubuntu, or anywhere I cna get the Ubuntu patch?

I ask because I recompiled the vanillia 2.6.17 patched with the emissions patchset (based off of the Ck patchset +extras) and the EVMS patch... and while its much faster... I don't seem to have Iptables? (so no firestarter firewall) and I get occasional problems with other programs that I don't know enough to fix.

SO is there a guide or can someone in this thread write one that goes into detail on patching and possibly gettign the ubuntu patches added.

I'm thinking something like Vanilla kernel +Ubuntu patchset +performence patchset of your choice + what restricted/normal modules you need and how to install them?

and if its already out there.. where is it? lol  as I go to college in about 3 days I sorta need the firewall pronto, and may have to go back to the old kernel for it >.< ](*,)

*update* found the stuff on Git and have set up my machine to get  access... However still have more questions... main one at least is now that I have access how do I go about getting the actual source and than can I safely apply the emission patchset and config for working uber dapper? or am I destined for a big mess ^^

---

### Post by Ramses de Norre on 2006-08-29
Is the backporting project aborted? It seemed very useful but there are no updates on it nomore.. (or at least not in this thread).
Are there still guys working on it or is it a no go for some reason?

---

### Post by jdong on 2006-08-29
Backports is still active, but there's not been much recent progress on kernel backporting... It's still a tough thing to do and requires more talking and planning.

---

### Post by Ramses de Norre on 2006-08-29
Oh ok, I was just wondering but this is good news! I'll wait untill you guys are finished, take your time ;)
And I wish I was able to help but I never compiled a kernel and I don't have the time to learn it right now.

---

### Post by jdong on 2006-08-29
There's gonna be a nice surge of around 20 or so backported packages, basically everything that's been asked for and approved up to this point, showing up in the repositories momentarily. Meanwhile, feel free to ask for updated packages at [https://launchpad.net/products/dapper-backports](https://launchpad.net/products/dapper-backports)


Kernels are big and complicated, and I'm not gonna pretend to be anywhere near as competent as the Ubuntu kernel team.... Especially in light of the xorg breakage two weeks ago, it's reminded all of us to be careful with pushing out updates :)

---

### Post by Underscore on 2006-09-04
any news on this subject?

---

### Post by jdong on 2006-09-04
I'm wondering if Edgy's kernels are compatible with Dapper... if so, then we can simply recompile them and use them in Dapper. That would even let us freeload on Edgy security updates :)

---

### Post by zachtib on 2006-09-04
> **jdong said:**
> I'm wondering if Edgy's kernels are compatible with Dapper... if so, then we can simply recompile them and use them in Dapper. That would even let us freeload on Edgy security updates :)

worth a shot, set up an extra box w/ dapper and have some fun :)

---

### Post by jdong on 2006-09-04
That'll be a while for me.. if someone else wants to give this a shot, please go ahead and do so!


I've dist-upgraded most of my dapper boxes to Edgy to debug a dbus breakage issue, and vmware is currently broken in Edgy, so I'm kind of out of testing mechanisms until I downgrade or spend some time fixing my vmware.

---

### Post by jdong on 2006-09-08
Another update:

The Edgy kernel debs will install on Dapper just fine, and will likely continue to do so thoughout Edgy's lifespan. There's no such guarantee on linux-restricted-modules from Edgy though, as Xorg userspace changes could introduce incompatibilities. Those who want ready-to-go 2.6.17 kernels can get Edgy kernels relatively easily then, with the most work being some restricted modules.

The Edgy kernels do not _build_ in Dapper's build environment though, which really complicates the backports issue :)


In another note, Ben Collins told me that since Dapper is a LTS release, they will consider "small backports", including new drivers, in Dapper's periodic kernel updates. The process is just filing a bug against linux-source-2.6.15 with keyword dapper-backport. If that is the case, I think most people are better off trying to get whatever's missing from Dapper's kernel into Dapper's kernel, then sticking with it for support convenience.

---

