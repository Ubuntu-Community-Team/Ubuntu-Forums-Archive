---
title: "Anyone know of a Duke Nukem for Linux?"
date: 2009-08-24
forum: The Cafe
---

### Post by bodyharvester on 2009-08-24
hi,

anyone? i registered at the forum ([http://forums.3drealms.com/vb/showthread.php?t=36279&page=3)to](http://forums.3drealms.com/vb/showthread.php?t=36279&page=3)to) show my unwavering support for Duke Nukem Forever but i cant find any info on whether Duke Nukem 3d is on linux, i saw something about it on sourceforge but i dont think theyll be done for a while, id love to pklay Duke Match online, but my only connection to the net is the wireless card in my laptop.

any info would be appreciated, thanks
p.s. im well aware not to expect the game (DNF) to be released, npot until take two stop the court case which begins next year

---

### Post by RiceMonster on 2009-08-24
Duke Nukem 3D works great in DosBOX. Try it.

---

### Post by Dark Aspect on 2009-08-24
> **RiceMonster said:**
> Duke Nukem 3D works great in DosBOX. Try it.

Why not run it native with [eduke32]("http://www.eduke32.com/"). I have Duke Nukem 3D running via that and Duke Nukum 1/Duke Nukem II running though Dosbox.

Theres a few other Native options as well, though eduke32 is the newest/best.

[http://icculus.org/duke3d/]("http://icculus.org/duke3d/")
[http://icculus.org/~ravage/duke3d/]("http://icculus.org/~ravage/duke3d/")
[http://www.jonof.id.au/jfduke3d]("http://www.jonof.id.au/jfduke3d")

---

### Post by bodyharvester on 2009-08-24
is eduke32 gonna need wine?

i cant find my Duke Nukem: Atomic Edition cd anywhere :(

---

### Post by Dark Aspect on 2009-08-24
> **bodyharvester said:**
> is eduke32 gonna need wine?

No, native code does not require wine. Please see the [eduke32 Linux installation guide]("http://wiki.eduke32.com/wiki/Building_EDuke32_on_Linux"). Heres a short run down for you,

```
sudo apt-get install build-essential libsdl1.2-dev libsdl-mixer1.2-dev nasm libstdc++6-4.3-dev libgtk2.0-dev
```

[Download eduke32 source code here]("http://dukeworld.duke4.net/eduke32/source_code/eduke32_src_20090131.zip")

cd to the source code directory and compile

```
make veryclean && make RELEASE=0
```

---

### Post by bodyharvester on 2009-08-24
thanks, 
now just to find that pesky disk :confused:

:) and then its off to kick some a** and chew some bubblegum, and im all outta gum:)

---

### Post by fugazi32 on 2009-11-04
> **RiceMonster said:**
> Duke Nukem 3D works great in DosBOX. Try it.

Waaaayyyheeeeey! Found my old Duke Nukem CD, it works fine in DosBox and @ a decent speed too. Used to have a native port running in SuSE 10.0 but the script doesn't run in Xubuntu 8.10. Oh well, at least i've got it working again anyhow! :D

---

### Post by forrestcupp on 2009-11-04
> **Dark Aspect said:**
> Why not run it native with [eduke32]("http://www.eduke32.com/"). I have Duke Nukem 3D running via that and Duke Nukum 1/Duke Nukem II running though Dosbox.

Wow!  Thank you.  I was just talking yesterday about how I wish someone would update Duke Nukem 3D to have modern graphics and controls.  This is unbelievable.

I lost my disk many years ago.  I think this is worth spending the $5.99 to download Duke 3D.

---

### Post by hoppipolla on 2009-11-04
> **forrestcupp said:**
> Wow!  Thank you.  I was just talking yesterday about how I wish someone would update Duke Nukem 3D to have modern graphics and controls.  This is unbelievable.

I lost my disk many years ago.  I think this is worth spending the $5.99 to download Duke 3D.

2nded! I think it looks wicked! :)

---

### Post by forrestcupp on 2009-11-04
> **hoppipolla said:**
> 2nded! I think it looks wicked! :)

I guess it's the next best thing to Duke Nukem Forever.


My wife once had a boss named Paul Newcomb.  I told her she should ask if he's related to Duke. :)

---

### Post by Bjalf on 2009-11-04
> **forrestcupp said:**
> Wow!  Thank you.  I was just talking yesterday about how I wish someone would update Duke Nukem 3D to have modern graphics and controls.  This is unbelievable.
Google "*Duke Nukem 3D High Resolution Pack*"

---

### Post by Simian Man on 2009-11-04
Why not just wait for Duke Nukem Forever?  I hear they are supposed to be releasing a GNU Hurd version sometime next year.

---

### Post by RiceMonster on 2009-11-04
> **Simian Man said:**
> Why not just wait for Duke Nukem Forever?

Haha, is it bad that I just noticed how appropriate the name is? That statement is funny in more ways than one :p.

---

### Post by hoppipolla on 2009-11-04
> **RiceMonster said:**
> Haha, is it bad that I just noticed how appropriate the name is? That statement is funny in more ways than one :p.

you have to admit if it comes out it would be amazing though! The footage I saw on Youtube was awesome! :)

---

### Post by CharmyBee on 2009-11-04
I stopped waiting for DNF when the 2001 version was scrapped.

---

### Post by 3rdalbum on 2009-11-04
> **RiceMonster said:**
> Haha, is it bad that I just noticed how appropriate the name is? That statement is funny in more ways than one :p.

The third Spice Girls album was released a year late, and ended off being called "Forever". We used to reckon it was a reference to how long it took to record :-)

---

### Post by Warpnow on 2009-11-05
You can always just emulate the console versions of Duke Nukem. Ubuntu has most emulators in its repositories.

---

### Post by NCLI on 2009-11-05
This is awesome!! I never knew something like this existed!! :KS

---

### Post by schauerlich on 2009-11-05
> **Simian Man said:**
> Why not just wait for Duke Nukem Forever?  I hear they are supposed to be releasing a GNU Hurd version sometime next year.

You stole my joke. :|

---

### Post by forrestcupp on 2009-11-05
> **Bjalf said:**
> Google "*Duke Nukem 3D High Resolution Pack*"

Looks pretty awesome.  It appears that this has eduke32 built into it.  Is that right?  If so, I guess I don't need both.

Thanks for the tip.

---

### Post by forrestcupp on 2009-11-06
I tried out the high res pack with the shareware demo of Duke 3D.  It's awesome.  The only problem I had was that it wasn't set up out of the box to use the new textures and models.  I had to do some research to find out you have to turn the autoload option on to use them.  After I did that, I wasn't disappointed at all.

It's not like a Crysis or anything, but it's still an awesome update to a great old game.  These guys did an excellent job.

---

