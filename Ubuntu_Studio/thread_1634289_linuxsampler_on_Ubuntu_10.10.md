---
title: "linuxsampler on Ubuntu 10.10"
date: 2010-11-30
forum: Ubuntu Studio
---

### Post by seydou on 2010-11-30
I recently struggled to make linuxsampler up and running on my laptop HP 2230s with Ubuntu 10.10, and here is my experience to share if anyone be interested.

The linuxsampler seems to be quite usefull piece of software, you can hit the homepage at [http://www.linuxsampler.org/index.php](http://www.linuxsampler.org/index.php)

By the way - Ubuntu repos do contain qsampler, but it is mere front-end for linuxsampler. However, the linuxsampler itself is not included. Why, it is beyond me. Anyway, it is nice piece of software well worth trying, but you either need to compile it yourself or trust me and download my packages.

The whole suite is available at [http://sarakinas.wu.cz/doku.php?id=linux_sampler](http://sarakinas.wu.cz/doku.php?id=linux_sampler), there is a little bit of the background info, too.

Ubuntu 10.10has 2 jackd packages - legacy jackd1, and the new one jackd2. Normally, I would rather use jackd2, but linuxsampler failed to compile against libjack-jackd2-dev on my machine. Reverting to jackd1 killed fluidsynth on return - when starting GUI (qsynth), it failed to create audio ports in jack and died with infamous last words

```

zombified - calling shutdown handler
fluidsynth: error: Help! Lost the connection to the JACK server

```

Seemed as a dead end, but I came to the solution, after numerous try-and-error steps.

So, if you venture to build linuxsampler yourself, do it this way:

First , revert back to jackd1, and make sure you have libjack-dev package installed. This would probably wipe out ardour, but no worry, we will get it back. After this follow the sequence proposed on [linuxsampler website]("http://www.linuxsampler.org/index.php"), when compiling all necessary packages - I used cvs versions for that matter, but tarballs should do as well. Build gigedit and libgig first, and install freshly compiled gigedit, libgig6 and libgig-dev packages prior building linuxsampler - do not use libgig-dev from Ubuntu repos, othervise the build fails. Once liunxsampler is compiled and installed, you can upgrade gigedit and libgig packages without any harm, and upgrade to jackd2 as well. After thas, install ardour back and you are done. Everything should work with jack just fine.

As for the frontend, I strongly recommend jsampler (Fantasia GUI looks cool), it worked for me better then gsampler, which tends to segfault on my system.

---

