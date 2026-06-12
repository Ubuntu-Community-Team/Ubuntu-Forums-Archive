---
title: "More security"
date: 2004-12-21
forum: The Cafe
---

### Post by nigelenki on 2004-12-21
What kinds of extra security should go into Ubuntu Linux?  I'm looking for transparent security, anything that doesn't bother the user.  SELinux policies are already going in, but they're easy to disable if they get in the way.  More transparent things won't need to be disabled.

Right now I'm looking at:

[list]
[*]IBM Stack Smash Protector
Stack Smash Protection prevents stack based buffer overflows from doing any real damage.  It even affords minimal protection to programs built without __guard creation and checking, by rearranging local variables.
[*]PaX
New enhanced memory protection policies fine-tune control over how program memory is set up to prevent foreign code from being injected.  It adds an NX bit on x86, and otherwise utilizes the existing bit to accomplish this.  It also randomly arranges the address space so attacks that don't rely on injecting new code will have to guess at where existing code is; the only way to reliably defeat this randomization is to inject code.
[*]GRSecurity
Some added control to lock things down even tighter.
[/list]

There's a wiki entry[1] on this as well, and an analysis of the USNs[2] to show how this would impact Ubuntu security.  Anything else transparent would be great.  An up-port of RexFBD[3] would be interesting, for example.

