---
title: "Firefox w/ Wine is faster than Native Firefox"
date: 2009-02-13
forum: The Cafe
---

### Post by vishzilla on 2009-02-13
[http://www.tuxradar.com/content/browser-benchmarks-2-even-wine-beats-linux-firefox](http://www.tuxradar.com/content/browser-benchmarks-2-even-wine-beats-linux-firefox)

:shock:

---

### Post by cardinals_fan on 2009-02-13
...while Midori scores a 970.

---

### Post by vishzilla on 2009-02-13
Midori is good, but the browser crashes on many website..

---

### Post by thisllub on 2009-02-13
Firefox without flash is fast and reliable.

Flash is the enemy.

---

### Post by bruce89 on 2009-02-13
Saying that Windows is faster because of this is flawed reasoning. There could be many reasons for this (compiler flags, Windows-only optimisations).

Also, Epiphany-Gecko gets 117, my own JavaScript WebKit browser gets 942.

---

### Post by phrostbyte on 2009-02-13
It's clear this has nothing to do with Linux or X. It's a shame people are passing the blame when the blame for this should be squarely on Mozilla.

---

### Post by vishzilla on 2009-02-13
phrostbyte is right.. its the same thing with Flash

something has to be done to make apps competitive in Linux to the other OSes like Windows.

---

### Post by phrostbyte on 2009-02-13
> **vishzilla said:**
> phrostbyte is right.. its the same thing with Flash

something has to be done to make apps competitive in Linux to the other OSes like Windows.

Well I think Firefox 3.1 might have fixed this problem. Overall it's not a huge problem, it means maybe Gmail opens milliseconds slower. 

I think there are bigger problems to worry about. :) I just was mad that people are using this as a platform to talk bad about X or Linux, when it's clear this isn't caused by  either.

---

### Post by handy on 2009-02-13
Native Linux Firefox is plenty fast enough for me as it is.

Who cares what other people think?

If you are happy with something, that's all there is to it.

---

### Post by MaxIBoy on 2009-02-13
This has been quite opposite to my experience; on both of my computers, Firefox 3 under WINE has been slow, buggy, and downright unstable. This could be due to regressions in WINE, it could me my distro, it could be a number of things. I'll definitely be running the benchmark myself.

---

### Post by Rokurosv on 2009-02-13
> **handy said:**
> Native Linux Firefox is plenty fast enough for me as it is.

Who cares what other people think?
[B]
If you are happy with something, that's all there is to it.[/B]

+1 It works fast for me and I'm happy with it. The 3.1 beta worked faster but there was a lot incompatibility with my addons so I'm just going to wait.

Also the PGO build is a lot faster for me than the standard Firefox

---

### Post by vishzilla on 2009-02-13
I was just imagining, a day would come when every distro will have its own Browser. How would that be? ;)

---

### Post by Rokurosv on 2009-02-13
> **vishzilla said:**
> I was just imagining, a day would come when every distro will have its own Browser. How would that be? ;)

Hmmmm something like IE?

---

### Post by SunnyRabbiera on 2009-02-13
This is nonsense, for me firefox in wine and linux firefox run about ther same, even with flash...

---

