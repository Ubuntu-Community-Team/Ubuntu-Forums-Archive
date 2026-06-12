---
title: "Crackling sound on fullscreen games and LMMS"
date: 2010-02-08
forum: Ubuntu Studio
---

### Post by ArtzP on 2010-02-08
Hello!
I have fresh install of ubuntu 9.10 with new computer. I have same issue again. No sound on games - or wierd crackling sound. I tried openarena and alienarena. Also tried LMMS. I have struggeled same problem earlier, but managed to fix it with compiling alsa drivers. I cannot remember anymore how to do it. Other sounds are running correctly.
Looking forward for your advise

---

### Post by mörgæs on 2010-02-09
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

---

### Post by ArtzP on 2010-02-12
Thank you. I already managed to fix it with compiling Alsa drivers. 
[http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/)  I don't know what error this fixes, but it helps. Next time I try other option. That compiling-installing takes too much time (half an hour at least).

---

### Post by AutoStatic on 2010-02-13
Hello ArtzP, good to hear that you got it to work. Hopefully there won't be any future updates that will bork your sound again. To quote [myself]("http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/#comment-521"):

> People should stop posting “howto’s” like this without a big warning that it could bork your sound or that following the “howto” is at your own risk. Upgrading ALSA this way is not the way to go, it can break your audio stack and then I didn’t consider any upcoming ALSA related updates. Francesco Conti has got it right in #42, install linux-backports-modules-karmic which will update ALSA like it should for Ubuntu.
Or… The other way around, people should stop following any “howto” out there on the web that seems authoritative. Next thing you know is that they ditch Ubuntu because they can’t get sound to work and blame Ubuntu for it because they didn’t get it right in the first place. And that while it’s 100% sheer PEBKAC in most cases.
Sorry for the rant but upgrading ALSA as described above should be the very, very last resort. First check the Ubuntu Help and Wiki pages, then ask on the Ubuntu forum and check Launchpad if no bugs are filed concerning your issue.

Best,

Jeremy

---

### Post by mango42 on 2010-02-13
> **AutoStatic said:**
> Hello ArtzP, good to hear that you got it to work. Hopefully there won't be any future updates that will bork your sound again. To quote [myself]("http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/#comment-521"):

Good, positive rant there, too ;-)

Yet it opens such a can of worms - everyone is trying to help the best they can but most of us really don't have the first clue why certain commands (and howto's) are better than others. We either lack the foundation, the inclination or the ability - sometimes all three...

Right now I feel like my head is spinning from trying to get stuff working, and I was once a hardware designer (and programmer of sorts, assembler & low level C), so not entirely 'just a user'

I'd like to be, though, as my compiling days are but a dim memory. ;-)

ps: Could I make a plea for ALL Ubuntu information, wherever found, to be clearly **dated** in the heading - it's enough of a minefield already (inevitable in such an extraordinary global endeavour!) without inadvertently delving into obsolete pearls of wisdom, particularly commandline code :confused:

---

### Post by AutoStatic on 2010-02-13
I completely agree with you mango42. If there is one supposed authoritative Wiki that suffers from obsolete pearls of wisdom then it has to be the Ubuntu Wiki unfortunately :(

---

### Post by jerrylamos on 2010-02-13
> **AutoStatic said:**
> Hello ArtzP, good to hear that you got it to work. Hopefully there won't be any future updates that will bork your sound again. To quote [myself]("http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/#comment-521"):

I'm running Karmic & Lucid.  There are LOTS of updates that BORK everything, and these forums save my neck.

Jerry

---