[1] [https://www.ubuntulinux.org/wiki/ProactiveSecurity](https://www.ubuntulinux.org/wiki/ProactiveSecurity)
[2] [https://www.ubuntulinux.org/wiki/USNAnalysis](https://www.ubuntulinux.org/wiki/USNAnalysis)
[3] [http://rexgrep.tripod.com/rexfbd.htm](http://rexgrep.tripod.com/rexfbd.htm)

There are others working on security hardening[4] Debian and Ubuntu.  Since I'm not doing any actual work, I'll just pass word along to them :)

[4] [http://debian-hardened.org/](http://debian-hardened.org/)

---

### Post by Lovechild on 2004-12-21
you should look at the thing RedHat uses for FC4:

[http://gcc.gnu.org/ml/gcc-patches/2004-09/msg02055.html](http://gcc.gnu.org/ml/gcc-patches/2004-09/msg02055.html)

---

### Post by nigelenki on 2004-12-22
[QUOTE=Lovechild]you should look at the thing RedHat uses for FC4:

[http://gcc.gnu.org/ml/gcc-patches/2004-09/msg02055.html](http://gcc.gnu.org/ml/gcc-patches/2004-09/msg02055.html)[/QUOTE]


1.  Date: 21 Sep 2004

IBM Stack Smash Protector is older than that.  It's several years old.

Furthermore, this has been in OpenBSD, Hardened Gentoo, and Adamantix for quite a while.

2.  Usage and effect

> 
The intended use in glibc is that by default no protection is
done, when the above GCC 4.0+ and -D_FORTIFY_SOURCE=1 is used
at optimization level 1 and above, security measures that
shouldn't change behaviour of conforming programs are taken.
With -D_FORTIFY_SOURCE=2 some more checking is added, but
some conforming programs might fail.


The IBM stack smash protector works for gcc 3.3 and 3.4.  If you use -fstack-protector it will protect functions in a compatible way.  Either way it rearranges variables and moves passed args down to new local vars so that buffer overflows can't damage these (no overhead).  The maximum overhead of __guard checking (sfp and retaddr) is 8% for a very tight function.  The overhead is incurred by extra code at the beginning and end; larger functions have a lower performance hit.  The overhead is only for functions with a local character pointer.  OpenBSD measures SSP overhead for -fstack-protector-all (to apply to everything instead of just functions with local character arrays) at 1.56%.

Protection in IBM SSP (ProPolice) is local vars, passed args, stack frame pointer, and return address.  The protection of these is complete.  Failure to protect occurs in structures (cannot be modified without breaking compatibility) where there's a pointer above a buffer.

3.  Redhat

Redhat is smoke and mirrors, like microsoft.  They make up their own crap because they're trying to look like they're magic, or something.

Redhat created Exec Shield in May, 2003 (one day after OpenBSD 3.3 with W^X).  PaX came along in October, 2000.  PaX still has 100% accurate NX emulation with a low (<1%) hit on x86, ES does not.  Brad Spender swears he has working ES exploits too (PaX has bugs in RandExec on AMD64, but I don't know about any actual exploits).  Adamantix and Hardened Gentoo use PaX; Hardened Debian probably will.

Redhat has a partial implementation of PIE; some binaries are position independent executables, but it's a joke (I've heard, not checked personally).  Adamantix and Hardened Gentoo do a full PIE base; Hardened Debian probably will.

Redhat is now what, re-inventing SSP?  The ProPolice implementation is as perfect as possible.  If it's not it can be improved.  OpenBSD, Adamantix, and Hardened Gentoo use ProPolice.  Hardened Debian is working on deploying ProPolice in Ubuntu and Debian.  Why the hell is Redhat reinventing it?




So . . . you want me to look at an immature project instead of a fully mature and actively maintained solution?  Hmm.

[http://gcc.gnu.org/ml/gcc-patches/2004-09/msg00348.html](http://gcc.gnu.org/ml/gcc-patches/2004-09/msg00348.html)
[http://gcc.gnu.org/ml/gcc-patches/2004-09/msg00373.html](http://gcc.gnu.org/ml/gcc-patches/2004-09/msg00373.html)

One last thing, the implementation for the IBM Stack Smash Protector.

[http://www.trl.ibm.com/projects/security/ssp/main.html](http://www.trl.ibm.com/projects/security/ssp/main.html)

---

### Post by Lovechild on 2004-12-22
actually we are using that thing with GCC 3.4 as well, it has already found several overflows in the packages in FC.

The overhead is lower, it can detect overflows at compile time and it's a common solution in gcc and glibc.

As for the exploits, I would like to see them, if they are there there's no reason to sit on them whipping up a storm with claims.. yes exec-shield is less secure than PaX, but how many desktop distros have PaX deployed and working... NONE. I welcome you to fix every single misbehaving app to get it in a working PaX environment, just ask the hardened Gentoo team how big a job that is.

---

### Post by nigelenki on 2004-12-22
> **Lovechild]actually we are using that thing with GCC 3.4 as well, it has already found several overflows in the packages in FC.
[/QUOTE]

Been using ProPolice in Hardened Gentoo for a while.  It's also in OpenBSD and Adamantix.

> 
The overhead is lower, it can detect overflows at compile time and it's a common solution in gcc and glibc.


ProPolice symbols are in Gentoo glibc.  I never notice any performance detriment from SSP-- which is what counts.  If you have a 75% performance overhead, but never touch over 10% CPU, and all tasks still execute in the same realtime timeframe, you have no performance detriment.  Realistically we like to keep the numbers low (1-2% in total is nice) because as we increase them, we increase the probability distribution of reaching 100% CPU and thus slowing down said:**
> 
As for the exploits, I would like to see them, if they are there there's no reason to sit on them whipping up a storm with claims.. yes exec-shield is less secure than PaX, but how many desktop distros have PaX deployed and working... NONE. I welcome you to fix every single misbehaving app to get it in a working PaX environment, just ask the hardened Gentoo team how big a job that is.

Brad SOLD them  :/  He's under NDA or something, so he can brag, but can't divulge the exploit.

I ran full PaX on x86 (Athlon XP Thoroughbred and Barton) and x86_64 (Athlon 64 Clawhammer).  No problems for me.  I have working Java, Flash, etc.  Had working 3D for a while with Nvidia's drivers; but that is a particular pain in the ass, and the newer Xorg servers i use dislike the nvidia driver anyway (even on a non-hardened install).

I was maintaining this for a time . . . [http://bugs.gentoo.org/show_bug.cgi?id=40665](http://bugs.gentoo.org/show_bug.cgi?id=40665)  Surprisingly few packages seem to break.  Marked off are:

 - Java (SunJDK/JRE, BlackdownJDK/JRE)
 - Wine
 - X11 (without dlloader; newer Xorgs will not need it)
 - Xine (3D*)
 - OpenOffice.org
 - xmms (ALSA trampoline, will be fixed)
 - mplayer (3D*)
 - mono
 - xscreensaver (3D)
 - zsnes (assembly code using immediate addressing and self-modifying the operands)
 - totem
 - acme
 - gnome-sound-recorder
 - xfce4-panel
 - blender (3D*)
 - bzflag (3D*)

*Most 3D apps will die under PaX due to some obscure bug in libGL or something, which gets them killed.  Fix that and you fix ALL THOSE.

That's 16 (counting Java as 1; there's something like 5 JDKs).  I'll also give you Qemu, which I know will break due to design.  17.  For now, these can just come marked, and they'll work.  A redesign will help ensure security, though.

Qemu will always need mprotect() restrictions off; the Qemu guys can design Qemu to use mprotect() and keep up a secure environment.  Qemu is designed to emulate a machine in realtime, and so cannot handle the hit of trying to generate tiny bits of code on the fly, dump them into files, and mmap() them in.

Java and Mono can use [a more secure design](http://www.kaffe.org/pipermail/kaffe/2004-October/099938.html) to function with full PaX.  These are batch execution jobs; they build an executable from bytecode, then run it.  In the beginning, they have everything they need to build all of the code they need (unlike realtime machine emulators), and so they can build directly to shared objects, dump to disk, and mmap() in without producing a visible slowdown.

Wine I'm not sure about.  It can probably be made to work under full PaX, but it runs programs we have no control over.  I don't think Wine could ever get everything; though getting down to just mprotect() restrictions being relaxed is probably possible.

X is being fixed.  I've heard that dlloader will be officially replacing the elfloader; this is good.  Fixing libGL (or libGLCore, one of those) will also fix all 3D apps dying from GL kills.  I don't know if this is general GLX, Nvidia, or MESA.

zsnes needs a rewrite of the inline assembly used in some parts of it.  Somebody did that, but didn't send up the patch.

OpenOffice.org, totem, gnome-sound-recorder, acme, and alsa just need some debugging.  libalsa has a trampoline in it (hence the xmms marking), but I've never seen it get anything a kill.

---

### Post by Lovechild on 2004-12-22
okay then.. code speaks louder than words.

get it work without hassle and I'll worship the ground you walk on, I too want better security.

---

### Post by nigelenki on 2004-12-23
Lorenzo's doing a good job of that.  :)

Having a PaX-enabled system work out of the box is easy enough; you just have to make sure your packages come with properly marked binaries for whatever period it is that they don't get fixed.  Lorenzo (Hardened Debian developer) is also bringing PIE and SSP to Debian/Ubuntu, and making binutils spit out binaries with a PT_PAX_FLAGS field in the .load segment (*the official control field for PaX; EI_PAX is a hack using an unused field*).

I made a pax-flags script that uses /etc/pax.conf to find and mark up binaries, based on the Gentoo init.d scripts.  I tweaked it for Debian and ran on there; pax-flags and pax.conf are at the below URI:

[http://d-sbd.alioth.debian.org/www/pax/](http://d-sbd.alioth.debian.org/www/pax/)

There is also a 3 phase demonstration of non-pax, PaX breaking things and PaX markings to have them work, and marked binaries running under a paxless kernel.  This demonstrates how to temporarily handle PaX incompatibilities so that everything still works; the real solution is to rewrite the software to work with PaX.



ANYWAY, I was looking for other things that may be feasible to deploy, like something akin to FormatGuard, but without the ugly 37% overhead (way too high to consider; PaX on x86 does <1%, SSP does ~1.5% according to openbsd).

---

