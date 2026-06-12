---
title: "Remember the Falling Sand Game?"
date: 2008-03-14
forum: The Cafe
---

### Post by Mazza558 on 2008-03-14
Well, this program's way cooler...

[IMG]http://siebn.de/linux.jpg[/IMG]

It's actually a Windows program, meaning you need Wine to run it in Linux. Luckily, it runs AMAZINGLY well, and is great fun.

[LIST=1]
[*]Install Wine from the repos
[*]Download Burning Sand from [HERE]("http://siebn.de/download/burningsand20070320.zip")
[*]Extract it into any folder
[*]Right Click on Burning Sand.exe and click "run with Wine Windows Emulator"
[*]You can only close it by intentionally crashing it (as far as I know) - click on the "save" icon at the top and click "cancel".
[/LIST]

For more info, go here: 

[http://siebn.de/]("http://siebn.de/")

---

### Post by hessiess on 2008-03-14
cannot load font error

---

### Post by Mazza558 on 2008-03-14
> **hessiess said:**
> cannot load font error

Have you got the Microsoft fonts installed?

---

### Post by LaRoza on 2008-03-14
[http://enigmasand.com/pyro2.html](http://enigmasand.com/pyro2.html)

Online version as well.

---

### Post by LaRoza on 2008-03-14
[http://enigmasand.com/pyro2.html](http://enigmasand.com/pyro2.html)

Online version as well.

---

### Post by spupy on 2008-03-14
Please, guys, i have exams in two weeks!!!

coughthankscough

---

### Post by smartbei on 2008-03-14
I am also unable to run the application due to "Couldn't laod font." (Yes, either Wine or BurningSand has a spelling error).

I have msttcorefonts already installed.

---

### Post by Mazza558 on 2008-03-14
> **smartbei said:**
> I am also unable to run the application due to "Couldn't laod font." (Yes, either Wine or BurningSand has a spelling error).

I have msttcorefonts already installed.

Which version of WIne are you using?

---

### Post by smartbei on 2008-03-14
Apparently 0.9.46 - (the current default install via aptitude).

---

### Post by Onyros on 2008-03-14
[http://www.piettes.com/fallingsandgame/index.html](http://www.piettes.com/fallingsandgame/index.html)

This one runs natively in Linux, and it's great fun... :)

---

### Post by FuturePilot on 2008-03-14
> **Onyros said:**
> [http://www.piettes.com/fallingsandgame/index.html](http://www.piettes.com/fallingsandgame/index.html)

This one runs natively in Linux, and it's great fun... :)

Anyone get it to work?
```
fsg-4.4: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory

```

---

### Post by loudnlownoma on 2008-03-14
Nice!  Subscribing to check out when I get home from work.  I can't imagine how much time I wasted with the online version before the came up and upgraded all of our PC's and "forgot" to load/update Java and Flash....

Although I was able to run across a Pocket Sand a while back - very limited in features or options, but some of the original flavor to it.  Site seems to be temporarily closed, but I still have the .zip laying around for anyone looking for a great time-waster on their portable drive...

---

### Post by init1 on 2008-03-14
> **FuturePilot said:**
> Anyone get it to work?
```
fsg-4.4: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory

```
Just do a
```

sudo apt-get install libpng3

```
and it should run fine.

---

### Post by FuturePilot on 2008-03-14
Yes that did work however that is an old and no longer supported version of libpng. I'm trying to recompile it against the newer version but I'm not getting too far :(

---

### Post by FuturePilot on 2008-03-14
Ah. It just needed some linkage :D
```
sudo ln -s /usr/lib/libpng12.so.0 /usr/lib/libpng.so.3
```
should get it working :)

[[IMG]http://img291.imageshack.us/img291/7867/fallingsandgamewj2.th.png[/IMG]](http://img291.imageshack.us/my.php?image=fallingsandgamewj2.png)

---

### Post by icechen1 on 2008-03-14
Wxsand is better:[http://www.piettes.com/fallingsandgame/](http://www.piettes.com/fallingsandgame/). it got Gtk and you can download more objects over Internet!
I think i downloaded an older version of libpng(libpng3) to make it work.

---

### Post by Mazza558 on 2008-03-15
> **smartbei said:**
> Apparently 0.9.46 - (the current default install via aptitude).

Ah, that's probably why. It works on 0.9.55 for me.

---

### Post by §cinc§ on 2008-03-15
Thanks for the link.
This game is hours of fun.

---

### Post by neilnapier on 2008-11-09
Sorry for posting in an about 8 month old topic... but this isn't bumping as "bumping" implies it is an unnessisary post, which of course it isn't.

BurningSand2 is available for Linux.

BurningSand2 is stable and despite what you have said BS2 is better for SOOOO many reasons.  These include.

1.  Moddable, as is WxSand.  But BS2 can have 32K elements and 1000 elements per interaction.
2. It has a higher FPS and is much more moddable, so much so that it can be made into almost any program.
3. It is open source so if you need fit you can edit it (its written in C++)

Here is the link the the Linux compatible version:

[http://siebn.de/burningsand/linux/](http://siebn.de/burningsand/linux/)

It has been confirmed that it works.

I felt that I should "bump" this rather than make a new topic.  

I hope you try BS because it is excellent.

---

### Post by init1 on 2008-11-09
> **neilnapier said:**
> Sorry for posting in an about 8 month old topic... but this isn't bumping as "bumping" implies it is an unnessisary post, which of course it isn't.

BurningSand2 is available for Linux.

BurningSand2 is stable and despite what you have said BS2 is better for SOOOO many reasons.  These include.

1.  Moddable, as is WxSand.  But BS2 can have 32K elements and 1000 elements per interaction.
2. It has a higher FPS and is much more moddable, so much so that it can be made into almost any program.
3. It is open source so if you need fit you can edit it (its written in C++)

Here is the link the the Linux compatible version:

[http://siebn.de/burningsand/linux/](http://siebn.de/burningsand/linux/)

It has been confirmed that it works.

I felt that I should "bump" this rather than make a new topic.  

I hope you try BS because it is excellent.
Nice, works fine in 8.10

---

### Post by 0per4t0r on 2009-06-04
I love this game, and I run it off my flash drive thru wine, and it works great! Also, pyro sand 2 is not the same as BS2.

---

