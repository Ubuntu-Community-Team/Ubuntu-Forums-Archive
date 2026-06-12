---
title: "The addicting &quot;falling sand game.&quot; Is it downloadable?"
date: 2007-12-04
forum: The Cafe
---

### Post by Roasted on 2007-12-04
[http://chir.ag/stuff/sand/](http://chir.ag/stuff/sand/)

I love it. I play it all day during boring classes. However, our WLAN is down, so I'd like to find a downloadable version to play without internet. If it's available for Linux (preferably Fedora Core 8, since that's what my laptop has) that'd be great. If not, I dual boot with Vista. 

Any ideas, fellas?

---

### Post by bobbocanfly on 2007-12-04
There are loads of non web versions of this game the most popular being Burning Sand and wxSand. Try and find the Falling Sand Games forum (yes it exists :D) and ask for a Linux version there. If not, im pretty sure Burning Sand works in Wine but have never tried it.

---

### Post by Lostincyberspace on 2007-12-04
how do you play it? I cant figure it out and it is driving me crazy.

---

### Post by FuturePilot on 2007-12-04
> **Lostincyberspace said:**
> how do you play it? I cant figure it out and it is driving me crazy.

I don't know but that thing grew so big it ate everything :shock:

---

### Post by Lostincyberspace on 2007-12-04
> **FuturePilot said:**
> I don't know but that thing grew so big it ate everything :shock:

I know I thought maybe you had to guide the sand so it didn't hit it, but it just went and ate the walls

---

### Post by Roasted on 2007-12-04
There's really no objective to it. It's just simply to be entertaining. The sand and whatnot can certainly fall to the bottom of the screen. 

Just use the tools on the right side to adjust the flow of the oil, sand, water, and salt. It's just something to kill time, and it's a lot of fun at the same time.

For the record, I downloaded WxSand. I downloaded it in XP (my school computer) and used my jumpdrive to bring the tar.gz over to Fedora Core 8 on my laptop. I unpacked the tarball and CD'd into the directory and ran ./configure. However, it wouldn't run. It said no such file or directory. Yet, I was in the directory, trying to run the typical ./configure command.

GRRRRRRR

---

### Post by igknighted on 2007-12-04
It's a java applet... all you need to do is save the page, yes?

---

### Post by PartisanEntity on 2007-12-04
It's cool, it reminds me of this in a way:
[http://www.isnichwahr.de/r37542112-crayon-physics.html](http://www.isnichwahr.de/r37542112-crayon-physics.html) (anyone know what this is?)

---

### Post by bobbocanfly on 2007-12-04
> **Lostincyberspace said:**
> how do you play it? I cant figure it out and it is driving me crazy.

Its a sandbox game. You make up the rules and play. That big thing can be turned off so you are just guiding the elements around the screen.

There are modders who write things for Burning Sand like a Nuclear Reactor mod etc. Its pretty cool.

---

### Post by IISpII on 2007-12-04
youll like this

[http://siebn.de/index.php?page=burningsand/game&PHPSESSID=3b76b100f427c313c95fda56bff08416](http://siebn.de/index.php?page=burningsand/game&PHPSESSID=3b76b100f427c313c95fda56bff08416)

:lolflag:

---

### Post by Roasted on 2007-12-05
Anybody else have a version of this game that can be downloaded to Linux? Preferably RPM or Tar.gz, since this laptop has Fedora...

I got a tar.gz of it but it is like... not a tar.gz... I know, sounds weird. When I open it up, there's an exe inside. I'm completely confused. Whoever packed this doesn't appear to have known what they were doing. Either that or I'm a complete idiot.

Any other ideas, folks?

---

### Post by FuturePilot on 2007-12-05
Well I came across this
[http://www.piettes.com/fallingsandgame/download.html]("http://www.piettes.com/fallingsandgame/download.html")
looked promising however it won't run
```
./fsg-4.4 
./fsg-4.4: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory

```

---

### Post by Hortinstein on 2007-12-05
hhaha i just came accross this game a few weeks ago...i kinda want to make my own for a programming project

---

### Post by Roasted on 2007-12-06
No input? I'd REALLY like a downloadable version so I can play it when I'm not near an access point.

---

### Post by smartboyathome on 2007-12-06
> **FuturePilot said:**
> Well I came across this
[http://www.piettes.com/fallingsandgame/download.html]("http://www.piettes.com/fallingsandgame/download.html")
looked promising however it won't run
```
./fsg-4.4 
./fsg-4.4: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory

```

Try this in a terminal, and then try running that again.
sudo ln -s libpng.so libpng.so.3

---

### Post by Gammell on 2008-01-09
> **Roasted said:**
> For the record, I downloaded WxSand. I downloaded it in XP (my school computer) and used my jumpdrive to bring the tar.gz over to Fedora Core 8 on my laptop. I unpacked the tarball and CD'd into the directory and ran ./configure. However, it wouldn't run. It said no such file or directory. Yet, I was in the directory, trying to run the typical ./configure command.
That sounds like configure might be missing the execute permission. Did you unpack it in windows? That will strip the file permissions... Actually just unpacking it onto a VFAT fs might be enough to screw up permissions even from within Linux (I'm not sure how VFAT behaves)... I dunno, maybe you unpacked it in Linux to an ext3 partition and none of this is relevant, just a thought.

---

