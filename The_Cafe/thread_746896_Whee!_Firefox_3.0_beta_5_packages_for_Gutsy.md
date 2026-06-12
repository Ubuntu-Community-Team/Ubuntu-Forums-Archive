---
title: "Whee! Firefox 3.0 beta 5 packages for Gutsy"
date: 2008-04-06
forum: The Cafe
---

### Post by jdong on 2008-04-06
I've signed off on the Firefox 3.0 beta 4 gutsy backports packages for upload, as I am fairly confident of its stability.

At the same time, I've added Firefox 3.0 beta 5 packages into the Backports PPA:
[https://edge.launchpad.net/~ubuntu-backporters/+archive](https://edge.launchpad.net/~ubuntu-backporters/+archive)


If you feel daring, feel free to test these packages and give feedback on [https://bugs.launchpad.net/gutsy-backports/+bug/212468](https://bugs.launchpad.net/gutsy-backports/+bug/212468)


Like the previous backports packages, these are based on Hardy packages except they safely make a copy of your Firefox 2.0 profile for use with Firefox 3.0 rather than overwriting that profile. This allows you to uninstall Firefox 3.0 and not ruin your firefox 2.0 profiles.

Despite some people reporting CPU usage spikes, I've not experienced any of that. I cannot tell any big difference between beta4 and beta 5, unlike the jump from beta3 to beta4, but YMMV :)

---

### Post by SpookyET on 2008-04-07
Is it PGO optimised?

---

### Post by jdong on 2008-04-07
No, not that I am aware of -- these are built using the standard Hardy buildsystem and options... PGO is a pretty new bleeding-edge feature in GCC and it's probably not wise for Hardy to ship with such built binaries :)

---

### Post by SpookyET on 2008-04-07
If you want to learn how to build it properly, check [http://aur.archlinux.org/packages/firefox-spookyet/firefox-spookyet/](http://aur.archlinux.org/packages/firefox-spookyet/firefox-spookyet/)

I'll do a build once I learn how to create debs. Pacman is idiot proof. You'll understand what's going on. Mozconfing and the build section in PKBUILD should interest you.  This is very close to how mozilla builds it. PGO optimised. I get around 1000 on the Sunspider javascript benchmark.

---

### Post by jdong on 2008-04-07
Umm, these are backports builds and as per backports policy they must closely reflect what's in Hardy. When the Ubuntu development builds migrate to PGO optimization, we will do the same in backports. I don't know who in their right minds switches build systems after beta freeze though :)

And there's nothing "improper" about building it without PGO.

---

### Post by SpookyET on 2008-04-07
Mozilla:-) 

The nightlies are PGO optimised.  I guess it's up to me, yet again, to build the best firefox package.

I hate doing it because it takes 2 hours. PGO builds are abnormally slow to compile, but very fast in the end.

Is there a quick tutorial that would catch me up to speed in creating debs? I don't have the time to read the debian manual.

Pacman was idiot proof.

---

### Post by jdong on 2008-04-07
The Debian guides, and the Ubuntu guides.

Note that Ubuntu's firefox are built separately using the xulrunner and xulbrowser trees to abstract the browser away from the Gecko rendering library that's used by around 30 other source packages in the repositories, so you can't just go around repackaging it from scratch without breaking a lot of packages.

If you feel PGO will have very significant performance improvements with little chance of regression, I'd recommend filing a bug against xulrunner-1.9 in Launchpad with relevant benchmark information and rationale for this change, so we can decide whether to implement this for Hardy or Intrepid.

The person who wrote the Ubuntu build system is a Mozilla developer and veteran Debian developer, so he must have good reasons for not choosing to implement profiled build this time around.

---

### Post by SpookyET on 2008-04-07
The Windows version is PGO optimised. People will hate the Ubuntu version knowing that the Windows version is so much faster.


This was a test I did on Arch Linux using i686:
Firefox 3 Beta 3 on the left.
Firefox 3 Beta 4 with Profile Guided Optimisations on the right: [http://www.paste2.org/p/15666](http://www.paste2.org/p/15666)

This is what I got with your build: [http://tinyurl.com/6fv8aq](http://tinyurl.com/6fv8aq)

7 times slower. I'm not sure how  much i686 helps. But, my i686 PGO was 3 times faster than my normal i686.

There are no regressions. It just works.

---

### Post by jdong on 2008-04-07
Interesting results, it'd be interesting to do an apples-to-apples comparison with the patchset that Ubuntu uses. As I said, please file a bug at [https://launchpad.net/ubuntu/+source/xulrunner-1.9](https://launchpad.net/ubuntu/+source/xulrunner-1.9) with these results so we can have some of our experienced Mozilla folks take a look at this.

(Ubuntu's firefox is slower not just because of PGO optimization but also largely due to the pango i18n font rendering backend is significantly slower than a non-pango or Windows one)

---

### Post by SpookyET on 2008-04-07
Firefox 3 should be using cairo, not pango. That said, the benchmark tests javascript, not font rendering. 

Bug filed: [https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/213708](https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/213708)

---

### Post by bjtuna on 2008-04-08
JDong -- great work on these packages, but would it be possible for them to be re-built to include better font rendering? It appears there's no sub-pixel smoothing going on. Something about it having to be built against cairo, I think.  Thanks!

---

### Post by jdong on 2008-04-08
We are built against Cairo but Mozilla bundled Cairo due to the fact that system Cairo is too old in Gutsy and is ABI incompatible with Hardy Cairo so no backport of that subsystem is possible.

---

