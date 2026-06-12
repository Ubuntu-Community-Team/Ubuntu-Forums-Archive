---
title: "Digg.com slow in Firefox on Ubuntu, but not in Windows, nor even Wine"
date: 2008-11-24
forum: The Cafe
---

### Post by altonbr on 2008-11-24
I've found when visiting Digg.com - a very AJAX/JavaScript intensive site - that my browser can get bogged down quite easily by their massive amount of JavaScript.

The thing is, when using Firefox 3 on Windows or even through WINE (!) it performs much much faster. This includes hit 'Ctrl++' to increase the font size (or zoom, as they now call it).

Yes, these tests have been run on the same machine and no, nothing is through a virtual environment.

Why do you think this is? Is there anyway to improve the performance?

I know TraceMonkey (a JavaScript intrepeter) will be coming out for Firefox 3.1 and it advertising amazing speedups[1], but even if it were to be released today, we wouldn't be able to use it until 9.04.

[1] [http://weblogs.mozillazine.org/roadmap/archives/2008/08/tracemonkey_javascript_lightsp.html](http://weblogs.mozillazine.org/roadmap/archives/2008/08/tracemonkey_javascript_lightsp.html)

So does anyone know why AJAX/JavaScript and the 'zoom' feature would be slowing in Linux than on Windows (or even through Wine)?

My PC isn't amazing, but it isn't bad either:

Pentium 4 640
GeForce 6800
2GB 4-4-4-12 DDR2 RAM
TB of disk space, etc.

---

### Post by b3n87 on 2008-11-24
I found the Apple website like that, could be something to do with Flash 10?

---

### Post by altonbr on 2008-11-24
> **b3n87 said:**
> I found the Apple website like that, could be something to do with Flash 10?

It's been happening for longer than Flash 10 and Flash is blocked on my PC.

---

### Post by Vadi on 2008-11-24
If you're on nvidia, it could be the drivers. Make sure they're the latest stable (177). If you're on that, maybe give 180.06 a try - they're a beta and a pita to install, but did speed up javascript performance for pages that were freezing/being slow.

---

### Post by Sealbhach on 2008-11-24
> **altonbr said:**
> 
I know TraceMonkey (a JavaScript intrepeter) will be coming out for Firefox 3.1 and it advertising amazing speedups[1], but even if it were to be released today, we wouldn't be able to use it until 9.04.



You can get Firefox 3.1 now, although it's Alpha. I'm using it right now. You can get it here:

[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/)

Extract the tar.bz2 in your /home folder and a new folder called "firefox" will be created. Then to run it just:

/home/username/firefox/firefox

It's so much faster than 3.0.....:)


.

---

### Post by altonbr on 2008-11-24
> **Vadi said:**
> If you're on nvidia, it could be the drivers. Make sure they're the latest stable (177). If you're on that, maybe give 180.06 a try - they're a beta and a pita to install, but did speed up javascript performance for pages that were freezing/being slow.

> **Sealbhach said:**
> You can get Firefox 3.1 now, although it's Alpha. I'm using it right now. You can get it here:

[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/)

Extract the tar.bz2 in your /home folder and a new folder called "firefox" will be created. Then to run it just:

/home/username/firefox/firefox

It's so much faster than 3.0.....:)


.

Those are both great suggestions, but do you know why Firefox 3 is so much slower in Linux than on Windows using the same machine? It feels REALLY sluggish.

I'll play with my add-ons and user profiles.

Thanks for the link to 3.1, I'm looking forward to trying it!

---

### Post by sharon.gmc on 2008-11-24
I have the same problem. . . I always go to Digg.com. . .

---

### Post by altonbr on 2008-11-24
PS: running 'firefox' in that .tar.bz opens up my Firefox 3.0.4 and running 'firefox-bin' returns:
> firefox-bin: error while loading shared libraries: libxul.so: cannot open shared object file: No such file or directory

EDIT: Sorry, it was because 3.0.4 was currently open and apparently it can't run the two synchronously.

It's still no where near the performance of 3.0 on Windows unfortuantely. It is very very sugglish... I'm wondering if I should wipe my settings/OS here soon.

---

### Post by altonbr on 2008-11-24
> **sharon.gmc said:**
> I have the same problem. . . I always go to Digg.com. . .

Have you tried any other browsers or versions of Firefox?

---

