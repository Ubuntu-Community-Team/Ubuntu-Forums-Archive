---
title: "how to put jack.pc in pkg_config_path?"
date: 2011-04-12
forum: Ubuntu Studio
---

### Post by poodoopealeoaph on 2011-04-12
Alright... so I've followed some friendly advice from another thread and have embarked on the attempt to compile the source for guitarix head and when I try to run the script I get this...
```
:~/Downloads/gx_head-0.14.0$ ./waf configure
Checking for program msgfmt              : /usr/bin/msgfmt 
Checking for program intltool-merge      : /usr/bin/intltool-merge 
Checking for program g++ or c++          : /usr/bin/g++ 
Checking for program cpp                 : /usr/bin/cpp 
Checking for program ar                  : /usr/bin/ar 
Checking for program ranlib              : /usr/bin/ranlib 
Checking for g++                         : ok  
Checking for jack <= 1.8.0               : Package jack was not found in the pkg-config search path.
Perhaps you should add the directory containing `jack.pc'
to the PKG_CONFIG_PATH environment variable
No package 'jack' found 
Checking for jack >= 1.9.1               : Package jack was not found in the pkg-config search path.
Perhaps you should add the directory containing `jack.pc'
to the PKG_CONFIG_PATH environment variable
No package 'jack' found 
/home/adam/Downloads/gx_head-0.14.0/wscript:371: error: the configuration failed (see '/home/adam/Downloads/gx_head-0.14.0/build/config.log')
```

So, I know that I have to put the jack.pc file in the pkg_config_path but I'm not exactly sure where this path is... is there any advice on how to get something like this working?

---

### Post by Pablo_F on 2011-04-12
Hi, 

Most probably, you have not installed libjack-dev package. Install it and try again.

Cheers, Pablo

---

### Post by sgx on 2011-04-12
I think you will be successful by installing guitarix using dpkg -i

Guitarix has a few dependencies, which are all listed here, but most are already in your system:

[http://packages.debian.org/unstable/sound/guitarix](http://packages.debian.org/unstable/sound/guitarix)

click the architecture you have from the list, i386 is here:

[http://packages.debian.org/sid/i386/guitarix/download](http://packages.debian.org/sid/i386/guitarix/download)

dpkg -i guitarix_0.11.1-1_i386.deb

This command will report missing dependencies, so download them and install
them first. You can use synaptic for this, as most dependencies are standard system files. libzita-convolver is the one that is not in most systems.

Guitarix is a complete setup, clicking various modules opens their gui,
so you don't need to clutter your screen with unused portions. If you have some IR files, they can be utilized in the convolver page

I think the jackd.pc thing is someones old wacky-tobaccy typo moment

Cheers

---

### Post by Pablo_F on 2011-04-13
Hi,

Well, I recommend gx_head rather than guitarix. gx-head is based on guitarix but imho, the sound is better and the gui is much nicer and more intuitive. A bonus is that it has two independent modules with input and output jack audio ports, the amp and the effect box. So you can combine gx_head with rackarrack effects, for example. In addition, it has good presets contributed by users. 

The last version (0.14) was announced two or three days ago and brummer is not maintaining guitarix anymore, afaik. 

Compiling gx_head is not difficult because all the tools and dependencies are in the repos. Of course, it would be easier if one of our beloved PPA packagers did the job. Afaik, gx_head 0.14 is not yet ready in any PPA.  

As for the original subject, at least in lucid, libjack-dev installs jack.pc in /usr/lib/pkgconfig (check in synaptic, libjack-dev properties, installed files) so you don't have to put it there manually, just install libjack-dev. 

Cheers, Pablo

---

### Post by zettberlin on 2011-04-13
> **Pablo_F said:**
> Hi,


As for the original subject, at least in lucid, libjack-dev installs jack.pc in /usr/lib/pkgconfig (check in synaptic, libjack-dev properties, installed files) so you don't have to put it there manually, just install libjack-dev. 

Cheers, Pablo

EVERY -dev-Package installs the pc-file for pkg-config.
In fact this message is misleading -- took me 2 days to find out, some 7 years ago ;-)

If you have all the dev-packages a program depends upon installed and you still get this message, then one of the dependencies could be too old. But a dev-package, that does not care for pkg-config would be considered broken...

---

### Post by sgx on 2011-04-14
Thanks for the correction info. I checked my system, which has no, or few -dev packages, and no compiled apps. Should have greatly expanded my google search!
Cheers

---

