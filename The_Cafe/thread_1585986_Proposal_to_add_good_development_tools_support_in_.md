---
title: "Proposal to add good development tools support in ubuntu."
date: 2010-10-01
forum: The Cafe
---

### Post by German Diago on 2010-10-01
Hello all. My name is Germán Diago and I would like to explain
the problems I've had lately using ubuntu.

I've been an ubuntu user since its first release. I've also
studied computer science, so one of my hobbies is developing
software. I code mainly in C++ (almost exclusively). The problem
is that the support in ubuntu for coding in C++ falls behind
other distributions such as fedora.

Fedora comes with an awesome eclipse installation that provides, among other things, support for the whole linuxtools project (see [http://www.eclipse.org/linuxtools/](http://www.eclipse.org/linuxtools/)) and good
support for cross-compiling, which can be quite time-consuming
if you have to configure your own environment.


Sure you can install an eclipse distribution in ubuntu, but it doesn't play nicely with these tools because:

a) oprofile support cannot be activated in a reasonable way because there is no oprofile-dev package and you can't compile
the module needed to use it without recompiling oprofile from source, among other problems.

b) Callgraph cannot be used because it needs a kernel with CONFIG_UTRACE support, which ubuntu doesn't provide. This means you have to compile your own
kernel, which is not feasible.

c) It has no MinGW precompiled packages for windows (which Fedora has in its own repositories)

d) Besides that, gdb in Fedora 14 has been optimized to be faster.

My proposal is to begin a project that makes eclipse and all its important tools as integrated as possible in repositories. This includes (in my personal order of importance):


a) C/C++ support via cdt and COMPLETE eclipse linuxtools.
   So we need here:
        Kernel that plays well with systemtap (with CONFIG_UTRACE enabled)
        oprofile-devel package in order to use the oprofile profiling tool.

b) Precompiled windows packages for important libraries such as boost for cross-compiling (this is costly, so it's leaved as optional).
c) Support for embedded development.
d) Pydev support
e) Good java support.

I really care about a) and b) proposals, although b) could be left for a later release.

I also think that it would be very important to have a good eclipse support from Canonical if it wants to attract developers. It's simply the best tool to code in linux.

For now I had to take the hard decision of switching to Fedora.
If my proposal can be accomplished (I could help myself) I will come back home :-)

Maybe the first thing to do is a blueprint? I look forward to reading your thoughts about this. Thanks for reading.

---

### Post by Tibuda on 2010-10-01
> **German Diago said:**
> c) It has no MinGW precompiled packages for windows (which Fedora has in its own repositories)


[http://packages.ubuntu.com/lucid/mingw32](http://packages.ubuntu.com/lucid/mingw32) ?

---

### Post by German Diago on 2010-10-01
> **Tibuda said:**
> [http://packages.ubuntu.com/lucid/mingw32](http://packages.ubuntu.com/lucid/mingw32) ?

I meant it doesn't have, gtkmm, gtk or boost packages precompiled for windows, for example, not the toolchain itself.

---

### Post by Tibuda on 2010-10-01
> **German Diago said:**
> I meant it doesn't have, gtkmm, gtk or boost packages precompiled for windows, for example, not the toolchain itself.

ah...

---

### Post by BrokenKingpin on 2010-10-01
Why don't you just use Fedora for development? Ubuntu is meant to be an easy to use desktop, not a development platform (although any Linux distro can work well for a development platform). Fedora focuses more on making a great development platform, but fails as a good end user desktop.

---

### Post by German Diago on 2010-10-01
> **BrokenKingpin said:**
> Why don't you just use Fedora for development? Ubuntu is meant to be an easy to use desktop, not a development platform (although any Linux distro can work well for a development platform). Fedora focuses more on making a great development platform, but fails as a good end user desktop.

I know. But the point would be to be able to use my fav linux distro for everything. Anyway, I'm looking for help since I'm not a kernel expert.

Canonical, please, consider my proposal. Ubuntu already is the best desktop distribution. Maybe I can help with packaging. The only thing left is to make it a great developer tool.

---

### Post by cariboo on 2010-10-01
Unfortunately the developers don't peruse the forum on a regular basis, so basically you're preaching to the choir by posting here. If you want to help, have a look [here]("https://wiki.ubuntu.com/UbuntuDevelopers").

---

### Post by German Diago on 2010-10-01
> **cariboo907 said:**
> Unfortunately the developers don't peruse the forum on a regular basis, so basically you're preaching to the choir by posting here. If you want to help, have a look [here]("https://wiki.ubuntu.com/UbuntuDevelopers").

Great! Thanks for the info.

---

