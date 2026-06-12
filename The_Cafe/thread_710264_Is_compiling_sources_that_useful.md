---
title: "Is compiling sources that useful?"
date: 2008-02-28
forum: The Cafe
---

### Post by Fixman on 2008-02-28
I am gonna uninstall some programs and reinstall themm by compiling the source code with -O3, but can I ask to someone with experience in this field if its really worth it?

---

### Post by k2t0f12d on 2008-02-28
> **Fixman said:**
> I am gonna uninstall some programs and reinstall themm by compiling the source code with -O3, but can I ask to someone with experience in this field if its really worth it?

It can be.  I compile a lot of packages myself on top of Debian, and have compiled a basic GNU/Linux from souce code.  The benefit of compiling locally is to give the compiler the chance to output binary that is as ideal as possible for your hardware.

I have a Pentium 4 2.4ghz.  Here is my cpuinfo output

```
$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.40GHz
stepping        : 7
cpu MHz         : 2399.950
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat
pse36 clflush dts acpi [COLOR="Red"]mmx[/COLOR] fxsr [COLOR="Red"]sse sse2[/COLOR] ss ht tm pbe up pebs bts sync_rdtsc cid xtpr
bogomips        : 4802.25
clflush size    : 64
```

My processor has mmx sse and sse2 extentions, so after reading the documentation on gcc I use the following CFLAGS environment variable

```
CFLAGS="-O3 -march=pentium4 -mtune=native -mmmx -msse -msse2 -pipe"
```

For C++ I use the same exact flags in the environment variable CXXFLAGS.

Be sure you know what type of CPU you have and what features it has before trying any optimization other then the -O series (e.g. -O3), and -pipe if you are using GNU tools.  Building with the wrong flags will produce output binary that *will not work* on the computer for which you are building.

---

### Post by forrestcupp on 2008-02-28
I used Sabayon Linux for a while, which uses the portage system to compile everything you install.  The problem with that is that it takes a long time to install everything.  I honestly didn't notice enough perceptible difference in the starting or running of the applications for it to justify spending that much time installing everything.  So I went back to Ubuntu installing binaries, and now I'm happier.

---

### Post by kevdog on 2008-02-28
What did you think of Sabayon beyond what was stated above?  I was thinking of trying it out!  Along with Arch.

---

### Post by harold4 on 2008-02-28
> **Fixman said:**
> I am gonna uninstall some programs and reinstall themm by compiling the source code with -O3, but can I ask to someone with experience in this field if its really worth it?

When compiling from source, take a look at using checkinstall.  That way you can manage the code as a .deb package.  Occasionally, checkinstall will fail to build the .deb and "make install" is needed.

---

### Post by forrestcupp on 2008-02-28
> **kevdog said:**
> What did you think of Sabayon beyond what was stated above?  I was thinking of trying it out!  Along with Arch.

Well, I used an old version before Compiz and Beryl merged.  The only good thing about Sabayon was that Beryl worked flawlessly by default.  Other than that, it wasn't that great.  It seems like it ran slower than Ubuntu for some reason.  It was kind of sluggish feeling.  That's what disappointed me about compiling everything.  It was a waste of time when Ubuntu ran faster with precompiled binaries.

But I'm sure SL has gotten better since then, Ubuntu has.

---

### Post by k2t0f12d on 2008-02-29
Before trying to build your software from source code you might want to stop to think about some of the complications that are not only possible, but likely.

It is very true that compiling from source code takes a great deal of time, even on fast machines.  On a 2.4ghz P4 it takes me ~135 minutes to build a temporary toolchain and ~360 minutes to build the most basic GNU system possible.  Compiling the Linux kernel adds 40 to 50 minutes on top of that.  Largish application suites like the X windows library or the GNOME and KDE window managers can easily match or exceed the entire compilation time of the base system *each*.

Custom built binaries easily have the *possibility* but no *guarantees* of improved performance.  If you choose to build a package with a less efficient choice of compiler options then a binary distribution like Ubuntu uses you can very very easily wind up with a program that performs *worse* or not at all.  Even if you are able to pinpoint the precise build that works the best on your hardware, the improvements to performance can be negligible.  Unless you enjoy dealing with these sorts of problems, or if you aren't at least willing to, you are probably better off using generic binaries built for you by a distribution.

Another problem is security.  A quote from DIY Linux for those building from source code who are worried about security (click the quote to view the source web page)
[QUOTE=Greg Schafer][FONT="Courier New"][FIXME shoot down the hysteria surrounding security patches. It's horses for courses. You want security? Then FFS run a distro which provides security updates. Mention how utterly idiotic it is to build a system yourself then place it in a security vulnerable situation (ie: on the internet) without having the faintest clue about security then expecting someone else to be responsible for patches. FIXME]("http://www.diy-linux.org/reference-build/introduction.html#security")[/FONT][/QUOTE]
This is 100% accurate.  When building from source, the onus is on the builder to find, judge, and then apply *absolutely any* patches, including those for security issues.  This is easier when the original developers are actively maintaining the software, but is not liable to have the lightning quick results that can be found in a distribution that is in the position to accept patches from anywhere.

So far I've been making building source sound pretty scary, where it really isn't.  It can be frustrating if you aren't very knowledgable about the GNU build tools, computer architecture, and at least an inkling of programming.  However, it is a pretty powerful and unique feeling to build you own GNU system, decorate it in your personal nomenclature, and turn it on and have everything work.  It is worth the time to learn doing if you have the time to spend.  In every case I have been able to build a software package from source and notice a perceptible improvement in performance, whether great or small.

Coming from a background in Ubuntu or Debian, I recommend practicing building the following software (click the name to download the tarballed source, except WINE which leads to winehq's howto get WINE with git)
[LIST]
[GNU Emacs]("ftp://ftp.gnu.org/pub/gnu/emacs/emacs-22.1.tar.gz")
[*][git source code manager]("http://kernel.org/pub/software/scm/git/git-1.5.4.3.tar.bz2")
[*][WINE Windows on UNIX]("http://www.winehq.org/site/git")
[/LIST]
Where you should use your custom made *git* utilities to download and maintain the lastest version of WINE.  Successfully building these programs from source and using them will cover *all* the basics.

---

