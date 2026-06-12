---
title: "Building Ubuntu from source PPAs, or is this a complete mess?"
date: 2010-11-17
forum: The Cafe
---

### Post by czr114 on 2010-11-17
Work with me here, because this idea is a bit out there.

Many of us are familiar with [Gentoo Linux](http://en.wikipedia.org/wiki/Gentoo_Linux). For those who aren't, the basic concept behind Gentoo is that it is a distro whose repositories are filled with source, which is dynamically compiled by the user's machine.

This can provide a substantial boost to performance, simply by invoking the compiler to take advantage of processor-specific optimizations.

The problem with Gentoo is that it's a royal pain to install and maintain, among other things. All in all, I'd still rather run a stock Ubuntu than an optimized Gentoo.

In a perfect world, Canonical would have Launchpad set up with unlimited CPU and disk space, and could afford to build a branch for each major CPU architecture. Maybe one day this will happen, but until then, there is an opportunity to build a highly-optimized system on the client machines.

I'm trying to collect some thoughts on how the source PPAs might be used to accomplish this goal. I'm not that familiar with package management in Ubuntu, which is why I'm taking this opportunity to think out loud.

It might be possible to override apt, by abstracting the software sources, and running a source fetch and build prior to package installation, with the freshly built binary being passed to apt from local storage.

It might also be possible to script the fetching and compilation of all packages as part of the standard Ubuntu installation, replacing them and the md5sums on the ISO prior to installation.

I do know that Launchpad is autobuilding the binaries we use, so adding in an autobuild targeted to the client machine, on the client machine, would need only make use of that code, albeit in a local context.

Can anyone with more knowledge of package management enlighten me as to whether this is even remotely within the realm of possibility, or whether it's so far out there as to be a complete and total mess?

Being able to code up such a setup would be a benefit to everyone, from the desktop user who wants more from his hardware, to the netbook user who needs the efficiency of properly-built packages to prolong battery life, to the user on a budget who can't afford new hardware, or to the educational institution which needs to get the best of a limited budget.

With 2% of the world's electricity consumption being used for computing, global use of better compiler optimization could make for a substantial cut, particularly among Ubuntu server farms, or in the ever-expanding cloud. Of course, for this to offer the best improvement, it would have to be done centrally at Launchpad, although end-users could also see a benefit from taking the hit at installation time to ensure the highest quality binaries are used in everyday operation.

Fetching source or optimized binaries through the PPAs might also be able to bring update bandwidth requirements down.

Am I even within the ballpark on this one?

---

### Post by amauk on 2010-11-17
For x86, the need to compile for specific sub-sets of the architecture (386, 486, 586, 686) has long, long past

The kernel can detect your CPU capabilities at run-time and enable/disable optimisation features on the fly

AFAIK, all programs on the x86 architecture are compiled (and therefore optimised) for the highest x86 version (i686)
They are however "generic" x86 as a whole, meaning the compiler also generates fallback code in case the CPU does not have a specific post-386 feature

The only benefit to the Gentoo way of source compiling is slightly smaller binaries (Ie. no unused fallback code)

---

### Post by czr114 on 2010-11-17
I can't speak to the specific nature of the internals of these optimizations, but I have seen substantial performance increase by targeting a build to my machine architecture, over binaries in the CentOS repos, on both x86 and x64. I can speak for Apache, PHP, ImageMagick, GD, OpenSSL, ffmpeg, LAME, zlib, and a few others, that is, unless something has changed in the last year concerning how compilers are optimizing binaries. When I had that support contract, we were seeing gains up to 1/3 on some of the media processing when built for the latest Intel chips, using standard gcc. It was worthwhile enough to keep doing it.

The size issue alone would be useful in reducing the system's overall memory footprint for binaries loaded into RAM, and making more efficient use of CPU cache by reducing RAM hits.

---

### Post by 3Miro on 2010-11-17
I use Gentoo and I am also somewhat familiar with Lunar Linux. Both source distributions. If you have experience with Gentoo and Lunar's repository you can see how they are build to let you customize your system. Portage has use flags and Lunar leads you through a series of "true/false" questions. There is nothing like that in Ubuntu's repo. You can perhaps do a customization for your CPU architecture and in the case of x86, this will probably lead to some improvement in performance, but overall it will be small (too small to be worth the trouble IMO). On x86_64, the difference in performance will be even smaller.

You can try with something simpler first. Recompile key parts of the system only. Do the kernel first, it is not very hard and it is by far the most important part of the system. Then you can do some other key applications/libraries. You don't have to do he entire system, just large parts of it.

---

### Post by czr114 on 2010-11-17
It is too small to be worth the trouble on one system, however I'm more interested in something that can benefit the whole community. Getting the ball rolling on that, or being a part of the project, would be something that might be worth the effort.

I'm currently running a custom built kernel, if only to test the recent process scheduling patch.

I just don't see the benefit in doing this in isolation on one system, which is why I chose the ease and hassle-free nature of Ubuntu over the performance or customization of other distros. I suspect that most power users on Ubuntu have had similar thoughts.

The key to this has to be the ease and transparency, otherwise it becomes a chore for the manual builders, and impossible for those with limited Linux experience. If it could be done seamlessly and transparently for everyone, then it might be worth it. Even a few percent faster execution and reduced binary size, system wide, would make sense for a broad, distro-wide implementation.

---

### Post by lykwydchykyn on 2010-11-17
You may want to look at apt-src, which is a tool for very easily downloading and building sources directly from the repositories.  I don't know that you get any specific optimizations from this method, at least not without editing the build scripts (that'd be the debian/rules file in the downloaded sources), but you may get some architecture-specific optimizations, don't know.

The only thing is, you have to have at least a minimal system installed to start using it, and if there are build dependencies it downloads them automatically as binaries.  If you just want to target specific parts of the system, it might be an easy way to begin.

---

### Post by czr114 on 2010-11-17
Thanks, apt-src and apt-build seem to be what I'm looking for, albeit I still have a few questions to resolve with regard to handling of updates through Ubuntu's update manager after a world build. I'll test an apt-build world in a VM, first, in case it wants to hose a running system.

---

