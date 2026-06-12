---
title: "Trouble Compiling Wine on Intrepid"
date: 2009-06-15
forum: Wine
---

### Post by ackanao on 2009-06-15
Hi all,

I'm trying to compile Wine 0.9.53 on Intrepid (32-bit) for a couple of days now but with no success. The problem is that the "stable" version of Wine works perfectly but there's one application I can't get to work with recent versions of Wine while it works flawlessly with Wine 0.9.53; I've tried probably a dozen different versions including latest one (1.1.23).

So I choose to compile Wine 0.9.53 from source and install it in a different folder - in that way I can "switch" from one version of Wine to another with ease.

build-essential and build-dep wine are installed and I use install-wine-deps.sh script from official Wine Wicki to be sure that I have all dependencies needed for compiling Wine.

I have no problems when compiling 1.x versions of Wine but whenever I try to compile 0.9.x versions I get some errors (I've tried 0.9.53, 0.9.52, 0.9.54 to see what will happen).

This is the error I get:

```
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__ -D_NTSYSTEM_ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith  -g -O2  -o signal_i386.o signal_i386.c
signal_i386.c: In function &#8216;merge_vm86_pending_flags&#8217;:
signal_i386.c:502: error: &#8216;VIF_MASK&#8217; undeclared (first use in this function)
signal_i386.c:502: error: (Each undeclared identifier is reported only once
signal_i386.c:502: error: for each function it appears in.)
signal_i386.c:513: error: &#8216;VIP_MASK&#8217; undeclared (first use in this function)
signal_i386.c: In function &#8216;raise_vm86_sti_exception&#8217;:
signal_i386.c:1086: error: &#8216;VIP_MASK&#8217; undeclared (first use in this function)
signal_i386.c: In function &#8216;__wine_enter_vm86&#8217;:
signal_i386.c:1486: error: &#8216;VIF_MASK&#8217; undeclared (first use in this function)
signal_i386.c:1487: error: &#8216;VIP_MASK&#8217; undeclared (first use in this function)
make[2]: *** [signal_i386.o] Error 1
make[2]: Leaving directory `/home/memyself/Desktop/wine-0.9.53/dlls/ntdll'
make[1]: *** [ntdll] Error 2
make[1]: Leaving directory `/home/memyself/Desktop/wine-0.9.53/dlls'
make: *** [dlls] Error 2
```

Can someone help me with this - thanks in advance
(sorry for my bad English)

---

### Post by Meow27 on 2009-06-15
question: why do you need to compile it?

another question: have you tried playonlinux?

---

### Post by ackanao on 2009-06-15
Hi Meow27,

About your first question:

As far as I know you can't install older versions of Wine on Intrepid unless you downgrade libldap2; Besides, I just want to have "stable" version of Wine installed on my system by default and all other versions of Wine in a folder I choose - If I'm not mistaken there's just one way I can achieve that and that is by compiling Wine and set install folder to the desired location (ex. ./configure --prefix=/home/myself/wine-0.9.53)

About POL:

Yes, I have POL installed and I must say that it is, by far, the most useful frontend for Wine I've seen (even more useful than CrossOver). 

But there are some problems with POL, for instance, if you want to use your own "heavy patched" version of Wine with POL you have to "hack" around to achieve that. Another problem is that Wine in POL behaves differently than Wine in Ubuntu repo's - I guess that comes from how Wine is compiled. For example, when I use the latest (1.1.23) version of Wine from repo's, game won't install at all (crashes instanly); When I use POL's 1.1.23 version of Wine game installs without the problem (but bug is still there)

I just want to have my own copy of Wine 0.9.53 because I don't want to depend on POL or Ubuntu repo's...

---

### Post by NightMKoder on 2009-06-15
That wine version is REALLY old and that's why you're having trouble compiling. Those identifiers were renamed in the kernel headers, so you will need a patch similar to
[http://www.mail-archive.com/pld-cvs-commit@lists.pld-linux.org/msg156762.html](http://www.mail-archive.com/pld-cvs-commit@lists.pld-linux.org/msg156762.html)

Or you can just file a bug in wine and help 1.1.24 run it :)

---

### Post by ackanao on 2009-06-16
Hi NightModer,

I've realized that yesterday when I tried to compile Wine from Git - I didn't test all 0.9.x versions but it seems that you just can't compile them on Intrepid; I doubt that the problem is in missing dependencies it is more likely that the problem is with kernel headers - So I choose to install additional linux-headers packages from repos but that didn't solve the problem...

If you're talking about bug for the game itself, it's already reported (not by me) - I've posted my findings on bugzilla already. Although the bug is submitted only recently it's obvious that it's at least a one year old. Maybe the future versions of Wine will resolve this issue, untill then, only viable option is 0.9.53 version of Wine.

Now, about compile issue (thanks for the link btw.) - Do you have any idea how to resolve this because if you use Intrepid (and probably Jaunty) it seems that you can't compile any versions of Wine prior to 1.x and that's a big problem in my opinion - unless I'm missing something obvious (that would be really embarrasing for me but that don't bothers me that much)

---

### Post by ackanao on 2009-06-16
**UPDATE**

I choose to set-up Hardy in a VirtualBox and then try to compile Wine 0.9.53; As expected, Wine compiles with no problems at all.

Obviously, there's a problem between linux-headers shipped with Intrepid and older versions of Wine and I don't know any workarounds for this...

I'll try to compile Wine later today on Jaunty to see whether this problem exists on Jaunty or not; In any case, can someone tell me what to do - I don't know whether to submit bug report or not and I don't know where to submit it (on Ubuntu launchpad or at Wine bugzilla) ?

---

### Post by ackanao on 2009-06-21
I've found the solution for compiling old versions of Wine on a modern Ubuntu system - that is if you encounter a similar error as I did (error in signal_i386.c file):

1. Unpack Wine source and then goto "**dlls -> ntdll**" folder;
2. Open signal_i386.c file and add these two lines next to do others #define:

```

#define VIF_MASK 0x00080000
#define VIP_MASK 0x00100000

```

I've put them in "**signal context platform-specific definitions**" just at the end of **#ifdef linux**

This should also work with other 0.9.x versions of Wine if you compile Wine on Intrepid (I didn't have problems compiling Wine on Hardy, don't know for Jaunty).

I'm also doing "Reverse Regression Testing" but it will take some time to find a patch that fixes this problem.

Well, most of my problems are solved - I still have minor issues but that's another topic...

---

