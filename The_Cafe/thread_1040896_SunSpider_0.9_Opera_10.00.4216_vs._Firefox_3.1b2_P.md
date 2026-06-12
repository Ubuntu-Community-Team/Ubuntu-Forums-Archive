---
title: "SunSpider 0.9: Opera 10.00.4216 vs. Firefox 3.1b2 PGO"
date: 2009-01-16
forum: The Cafe
---

### Post by adamlau on 2009-01-16
Opera 10.00.4216 (FROM) is the latest snapshot release (as of 2009-01-15). Firefox 3.1b2 PGO (TO) compiled with the following mozconfig:

mk_add_options MOZ_MAKE_FLAGS=-j4
mk_add_options MOZ_CO_PROJECT=browser
mk_add_options MOZ_OBJDIR=/files/Backups/Programs/Firefox/obj-@CONFIG_GUESS@
mk_add_options PROFILE_GEN_SCRIPT='$(PYTHON) $(MOZ_OBJDIR)/_profile/pgo/profileserver.py'
export CFLAGS="-march=native -O2 -fomit-frame-pointer"
export CXXFLAGS="-march=native -O2 -fomit-frame-pointer"
ac_add_options --enable-application=browser
ac_add_options --enable-profile-guided-optimization
ac_add_options --enable-update-packaging
ac_add_options --enable-official-branding
ac_add_options --disable-crashreporter
ac_add_options --enable-optimize
ac_add_options --disable-debug
ac_add_options --disable-tests

I did not include results for WebKit r39953 Qt (which I have been building and testing with since r39553) as the browser is not exactly usable in a production environment (limited feature set, intermittent crashes). SunSpider 0.9 Results :shock: :

[IMG]http://i275.photobucket.com/albums/jj281/adamchrista/Screenshots/Opera-104216_vs_Firefox-31b2-PGO-1.png[/IMG]

---

### Post by aeacides on 2009-01-16
So hmm, what does it mean exactly :p ? [COLOR="black"]**Comparison **[/COLOR]column shows Opera or Firefox results? My guess is Opera, but I'm not sure at all.

---

