---
title: "Firefox 3.1 Beta 2 Sunspider vs. 3.0.5"
date: 2009-01-17
forum: The Cafe
---

### Post by MisterFlibble84 on 2009-01-17
Firefox 3.1 Beta 2: (2226.4 ms)

[http://paste.ubuntu.com/105887/](http://paste.ubuntu.com/105887/)

Firefox 3.0.5 (3763.2 ms)

[http://paste.ubuntu.com/105888/](http://paste.ubuntu.com/105888/)

Firefox 3.1 will be neck and neck with Webkit and only a few hundred ms behind Google Chrome. (at least what it got in Wine)

---

### Post by Erunno on 2009-01-17
WebKit r40000: 933.8 ms (OSX 2.4 GHz Core 2 Duo)

And testing through Wine has only a very limited validity as not only the application has to go through a compatibility layer but also one can't assure that the code paths in Wine are as optimized as on its native platform (e.g. Direct3D runs in most cases noticeably slower on Wine according to its developers).

---

### Post by jomiolto on 2009-01-17
Interesting :)

Opera 10 beta: 6675.8ms
Firefox 3.0: 4699.4ms
Midori 0.1.2: 1541.8ms (uses webkit)

These were run on a slow Celeron laptop. It seems like JavaScript speed is going through the roof as the web browsers continue to improve. I wonder how something like Firefox 2 or even older browsers would do in this test (if they can run it) :P

---

### Post by Erunno on 2009-01-17
Dromaeo [1] seems to be a more meaningful test than pure SunSpider anyway as it has a far greater scope when testing the JavaScript implementation. For instance, it also tests DOM interaction performance heavily which many so-called AJAX sites use to change content dynamically without reloading the whole page.

[1] [http://dromaeo.com/]("http://dromaeo.com/")

---

### Post by adamlau on 2009-01-19
Opera 10.00.4216 (FROM) vs. Firefox 3.1b2 PGO (TO) compiled with the following mozconfig:

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

[IMG]http://i275.photobucket.com/albums/jj281/adamchrista/Screenshots/Opera-104216_vs_Firefox-31b2-PGO-1.png[/IMG]

Midori 0.1.2 built against the updated WebKit package from 'deb [http://ppa.launchpad.net/webkit-team/ubuntu](http://ppa.launchpad.net/webkit-team/ubuntu) intrepid main' with the following options: 

```
-d none --disable-sqlite --disable-addons --disable-unique --disable-libsoup --disable-nls --disable-docs --disable-userdocs --disable-apidocs
```

Completed SunSpider in just under 1500ms. Issues with cookies on certain sites (even when built with all options enabled) and crashes on the closing of tabs have led me back to my traditional Opera/Firefox combination. Thanks for the recommendation, Erunno. Will give Dromaeo a try :) .

---

