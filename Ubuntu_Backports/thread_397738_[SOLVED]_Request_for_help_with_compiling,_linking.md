---
title: "[SOLVED] Request for help with compiling, linking"
date: 2007-03-31
forum: Ubuntu Backports
---

### Post by benblout on 2007-03-31
I found a small piece of software I would like to use on my Dapper system.
In order to compile it, I had to install a newer version of libhid-dev, which ended meaning I needed 4 packages from Edgy to satisfy the various dependencies

libc6_2.4-1ubuntu12_i386.deb
libhid-dev_0.2.15+20060325-2ubuntu1_i386.deb
libhid0_0.2.15+20060325-2ubuntu1_i386.deb
libusb-0.1-4_0.1.12-2_i386.deb

After they installed, my small program compilied just fine, and ran just fine.  However, even though these four packages, when installed together, don't break *any* dependencies, the system isn't happy - there are immediate warnings about locale settings, and I worry about what else will be broken with an ugrade of libc.

So my goal is to compile and link this program so that it will run on standard Dapper system.  I know this isn't exactly backporting, but I thought people who did do back porting would be more familiar with these issues.

I made slight progress - by specifying the libraries on the command line for gcc, I can get the program to compile and link on a stock Dapper.  And if I compile and link it with the extra libraries installed, I can make use of the LD_PRELOAD and LD_LIBRARY_PATH variables to have it run a tiny bit on a stock Dapper system - but it is not functional.  

Any suggestions would be great.
Any suggestions about *where* or *who* to ask likewise great.
If helpful, I can provide any further information.
And of course, if this is too off-topic here in backports, my apologies, and I'll run off to an other part of Ubuntu.  :-)

-Ben

---

### Post by xopher on 2007-04-04
My suggestion is - frankly - to do a dist-upgrade (or two for that matter). It might seem like a big thing to do, but it's really easy and quite safe.

You wouldn't want to run windows98 when there's windows 2000 and XP available?

Just a thought.. :rolleyes:

And those are packages that don't backport well, so basically you won't get that app to work properly within dapper. Correct me if I'm wrong, but that's what I think.

---

### Post by benblout on 2007-04-04
> **xopher said:**
> My suggestion is - frankly - to do a dist-upgrade (or two for that matter). It might seem like a big thing to do, but it's really easy and quite safe.

You wouldn't want to run windows98 when there's windows 2000 and XP available?

Just a thought.. :rolleyes:

I have considered it.  The machine I am on now has been dist-upgraded from 4.10 to 5.04 to 5.10 (for a few hours) to 6.06.  I really like the idea of just sticking with one version for a while - upgrades end up taking a lot of time.  Plus I am responsible for maintaining seven machines for various friends and family members, and having everything run the same version is very nice.

And to answer your rhetorical question, if windows 98 worked well for what I wanted, then I would stick with it.  I actually stuck with OS/2 up until Debian Woody was in beta, to give you an idea of how quickly I adapt new versions!

-Ben

---

### Post by benblout on 2007-04-04
> **xopher said:**
> And those are packages that don't backport well, so basically you won't get that app to work properly within dapper. Correct me if I'm wrong, but that's what I think.

Well, I can't correct you, that is for sure!

In case I was not clear enough, I am not trying to backport those four packages.  In fact, I only need to upgrade two packages (libhid0 and libhid-dev, which drag in the other two as dependencies.

I have the thought that a statically compilied version of my program would be the answer, but how to create such a thing is beyond me.   I poked at it for a few hours without success before giving up.  Do I even understand the situation?  Would a statically linked version of my program run correctly?

Thanks,

Ben

---

### Post by benblout on 2008-01-21
I finally got this figured out.  Not sure why it is working, but it is.  And in the interest of being helpful in the case anyone else stumbles onto this thread, I'll relate what worked for me.

This is on a Dapper system, and the program I wanted to compile was shark.c.  And for any search engines, this is the program that controls the Radio Shark (Radioshark).  I put the libraries I needed in a directory that I called 'libraries'.  (These all came from Edgy packages.)
```
~/radioshark $ ls libraries/
ld-linux.so.2  libc.so.6  libhid.so.0  libusb-0.1.so.4
```
I needed two of the newer libraries for shark.c to compile, so I specified both on the cc command line.  I also stumbled on a magic option to pass (via the -Xlinker optino) to the linker:
```
~/radioshark $ cc -o sharktest -Xlinker -rpath -Xlinker libraries/ libraries/libhid.so.0 libraries/libc.so.6 shark.c
```
I need to use sudo to run the program.  But the key thing I stumbled on was to use the newer ld-linux.so at run time:
```
~/radioshark $ sudo ./sharktest -red 0 Password:
Segmentation fault
~/radioshark $ sudo libraries/ld-linux.so.2 ./sharktest -red 1
```
And that last line *works*

---

