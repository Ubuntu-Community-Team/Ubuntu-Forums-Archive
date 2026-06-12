---
title: "Backport: Kernel 2.6.10-2 from Hoary"
date: 2005-01-25
forum: Ubuntu Backports
---

### Post by jdong on 2005-01-25
**Synopsis**
2.6.10 has been considered one of the MOST stable kernels in the 2.6 series (Kerneltrap). For me, it solves lots of ACPI and DVD burning issues. For others, it adds certain new drivers

**Backporting process**
In addition to the kernel, updated kernel-wedge (build tool) was backported. Later, I realized a new initrd-tools , which is coming along in the next revision.

**Packaging Status**
i386: Linux-image's of revision 11, Metapackage staging as of revision 13, Restricted Modules staging as of revision 14
ppc: Nope
amd64: come on, take a guess.

---

### Post by jdong on 2005-01-25
NOTE: still working on Linux-restricted-modules.

---

### Post by jdong on 2005-01-25
Ok, Restricted modules are uploading, everything else is already in staging . I'll be testing it in a second, will report back after I reboot into this kernel.

---

### Post by jdong on 2005-01-25
2.6.10-2 i386 and k7 packages confirmed fully functional for me -- including 3-D Nvidia drivers. Need to test CD burning, but it LOOKS GOOD!  8-)

---

### Post by nehalem on 2005-01-26
Does this include better bluetooth support.  The 2.6.8 included support for bluetooth but not keyboards and stuff (I have a keyboard and mouse).  I believe it's called HID support.  Regardless I'm going to try it :)

Thanks.

---

### Post by nehalem on 2005-01-26
So installed it and everything works great .... except jedit runs quite a bit slower.  It takes a while longer to refresh, scroll, etc.

I'm curious what the culprit is with it???

---

### Post by kleeman on 2005-01-26
Any chance of a 686-smp version? (he says hopefully ;-))

---

### Post by jdong on 2005-01-26
[http://cloud9.homelinux.net:81/ubuntu/backports/dists/warty-backports-staging/main/binary-i386/](http://cloud9.homelinux.net:81/ubuntu/backports/dists/warty-backports-staging/main/binary-i386/)

linux-image-2.6.10-2-686-smp_2.6.10-11_i386.deb

It's already in there.

---

### Post by kleeman on 2005-01-26
Oops should have looked instead of extrapolating the i386 you mentioned. Thanks a lot!!!

---

### Post by jdong on 2005-01-27
I use i386 in the same sense Debian uses it: Intel 32-bit x86 architecture.

---

### Post by faqpete on 2005-02-11
Hi!
Since I discovered Ubuntu Warty as a goodie in a pc-magazin I'm using this great distribution on my laptop (acer 1522wlmi). To get my IPN2200 wireless-adapter work (built in) I installed ndiswrapper with the xp-driver - works like a charm ... till I switched to Kernel 2.6.10-2 - no chance to get ndsiwrapper to work. So is it possible, to make a backport from 2.6.10-3? This may hopefully solve my problem  :-?  ?
Thanks for your great work, and excuse my "bad" english

faqpete

---

### Post by jdong on 2005-02-11
I think Ndiswrappers will have to be recompiled for the new kernel. I'll try to get that done!

---

### Post by emperor on 2005-02-13
When will the 2.6.10 kernel be released from staging?

---

### Post by jdong on 2005-02-13
Everything looks good, except the ndiswrapper issues. So is that a show-stopper?

---

### Post by jdong on 2005-02-13
It seems as if you need to install ndiswrapper-source, and use module-assistant with kernel headers to recompile the module.

---

### Post by jdong on 2005-02-14
Does anyone object to this kernel moving to stable? Maybe stable/bleeding?

---

### Post by rufius on 2005-02-14
[QUOTE=jdong]Does anyone object to this kernel moving to stable? Maybe stable/bleeding?[/QUOTE]
 I would go with stable/bleeding jdong. Sounds like a place for it to be, not too much risk someone will install it unwittingly.

---

### Post by lerrup on 2005-02-15
sorry to be thick, but how do I update by system to this/where is it?

Cheers.

---

### Post by jdong on 2005-02-15
Can someone investigate if this is affected by USN 82-1?

---

### Post by jdong on 2005-02-16
Guys, I'm planning to **remove** this backport from the repository.

Why?

The Hoary kernel line is moving too fast. Since this backport, there's at least been 10 new kernel revisions in Hoary, all of them having something fixed. I don't want to pull a gentoo-dev-sources here in Ubuntu. I think most Gentoo will still twitch uncontrollably when they hear that a new LiveCD is in the works ;).

Does this warrant its removal for the sake of stability? Or does this warrant the kernel a spot in backports/bleeding?

Opinions/suggestions welcome.

---

