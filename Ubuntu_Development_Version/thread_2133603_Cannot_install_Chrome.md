---
title: "Cannot install Chrome"
date: 2013-04-08
forum: Ubuntu Development Version
---

### Post by monkeybrain2012 on 2013-04-08
Chrome doesn't install in 13.04 because of missing dependency (libudev0 >=147) The library has been removed from Raring repository (have libudev1 instead) To install Chrome one needs to download the missing lib from Quantal's repository.

[http://handytutorial.com/install-google-chrome-in-ubuntu-13-04-fix-dependency-problem/](http://handytutorial.com/install-google-chrome-in-ubuntu-13-04-fix-dependency-problem/)

It seems quite unacceptable that the user would need to go to repository for older releases of Ubuntu to hunt down missing pieces in order to install a very popular piece of software. Hope this will be fixed by release.

---

### Post by sanderj on 2013-04-08
Checking: You really mean Chrome, not Chromium?

FWIW: I'm running **Chromium** Version 25.0.1364.160 Ubuntu 13.04 (25.0.1364.160-0ubuntu3), and that installs as it should

---

### Post by monkeybrain2012 on 2013-04-08
> **sanderj said:**
> Checking: You really mean Chrome, not Chromium?

FWIW: I'm running **Chromium** Version 25.0.1364.160 Ubuntu 13.04 (25.0.1364.160-0ubuntu3), and that installs as it should

I mean Chrome, not Chromium. I installed the deb from Google as in Precise and Quantal, it then creates a repository for upgrading. I use Chrome + Firefox.

---

### Post by VinDSL on 2013-04-08
If you mind living on the ragged edge (after all, we're testers)...

You might want to try Canary unstable/untested -- straight off the trunk!  :D

LINK:  [http://download-chromium.appspot.com/](http://download-chromium.appspot.com/)

Currently running (as I type):  "Version 28.0.1470.0 (192941)"

Works great on my Raring install.  No fiddling around with old versions of udev.  ;)

---

### Post by calebmolstad on 2013-04-08
Similar thread[URL="http://ubuntuforums.org/showthread.php?t=2132483"]
http://ubuntuforums.org/showthread.php?t=2132483[/URL]

---

### Post by craig10x on 2013-04-08
Ahh...but Chrome has its own built in (and current flash which we don't get anymore from adobe....chrome has an agreement with adobe to provide up to date versions with pepper) and also a very convenient web pdf reader (so you can look at a pdf file without downloading it to your drive but with the option to do that as well)...That is why many prefer Chrome over Chromium (although i know you can ADD those to Chromium but it is nice to get it "stock" as it were)...

That dependency thing does need to get fixed...it's gonna cause a problem for those installing the latest 13.04s...I ran the beta live and sure enough, had to add that dependency to get chrome to install...
no problem when i installed 13.04 because that was way before the change...

Vin...he can go bleeding edge canary with Chrome too...and i've sometimes run Chrome beta on live sessions and it seemed fine....on my installed ubuntu i am a bit more "chicken" and run stable ;) :D

In fact, when download the Chrome Deb, aside from putting the Chrome updater ppa in your software sources, if you look in the package manager you see all three version of Chrome (stable, beta, unstable) of course the one that is installed is stable, but at any time you can upgrade/downgrade from one version to another...

Again, that dependency problem needs to get fixed...hope it will be done by final release...

---

### Post by vasa1 on 2013-04-08
> **VinDSL said:**
> ...
Currently running (as I type):  "Version 28.0.1470.0 (192941)"
...
That means you should be running Google's recently forked [Blink engine]("http://blog.chromium.org/2013/04/blink-rendering-engine-for-chromium.html").

---

### Post by craig10x on 2013-04-09
They mentioned that "Blink" development just started in Canary...so, it will be some time before there are actual differences of "webkit"...right now, they are basically identical...

---

### Post by vasa1 on 2013-04-09
> **craig10x said:**
> They mentioned that "Blink" development just started in Canary...so, it will be some time before there are actual differences of "webkit"...right now, they are basically identical...

My understanding is that Chrome dev already has it.

See [http://techdows.com/2013/04/chrome-28-with-blink-now-available.html](http://techdows.com/2013/04/chrome-28-with-blink-now-available.html) at the bottom. But maybe it's still in Windows and not in Linux builds?

---

### Post by craig10x on 2013-04-09
Nice article link vasa 1...and it states that right in the beginning of the article: (it will get different as development comes along, of course)...
[COLOR=#111111][FONT=Georgia]
At present you can&#8217;t really spot/see any difference the way Chrome works with Blink as Google developers working on it and Chrome says on availability of it for Chrome as &#8220;very beginning, its really nothing that different from WebKit
[/FONT][/COLOR]

---

### Post by vasa1 on 2013-04-09
> **craig10x said:**
> ... its really nothing that different from WebKit

True dat so that the web developers don't panic ;) But it's supposed to be quicker with much less code. 

Right now I'm watching  [http://www.youtube.com/watch?v=TlJob8K_OwE](http://www.youtube.com/watch?v=TlJob8K_OwE) on the topic.

---

### Post by LinuXXuniL on 2013-04-09
Download and install with ubuntu software center libudev0_175-0ubuntu19_i386.deb (you will find it with google on launchpad)
Then download and install the latest chrome as you usualy do.

---

### Post by craig10x on 2013-04-09
Yep...from what i read about, it sounds like "blink" will really make quite a bit of improvements in Chrome....faster, more lean and mean (lol) and no doubt, even more stable... :)
The only reason you wouldn't see much if any difference at the moment is because they just added it in, and now they have to start working on it's development...

---

### Post by VinDSL on 2013-04-10
Blink, baby!  :D

Trunk build just started looking more appealing, yes?


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-10-apr-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-10-apr-2013-1.png")[/INDENT]

---

