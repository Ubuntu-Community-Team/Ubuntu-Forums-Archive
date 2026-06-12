---
title: "Chromium PPA"
date: 2009-03-17
forum: The Cafe
---

### Post by unoodles on 2009-03-17
I just read [this article on slashdot]("http://tech.slashdot.org/article.pl?sid=09/03/17/2345216") about a chromium ppa for ubuntu.
I tried it out and it actually feels pretty smooth, even though it is pre-alpha. (Though tabs didn't work for me :D )
I just tried the Acid 3 test, and got a 99/100. Not bad at all.

What do you think?

---

### Post by konqueror7 on 2009-03-17
thanks for the info, works good on me here...:D

---

### Post by pt123 on 2009-03-17
cant wait to try it once home

---

### Post by Skripka on 2009-03-17
FYI-We were discussing this on nOOST-the "Chormium PPA" is actually a hackish Wine-based way of running Windows Chrome in Linux

---

### Post by namegame on 2009-03-17
> **Skripka said:**
> FYI-We were discussing this on nOOST-the "Chormium PPA" is actually a hackish Wine-based way of running Windows Chrome in Linux

Here's a link. :P

[http://grubbn.org/otheros/showthread.php?tid=155](http://grubbn.org/otheros/showthread.php?tid=155)

---

### Post by smartboyathome on 2009-03-17
> **Skripka said:**
> FYI-We were discussing this on nOOST-the "Chormium PPA" is actually a hackish Wine-based way of running Windows Chrome in Linux

Actually, as said on the nOOST forums, the *Arch Linux* Chromium package is based on Crossover's attempt to run Chromium in Wine. This is built from Chromium's own SVN repository, not a snapshot for Windows.

---

### Post by Changturkey on 2009-03-18
Any idea when Chrome/Chromium will get plugins?

---

### Post by unoodles on 2009-03-18
I'm with Smartboyathome on this one. I am quite sure that this is actually a native Linux build.

> **Changturkey said:**
> Any idea when Chrome/Chromium will get plugins?

Probably a pretty long time. Right now, things are pretty early.

---

### Post by smartboyathome on 2009-03-18
> **Changturkey said:**
> Any idea when Chrome/Chromium will get plugins?

Probably not for a while. :(

---

### Post by pt123 on 2009-03-18
[http://tech.slashdot.org/article.pl?sid=09/03/17/2345216](http://tech.slashdot.org/article.pl?sid=09/03/17/2345216)

on slashdot there is post saying it is not.

I remember reading that version 2 removes the dependency on WinHTTP (?) there by allowing Google to release Chrome for Mac & Linux

---

### Post by TiGR on 2009-03-18
Is that only me having trouble trying to run it? I've added hardy ppa chromium repository (deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) hardy main) and installed chromium-browser. But when I try to lauch it it just says:```
[8044:8044:9742905376:ERROR:common/temp_scaffolding_stubs.cc(215)] Not implemented reached in static bool Upgrade::IsBrowserAlreadyRunning()
[8044:8044:9742961601:ERROR:common/temp_scaffolding_stubs.cc(195)] Not implemented reached in static bool FirstRun::IsChromeFirstRun()
Illegal instruction
```
Any ideas?

---

### Post by shellster on 2009-03-18
I am having the same problem.  I haven't figured anything out yet.

---

### Post by smartboyathome on 2009-03-18
> **pt123 said:**
> [http://tech.slashdot.org/article.pl?sid=09/03/17/2345216](http://tech.slashdot.org/article.pl?sid=09/03/17/2345216)

on slashdot there is post saying it is not.

I remember reading that version 2 removes the dependency on WinHTTP (?) there by allowing Google to release Chrome for Mac & Linux

But it is a genuine Linux program, read about it on their site:

[http://dev.chromium.org/Home](http://dev.chromium.org/Home)

:)

---

### Post by Hells_Dark on 2009-03-18
Works fine here. It's really fast.

---

### Post by trickyD on 2009-03-18
Just added the ppa.launchpad.net repositories for Hardy - same error when I try and launch it from the shell.

```
chromium-browser: Symbol `SSL_ImplementedCiphers' has different size in shared object, consider re-linking
[6587:6587:1094347508:ERROR:common/temp_scaffolding_stubs.cc(215)] Not implemented reached in static bool Upgrade::IsBrowserAlreadyRunning()
[6587:6587:1094347692:ERROR:common/temp_scaffolding_stubs.cc(195)] Not implemented reached in static bool FirstRun::IsChromeFirstRun()
Illegal instruction
```

Damn shame, guess I'll have to hang on a little longer.

-- 
tD

---

### Post by coolbrook on 2009-03-18
I'm also experiencing that error (on Hardy.)   I'll have to try an install on one of my Intrepid machines.

---

### Post by mbrubeck on 2009-03-18
I'm getting the "Illegal Instruction" error too.  Someone on Slashdot thought Chromium might be using instructions that aren't available on older AMD (or other old/non-Intel) CPUs.  My computer fits that description (AMD Athlon), does yours?

---

### Post by DougieFresh4U on 2009-03-18
Getting the ole 'missing public key' Can some one point me to it, please?

---

### Post by pt123 on 2009-03-19
> **smartboyathome said:**
> But it is a genuine Linux program, read about it on their site:

[http://dev.chromium.org/Home](http://dev.chromium.org/Home)

:)

when I said "not", I was refering it to NOT using Wine

---

### Post by trickyD on 2009-03-19
> **mbrubeck said:**
> I'm getting the "Illegal Instruction" error too.  Someone on Slashdot thought Chromium might be using instructions that aren't available on older AMD (or other old/non-Intel) CPUs.  My computer fits that description (AMD Athlon), does yours?

Yeah - mine is an old Athlon XP 3200+ ...

--
tD

---

### Post by trickyD on 2009-03-19
> **DougieFresh4U said:**
> Getting the ole 'missing public key' Can some one point me to it, please?

Good instructions here:

[http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)

-- 
tD

---

### Post by smilingfrog on 2009-03-20
The signing key is found [here]("https://launchpad.net/~chromium-daily/+archive/ppa") on launchpad.

I also am running hardy on AMD3200+, and I can't get chromium to work. Same errors. What system/distro do people have it working on?

---

### Post by coolbrook on 2009-03-20
I'm getting the same result on an Intrepid machine.

---

### Post by Sunflower1970 on 2009-03-20
Tried Chromium a few days agon on Intrepid, and was getting the same errors as others. I just uninstalled it. I'll wait till it's further along.

---

### Post by DougieFresh4U on 2009-03-20
> **smilingfrog said:**
> The signing key is found [here]("https://launchpad.net/~chromium-daily/+archive/ppa") on launchpad.

I also am running hardy on AMD3200+, and I can't get chromium to work. Same errors. What system/distro do people have it working on?

Thanks for link to key, I knew how to install key, just didn't know where it was as I picked up ppa in thread and no key with it

I am running Jaunty and chrome is working....sort of.......

---

### Post by TiGR on 2009-03-24
> **mbrubeck said:**
> Someone on Slashdot thought Chromium might be using instructions that aren't available on older AMD (or other old/non-Intel) CPUs.  My computer fits that description (AMD Athlon), does yours?
Maybe. I've been testing it on quite old machine  with Celeron 1.3 GHz, experiencing this "Illegal Instruction" error.

---

### Post by Delever on 2009-03-26
Yay! Tabs!

Not working right, but anyway...

Tabs! Tabs! Tabs! Yay!

---

### Post by edam on 2009-03-26
Works ok here (64-bit intrepid on intel core 2 quad).

Well, I say "works"... No other windows open (options, about, print, etc). And while the new tabs are very nice indeed, it's a pity they don't work at all! You can't switch/close/move them! :P

Still... great start!

---

### Post by Giant Speck on 2009-03-26
> **Delever said:**
> Yay! Tabs!

Not working right, but anyway...

Tabs! Tabs! Tabs! Yay!


Yay!  I see them, too!

However, I am still not able to access anything in the Wrench Menu.  Not even Options.  :(

---

### Post by ghindo on 2009-03-30
Just tried it out on Jaunty and it's still very, VERY unstable.  Nothin' to do but wait and keep updating.  :popcorn:

---

### Post by MonkeeSage on 2009-04-06
The is a known problem: [#9007](http://code.google.com/p/chromium/issues/detail?id=9007). It is caused by a dependency on SSE2 opcodes, so it breaks on any non-SSE2 CPU (e.g., PIII, Athlon). Should be fixed eventually.

---

### Post by Giant Speck on 2009-04-06
Whoo!  I can switch between tabs now!  :)

If only I could close them.  And too bad the wrench menu still doesn't work.  :(

---

### Post by bluebyt on 2009-04-19
Since I updated this morning, I can save images now!

I like it a lot, Chromium is very fast!

---

### Post by vishnu on 2009-06-01
anyone got flash player working on it yet?

---

### Post by sports fan Matt on 2009-06-01
Is there a way to make the bookmarks appear one after the other (and more importantly, to have them not take up the entire screen?)

---

### Post by Tipped OuT on 2009-06-01
How do I download and install this? :confused:

---

### Post by sports fan Matt on 2009-06-01
See if this post helps: [http://gizmodo.com/5173257/google-chrome-passes-into-20-beta-chromium-for-linux-gets-a-simple-install](http://gizmodo.com/5173257/google-chrome-passes-into-20-beta-chromium-for-linux-gets-a-simple-install)

---