### Post by ember on 2005-02-16
Hmm .... I guess as it's in 'bleeding' there's nothing wrong about it. Anyone who likes can still stick to 2.6.8.

---

### Post by rufius on 2005-02-16
[QUOTE=jdong]Guys, I'm planning to **remove** this backport from the repository.

Why?

The Hoary kernel line is moving too fast. Since this backport, there's at least been 10 new kernel revisions in Hoary, all of them having something fixed. I don't want to pull a gentoo-dev-sources here in Ubuntu. I think most Gentoo will still twitch uncontrollably when they hear that a new LiveCD is in the works ;).

Does this warrant its removal for the sake of stability? Or does this warrant the kernel a spot in backports/bleeding?

Opinions/suggestions welcome.[/QUOTE]
 I'm with you on removing it, I've been watching the Hoary-devel and Ubuntu-devel mailing lists and there seems to be a lot of kernel issues being reported/mentioned.

---

### Post by emperor on 2005-02-17
[QUOTE=jdong]Guys, I'm planning to **remove** this backport from the repository.
   Opinions/suggestions welcome.[/QUOTE]
 
 We "warty" guys need a kernel update from 2.6.8 to fix the ACPI and a few other issues. Please give us a backport 2.6.10 or 2.6.11 kernel solution to resolve this.

---

### Post by jdong on 2005-02-17
I will backport the latest version of Kernel 2.6.10, and put it in the bleeding tree.

---

### Post by jdong on 2005-02-17
Building 2.6.10-18 from Hoary.

---

### Post by jdong on 2005-02-17
urg -19 just magically appeared in APT. Building that instead.

---

### Post by cpinto on 2005-02-21
[QUOTE=jdong]Does anyone object to this kernel moving to stable? Maybe stable/bleeding?[/QUOTE]
I'm currently using Hoary (I got an itch for the new Gnome 2.10 :) ) and I must say that the kernel is a bit messed up. I've got some serious issues with nvidia-3d acceleration (simply doesn't work) so if I were you I'd only backport the kernel and no restricted modules whatsoever.

An alternative is to compile the nvidia kernel driver from warty against this new kernel.

---

### Post by jdong on 2005-02-21
I'm currently using the 2.6.10-4-19 k7 kernel in Hoary. 3d accel works great with my Nvidia card, and so does everything else. This is the currently staging kernel.


So, it seems like all works except:

============
* Ndiswrapper -- possible issue? It's currently built as a module. May need newer userland utils?
*Security -- some sort of minor FS sign checking bug. Need to further investigate.


I think we're closing in on a promote.

---

### Post by keeee on 2005-02-23
Ndiswrapper still doesn't work with ndiswrapper 1.0 (I've compiled the source from ndiswrapper.sf.net) + kernel 2.6.10 from staging. It still gives a "not permitted" error when trying to modprobe ndiswrapper :/

---

### Post by jdong on 2005-02-23
Does dmesg give any more hints?

---

### Post by keeee on 2005-02-23
Nope :/
This message is repeated six times:

ndiswrapper version 1.0rc2 loaded (preempt=yes,smp=no)
ndiswrapper (wrapper_init:1494): loadndiswrapper failed (59904); check system log for messages from 'loadndisdriver'

I can't see any more interesting logs here mate, it does seam that the kernel version is 1.0rc2 instead of version 0.10 of the user-utils.

---

### Post by keeee on 2005-02-23
I got it working mates! I'm typing this from my laptop using kernel 2.6.10 and my linksys wlan card ;) It seems it's just a problem with the user-level tools I guess.
What I did:

1) Removed (purged) the old ndiswrapper from ubuntu (v 0.10)
2) Added deb [http://ndiswrapper.sourceforge.net/debian](http://ndiswrapper.sourceforge.net/debian) ./ to my apt sources and 
3) Installed ndiswrapper-source (v 1.0)
4) Make && Make install @ modules/ndiswrapper/driver
5) Make && Make install @ modules/ndiswrapper/utils
6) Add the right .INF file and modprobe ndiswrapper
7) Works like a charm :)
source: [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)
source: [http://ndiswrapper.sourceforge.net/phpwiki/index.php/Installation](http://ndiswrapper.sourceforge.net/phpwiki/index.php/Installation)

From the ndiswrapper wiki: "This should compile and install both the kernel module and the userspace utilities." It seems like it indeed installed a new ndiswrapper module, syslog says "ndiswrapper 1.0" is loaded instead of the "ndiswrapper 1.0rc2" that couldn't load before.
Maybe apply these patches @ the ubuntu backport kernel + backport ndiswrapper-utils? That's my best bet.

---

### Post by jdong on 2005-02-23
I'll make a backport of ndiswrapper 1.0, as that seems to fix it.

---

### Post by faqpete on 2005-02-26
Thx jdong! Hope it works for me too ;-)

---