### Post by ghindo on 2009-02-13
[http://tech.slashdot.org/comments.pl?sid=1126335&cid=26841669](http://tech.slashdot.org/comments.pl?sid=1126335&cid=26841669)

---

### Post by airjaw on 2009-02-13
IME firefox is noticably slower in Ubuntu than Windows. I don't think ints Ubuntu's fault but rather, Mozilla's.

I'm glad this test is gaining attention on the web. hopefully Mozilla will get to work on it.

---

### Post by cardinals_fan on 2009-02-13
> **SunnyRabbiera said:**
> This is nonsense, for me firefox in wine and linux firefox run about ther same, even with flash...
Could you take the test and let us know if it is accurate?

*Not that the test means anything, but I'd be interested in knowing*

---

### Post by michaelzap on 2009-02-13
> **airjaw said:**
> IME firefox is noticably slower in Ubuntu than Windows. I don't think ints Ubuntu's fault but rather, Mozilla's.

I'm glad this test is gaining attention on the web. hopefully Mozilla will get to work on it.

+1

I can definitely notice the speed difference between FF on Windows and Linux. It's not so severe that I've stopped using FF on Linux, but it annoys me anyway. Mozilla ought to invest some time and effort into optimizing their code for Linux!

---

### Post by crimesaucer on 2009-02-13
All I know is that my Firefox-PGO 3.1b2 compiled for my processor using C[XX]FLAGS and LDFLAGS seems to work as fast as my Vista version of FF 3.1b2..... both versions of 3.1b2 are much faster than FF 3.0.6 on Vista and Linux.


I also find that my FF 3.1b2-PGO seems as fast as Epiphany-Webkit and Midori-Webkit (both very recent builds)..... the same pages load in the same time..... with the FF 3.1b2-PGO I never have any crashes and I don't have any of the java/webkit problems or cookie problems. 


Today when I was on Vista I tried the Minefield 3.2a1 build for Win32 (on Vista64) and it felt even faster than 3.1b2..... it was as snappy and quick as Opera 9.63 on Vista and Chrome on Vista..... so I'm sure once they release the source of the 3.2 that the PGO builds will be very quick. I might even install the 3.2 x86_64 generic Linux binary package.



Another thing I noticed is that when I use Firefox on Vista64 (4GB RAM) with utorrent running, Firefox becomes slow and almost inoperable. I don't get this with deluge and Firefox on Linux with the same style torrents and peer settings.

---

### Post by smartboyathome on 2009-02-14
:shock: I just ran this against Opera, Firefox, Midori, and cxChromium (Crossover's port of Google Chrome), and Opera scored 127, Firefox 133, Midori 1381(**!!!**) and cxChromium 1122(**!**). I dunno what to say about that. :|

---

### Post by vishzilla on 2009-02-14
smartboyathome, did you use the V8 Benchmark Suite?

for me, Firefox 3.0.6 => 81.7, Midori 0.1.2 => 1137 :shock:

---

### Post by billgoldberg on 2009-02-14
I feel no speed difference between Firefox on Windows and on Ubuntu.

---

### Post by ithanium on 2009-02-14
> **airjaw said:**
> IME firefox is noticably slower in Ubuntu than Windows. 

also noticed this thing :|

---

### Post by kevdog on 2009-02-14
So does anyone know of any instructions how to compile Firefox from source and configure the cflags and ldflags appropriately?  I'd like to try to compile Firefox and run the test between the stock and compiled versions.

---

### Post by oedipuss on 2009-02-14
If PGO makes a noticeable difference, why doesn't ubuntu provide a pgo build?

---

### Post by Erunno on 2009-02-14
Firefox is actually more affected by a badly optimized JavaScript Engine than the other browsers. Since Firefox' interface is defined in XUL, which relies on JavaScript as scripting language, any slowdown in SpiderMonkey/TraceMonkey will also have effects on the speed of the interface itself and not just the scripts on web pages.

---

### Post by smartboyathome on 2009-02-14
> **vishzilla said:**
> smartboyathome, did you use the V8 Benchmark Suite?

for me, Firefox 3.0.6 => 81.7, Midori 0.1.2 => 1137 :shock:

Yes I did. :KS

> **oedipuss said:**
> If PGO makes a noticeable difference, why doesn't ubuntu provide a pgo build?

PGO requires one to compile it to their specific hardware to get the speed boost, and since Ubuntu provides binary packages, not automatic compiling source ones, it wouldn't give the benefit of the PGO builds.

---

### Post by crimesaucer on 2009-02-14
> **kevdog said:**
> So does anyone know of any instructions how to compile Firefox from source and configure the cflags and ldflags appropriately?  I'd like to try to compile Firefox and run the test between the stock and compiled versions.

I'm not sure of how to do this in Ubuntu. In Arch there is already a nice AUR PKGBUILD script that is super easy to use.


I think you need to install this for ubuntu: [https://developer.mozilla.org/en/Linux_Build_Prerequisites#Build_Tools](https://developer.mozilla.org/en/Linux_Build_Prerequisites#Build_Tools) 



There is PGO building info for Linux here: [https://developer.mozilla.org/en/Building_with_Profile-Guided_Optimization#Building](https://developer.mozilla.org/en/Building_with_Profile-Guided_Optimization#Building)


This is the part of the Arch PKGBUILD that uses the "make -f client.mk profiledbuild" command as well as the LDFLAGS:

```

 export LDFLAGS='-lX11 -lXrender'

  LD_PRELOAD="" /usr/bin/Xvfb -nolisten tcp -extension GLX :99 &
  XPID=$!
  export DISPLAY=:99

  sed -e 's/#CFLAGS#/'"$CFLAGS"'/g' <"$srcdir"/mozconfig >.mozconfig

  LD_PRELOAD="" make -f client.mk profiledbuild MOZ_MAKE_FLAGS="${MAKEFLAGS}" || return 1
  kill $XPID

  make -j1 DESTDIR=${pkgdir} -C ff-opt-obj install || return 1


```


The part about the C[XX]FLAGS uses the ones that are already set in the Arch /etc/makepkg.conf file.


There is also the mozconfig:

```

# load defaults from src tarball
. $topsrcdir/browser/config/mozconfig
# add our own options
ac_add_options --enable-application=browser
ac_add_options --prefix=/usr --libdir=/usr/lib
ac_add_options --with-system-nspr --with-system-nss--with-system-jpeg --with-system-zlib --with-system-png
ac_add_options --with-pthreads
ac_add_options --enable-optimize="#CFLAGS#"
ac_add_options --enable-default-toolkit=cairo-gtk2 --disable-freetype2 --enable-xft --enable-system-cairo
ac_add_options --disable-tests --disable-installer --disable-debug --disable-profilesharing --enable-single-profile
ac_add_options --enable-official-branding
ac_add_options --enable-dbus
ac_add_options --enable-jemalloc
ac_add_options --enable-pango --enable-crypto --enable-svg --enable-canvas 
ac_add_options --disable-xprint
ac_add_options --disable-crashreporter
ac_add_options --enable-xinerama
ac_add_options --enable-safe-browsing --enable-webservices
ac_add_options --enable-strip
#ac_add_options --enable-libxul --with-libxul-sdk=/usr/lib/xulrunner-devel-1.9
mk_add_options MOZ_MAKE_FLAGS=-j8
mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/ff-opt-obj
mk_add_options PROFILE_GEN_SCRIPT='$(PYTHON) $(MOZ_OBJDIR)/_profile/pgo/profileserver.py'

```


This has the part about PGO here: 

```
mk_add_options PROFILE_GEN_SCRIPT='$(PYTHON) $(MOZ_OBJDIR)/_profile/pgo/profileserver.py'
```

And the part about C[XX]FLAGS here: 

```
ac_add_options --enable-optimize="#CFLAGS#"
```

And the part about cairo: 

```
ac_add_options --enable-default-toolkit=cairo-gtk2 --disable-freetype2 --enable-xft --enable-system-cairo
```



I'm sure someone can make a script for ubuntu, or you could modify your mozconfig file and use ./configure make with the correct build options or something.



One last thing..... it takes over and hour to build for me.


Also read this digg comment: [http://digg.com/linux_unix/Firefox_Faster_In_Wine_Than_Native?t=23309788#c23309788](http://digg.com/linux_unix/Firefox_Faster_In_Wine_Than_Native?t=23309788#c23309788)

---

### Post by cardinals_fan on 2009-02-14
> **smartboyathome said:**
> :shock: I just ran this against Opera, Firefox, Midori, and cxChromium (Crossover's port of Google Chrome), and Opera scored 127, Firefox 133, Midori 1381(**!!!**) and cxChromium 1122(**!**). I dunno what to say about that. :|
WebKit.  You can love it or hate it, but you can't deny it :)

Anyway, links -g is the fastest browser for me, but I can't test it because it doesn't support javascript.

---

### Post by MaxIBoy on 2009-02-14
Native Linux Firefox (straight from the repos) scores 128 on that benchmark-- Windows Firefox (straight from Mozilla's site) under WINE scores 160. 

However, the benchmark only looks at Java performance. Sometime in the future, I'm going to make a greasemonkey script that will browse a bunch of local (on the hard drive) sample webpages (html, xml, flash, php, java, and so on,) in a bunch of different tabs and windows, and measure overall responsiveness.

---

### Post by Skripka on 2009-02-14
Dear gawd....I thought Midori and Arora were supposed to be somewhat similar?

On my box (see signature), which is anything but lacking power

[http://v8.googlecode.com/svn/data/benchmarks/v3/run.html](http://v8.googlecode.com/svn/data/benchmarks/v3/run.html)


Firefox 3.0.6 (Native-in the repos): 196
Opera 10 alpha (build 4102):194
Konuerqor KDE4.2: 176
Arora 0.4: 90.7


It sucks that the only QT4 native browsers are also the slowest.

---

### Post by crimesaucer on 2009-02-14
> **Skripka said:**
> Dear gawd....I thought Midori and Arora were supposed to be somewhat similar?

On my box (see signature), which is anything but lacking power

[http://v8.googlecode.com/svn/data/benchmarks/v3/run.html](http://v8.googlecode.com/svn/data/benchmarks/v3/run.html)


Firefox 3.0.6 (Native-in the repos): 196
Opera 10 alpha (build 4102):194
Konuerqor KDE4.2: 176
Arora 0.4: 90.7


It sucks that the only QT4 native browsers are also the slowest.


That test gives my Firefox 3.1b2-PGO compiled browser a very low score of 114..... 

I'm pretty sure that my browser is fast. I have the official 64bit JRE and the official 64bit Flash plugins, and all of the best "about:config" settings..... and very few Add-Ons installed. My pages load as fast as Epiphany-webkit and Midori-webkit for various sites with flash and large pages of photos like the Screenshot thread or deviantART.

---

### Post by Skripka on 2009-02-14
> **crimesaucer said:**
> That test gives my Firefox 3.1b2-PGO compiled browser a very low score of 114..... 

I'm pretty sure that my browser is fast. I have the official 64bit JRE and the official 64bit Flash plugins, and all of the best "about:config" settings..... and very few Add-Ons installed. My pages load as fast as Epiphany-webkit and Midori-webkit for various sites with flash and large pages of photos like the Screenshot thread or deviantART.

On my box it isn't speed that really miffs me.  What gets me is the fact that a native Qt4 browser that runs flash well does NOT EXIST.   Grrrrr.  Konqueror does not run embed Youtube vids, Opera doesn't even make a 64bit Qt4 build (for gwad knows what reason-and they won't even tell why), and Arora doesn't even run Flash.  SOL.

---

### Post by wersdaluv on 2009-02-14
After all, Windows is high priority for Mozilla while Linux isn't.

---

### Post by crimesaucer on 2009-02-15
> **Skripka said:**
> On my box it isn't speed that really miffs me.  What gets me is the fact that a native Qt4 browser that runs flash well does NOT EXIST.   Grrrrr.  Konqueror does not run embed Youtube vids, Opera doesn't even make a 64bit Qt4 build (for gwad knows what reason-and they won't even tell why), and Arora doesn't even run Flash.  SOL.

And Midori-webkit doesn't work with the jre_beta 6u12-1 64bit plugin..... and it's still very unstable with the webkitgtk-svn (Arch AUR package).... as well as not having cookies enabled. 

Epiphany-webkit also won't use my jre_beta 6u12-1 64bit plugin and for some reason the Epiphany URL search engine won't work at all with my webkit builds..... and the Epiphany extensions and greasemonkey scripts won't work either.


So I stay with Firefox..... even the development builds have working flash64/jre64 plugins and all of the nice things like: extensions, download-managers, cookies, media-player plugins, search-engines.....

---

### Post by bruce89 on 2009-02-15
> **crimesaucer said:**
> Epiphany-webkit also won't use my jre_beta 6u12-1 64bit plugin and for some reason the Epiphany URL search engine won't work at all with my webkit builds..... and the Epiphany extensions and greasemonkey scripts won't work either.

So I stay with Firefox..... even the development builds have working flash64/jre64 plugins and all of the nice things like: extensions, download-managers, cookies, media-player plugins, search-engines.....

Wait for Epiphany 2.28. The Epiphany-WebKit package is effectively very old, as the stable Epiphany branches have had no work on the WebKit stuff (though trunk has).

---

### Post by aktiwers on 2009-02-15
I Score: 215 in V8 benchmark test
[http://v8.googlecode.com/svn/data/benchmarks/v3/run.html](http://v8.googlecode.com/svn/data/benchmarks/v3/run.html)

With Firefox 3.0.6

---

### Post by Simian Man on 2009-02-15
Another reason for this is the library model of the OSes.  On Windows applications statically link to as much as possible.  That's because Windows doesn't really provide much in the way of library support.  If an application needs, for instance, libpng, it needs to either statically link to it or install the DLL itself.  Between these two options, static linking is preferable as it is faster (no context switching, shared memory space etc.)  The problem with this is that applications are large as they all package most of their dependencies and you can't update the libraries and have it affect the applications.

On Linux, of course, apps like Firefox don't come with their dependencies, they are packaged and installed separately.  The advantages of this are saneness (I'm sure I have many copies of the same libs installed under Windows), lower disk usage, and the ability to update libraries and have it affect all apps.  Unfortunately, as I said, dynamic linking incurs some performance cost as each .so essentially runs in its own process space and you must switch contexts on library calls.

I think the benefits of dynamic linking obviously outweigh the drawbacks, but it does mean Windows applications can be a bit faster.

---

### Post by Keyper7 on 2009-02-15
swiftweasel = PGO without effort

---

### Post by crimesaucer on 2009-02-15
> **Keyper7 said:**
> swiftweasel = PGO without effort

I've used swiftweasel and swiftfox in the past (was good on my old celeron m laptop). I also have built regular builds of Firefox-optimized with the mozconfig file for my processor.

But swiftweasel and swiftfox have had problems working/building on my Turion 64 X2 processor (even the pre-made binaries won't install or work). And the PGO build seems to works faster then the mozconfig optimizations of this other Firefox package from Arch AUR: [http://aur.archlinux.org/packages.php?ID=18090](http://aur.archlinux.org/packages.php?ID=18090)

---

### Post by jblackhall on 2009-03-09
I realize this is digging up an old topic, but I just read a couple of comments by Aza Dotzler of Mozilla who blames some folks on the Linux side as opposed to the Mozilla team.  He makes some interesting points.

> Windows has a better compiler than Linux. That's a big part of the problem. Get GCC to produce more performant code, and Firefox will be faster on Linux native than under Wine. Also, on Windows, we do profile guided optimization when we build. Linux distros who are the main source of Linux Firefox don't do that. These are both issues that are outside of Mozilla's realm and if you're disappointed in that Wine to native comparison, you should chase down the Firefox maintainers at the various distros and get them to do PGO builds and you should chase down the GCC guys and get them to improve the compiler.

And, yes, I am blaming other people besides the Firefox developers for the results of that Firefox native vs. Wine test. 
[http://weblogs.mozillazine.org/asa/archives/2009/02/how_many_linux.html#comment-2626289](http://weblogs.mozillazine.org/asa/archives/2009/02/how_many_linux.html#comment-2626289)

> Tomer, yeah, Mozilla doesn't do PGO builds either because "no one" uses our builds (except a few people like you) so it's not worth the effort on our end. The linux distros created a situation where there's no value in software vendors like Mozilla trying to make good builds for Linux because they lock most people in to their own packaging system. And even our own builds are also limited by GCC's inferiority to Microsoft's compiler.
[http://weblogs.mozillazine.org/asa/archives/2009/02/how_many_linux.html#comment-2626395](http://weblogs.mozillazine.org/asa/archives/2009/02/how_many_linux.html#comment-2626395)

---

### Post by ghindo on 2009-03-09
I don't understand why he's saying that GCC is a worse compiler than Microsoft's.  Are there any studies/numbers to back this up?

---

### Post by joey-elijah on 2009-03-09
as much as i love Mozilla, their ethos and Firefox some of their sentiments are a bit on the 'well we don't really care too much about linux' side.

If google chrome is faster than firefox when it lands in Ubuntu, and providing the extension framework is there, then there could be a massive shift towards Chrome.

Most Linux users use Firefox as their default browser - which is probably a nice chunk of Mozzila's market share. If they really can't take the time to provide/test firefox for Linux users and pretty much tell us to run it thought WINE if we want decent performance then, well, i cannot wait for Chrome! 

I hate how slow Firefox is to start up, browser and shut down on my system, which is hardly a tortoise.

On Windows it flies! IN Ubuntu i actually find myself using Ephiphany or Midori for quick, casual browsing rather than hitting the firefox icon and waiting around 10-15 secs for it to become usable.

Why should Linux users be the black sheep of the firefox family?

---

