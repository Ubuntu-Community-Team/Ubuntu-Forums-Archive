---
title: "ENV / GCC / SS Optimizations"
date: 2010-03-08
forum: Server Platforms
---

### Post by Tlon on 2010-03-08
I couldn't find a forum listing that seemed appropriate for this discussion, so I thought I'd toss it in here...

I'm building a custom task-specific server -- it's primary purpose is to process data to feed into another server for public consumption. The applications I've put together are extremely resource-intensive, so I want to get the most out of my hardware.  My problem is that I haven't yet found a good way to do that with Ubuntu. What I'm trying to do is trivially easy on Gentoo or OpenSolaris, but I'm not crazy enough to run the former in a production environment, and I've been non-plussed with OSOL's multimedia support.  What I want is a base system built on stable binaries, with add-on repos that would compile under a set of optimized options, and could be updated accordingly (basically, a deb-based version of CAOS).

I *thought* I had found this with apt-build, but for some reason it doesn't seem to be passing the flags I've assigned to it.  Here's apt-build.conf:

> 
build-dir=/var/cache/apt-build/build
repository-dir=/var/cache/apt-build/repository
Olevel=-O3
mtune=-mtune=native
options=" -msse4.2 -m64 -march=native -fprefetch-loop-arrays -funroll-all-loops -mpclmul -maes -myeclibabi=syml -fprofile-correction, -W1,-z common-page-size=2M"
make_options="-j9"


System is 2x Intel Xeon X5570's, each tied to an independent IOH-36D hub, 48GB RDIMMs.

The apt-build repo list IS fully populated, taken right from the system's list, hand-purged of packages that I don't want to be apt-built (kernel, etc.).

GCC is 4.4.1. I've just learned that at least one of those flags isn't supported until 4.4.3, so that's something I'll have to address, but there are still several lingering issues.

1) During build, I'm told that my system is being treated as a generic amd64 system.

2) During build, I'm told that O2 optimizations are being used.

3) During build, I'm often presented with GCC options that I know I did *not* specify

4*) System monitor output isn't indicative of -j9 performance; rather, I get one thread (!) at 100%, and a second thread at 10-15%... obviously, far from optimal.

5) None of this addresses what to do for CPPFLAGS.  I don't *want* CPPFLAGS cloning CFLAGS; there are supplemental options that I want that would break C compilation if I were to include them in my base options.

6) I can't, for the life of me, figure out where compiler and make options are supposed to be set.  I used Ubuntu ages ago, but then forked between Gentoo for my tinkering fetish and OpenSolaris for my workstation purposes. In either of those, setting these variables is easy as pie. In Ubuntu, I'm at a total loss. Where, exactly, are the flags for GCC/G++ set in Ubuntu?

7) Assuming I can get it to work correctly, is there any way to ensure that apt-build rebuilds the DEPENDENCIES it installs in the process of installing whatever's specified, rather than installing the dependencies as simple binaries? It seems dangerous to have optimized binaries dependent upon sluggish deps.

* -j9 is beccause I don't want to devote my entire system to compilation... one CPU is more than enough, and the machine has other things to do.

Other things I'd like to be able to do is switch between GCC / SunStudio / and Intel Compiler 11.1 with relative ease (e.g., a command-line switch would be nice).

** Quick Edit: system started as a vanilla Ubuntu 9.10 Server install.  After that, basic packages (including apt-build) were added, and xubuntu-desktop was installed (via apt-build).


Thank you very much, for all of you out there who take the time to read through this and offer whatever constructive help that you can. The hardware I'm using is grossly under-rated for my purposes, and it's enormously frustrating trying to make heads-and-tails out of all of this. Many, many thanks.

Tlon

---

### Post by walmartshopper67 on 2010-04-03
Sorry it's taken so long for a reply - i *just* succeeded in getting distcc to work with apt-build, it was a huge pain. Apt-build is kind of buggy, and as far as i've been able to find, the development has stalled. Some of your problems *might* be caused by the apt-build 'wrapper' script, which calls make with the options/data stored in the apt-build.conf file. Try running apt-build with the --nowrapper option to disable it and see what's going on in the output. Also, if apt-build isn't calling distcc at all (check by running the distccmon-text command **as root** (because apt-build must be run as root), try setting the CC variable to "distcc" (i.e. export CC="distcc" on the command line). 

as for apt-build building it's dependencies instead of just installing them, it doesn't and i really haven't found a good way around that except by hand. That's one thing that could be addressed if apt-build development were to continue...

---

