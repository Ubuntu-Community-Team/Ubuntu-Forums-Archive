---
title: "Executables instead of tar.gz files"
date: 2008-11-25
forum: The Cafe
---

### Post by fredscripts on 2008-11-25
Hi!!


After thinking about the experience of trying to download and install a simple theme and a simple usplash-screen from gnome-look on my Ubuntu, having issues that seemed easy to solve but with no answer here in this forums([http://ubuntuforums.org/showthread.php?t=991241](http://ubuntuforums.org/showthread.php?t=991241)) nor in IRC, I've thought about a change:

Why not simple "CoolDark.theme" or "NiceFinger.usplash" executable files that run all the configurations needed to install the theme or the usplash (or icons, or whatever of gnome-look), instead of annoying tar.gz files plenty of README, HOW-TO's that are different for every theme that even after following them still not work properly?

I hope future versions of Ubuntu will include support on that , as that's one of the reasons I love Ubuntu.

What do you think?

---

### Post by blueturtl on 2008-11-25
> Why not simple "CoolDark.theme" or "NiceFinger.usplash" executable files that run all the configurations needed to install the theme or the usplash (or icons, or whatever of gnome-look), instead of annoying tar.gz files plenty of README, HOW-TO's that are different for every theme that even after following them still not work properly?

For security reasons obviously.

I thought installing themes in Ubuntu was as simple as dropping the .tar.gz files into the Appearance/Themes window?

edit: I read your help thread and to me it seems like maybe you have a broken/poorly designed theme.

Most themes install fine by simply drag&dropping them into the Appearance window, in my experience at least.

---

### Post by Paqman on 2008-11-25
A theme doesn't need to be executable, it's just a bunch of files.

Tar.gz is just a compressed container, like .zip or .rar. It's just a handy way of someone bundling a lot of files together.

---

### Post by bufsabre666 on 2008-11-25
for themes: go system to preferences to appearance, on the first screen click install and select the tarball... there its installed

and for upsplashes install a program called start up manager

```
sudo apt-get install startupmanager
```

and they have an option on the second tab to add different upsplashes 

why do you need an installer? atleast this way you dont need to compile a binary for i386 amd64 arm ppc and the others

---

### Post by nothingspecial on 2008-11-25
On debian based distros we have .debs which install with a couple of clicks.

---

### Post by fredscripts on 2008-11-25
> **bufsabre666 said:**
> for themes: go system to preferences to appearance, on the first screen click install and select the tarball... there its installed

and for upsplashes install a program called start up manager

```
sudo apt-get install startupmanager
```

and they have an option on the second tab to add different upsplashes 

why do you need an installer? atleast this way you dont need to compile a binary for i386 amd64 arm ppc and the others

I already know how to install themes and usplashes...it just one day I tried to install a simple theme and a simple usplash screen from gnome-look following these methods...and no luck: [http://ubuntuforums.org/showthread.php?t=991241](http://ubuntuforums.org/showthread.php?t=991241)

Maybe I'm so unlucky that the first theme and usplash screen I've tried to install are damaged...

---

### Post by SunnyRabbiera on 2008-11-25
well first of all that theme right there is probably not set up to use the standard theme manager that we use, some themes are like this.
as for usplash there I can see why possibly you would have issues, first of all usplash is a part of the root of the system so its not like a simple change to a few toolboxes here and there.
Usplash really cant have executables as you wish as really that can allow bad things to happen to your system if you dont know what it is.
hey loading a boot theme on windows is not much easier, you have to download questionable software just to make it look the way you want it and YES stardock software is questionable software dont kid yourself.

---

### Post by Bölvaður on 2008-11-25
Listen to sunny... there is a reason why he has that many thanks :KS
Im not going to add more thanks to his counter because it's too high for me not to get jealous.
So it has to be written consent +1 Sunny :popcorn:


I want to add that an binary executable would probably be very bad thing as it usually wouldnt work for most users because they have different setup than the theme is setup for.
.deb would be possible and you actually can find themes that are set up as .deb

but the bottom line is that most themes are now they are more accessible for everyone than they would in an executable file.

---

### Post by nothingspecial on 2008-11-25
> **Bölvaður said:**
> Listen to sunny... there is a reason why he

Not he - she. See here -



[http://ph.ubuntuforums.com/showthread.php?t=948104](http://ph.ubuntuforums.com/showthread.php?t=948104)

---

### Post by Bölvaður on 2008-11-25
> **nothingspecial said:**
> Not he - she. See here -



[http://ph.ubuntuforums.com/showthread.php?t=948104](http://ph.ubuntuforums.com/showthread.php?t=948104)

Oh my.. I thought sunny was a she from her writings in the past but I never knew so I went the safe way and refer to her as "he" as most users here seemed to be male :(
Im sorry

Forgiveness?

---

### Post by nothingspecial on 2008-11-25
Don`t ask me, ask Sunny. :)

---

### Post by SunnyRabbiera on 2008-11-25
> **Bölvaður said:**
> Oh my.. I thought sunny was a she from her writings in the past but I never knew so I went the safe way and refer to her as "he" as most users here seemed to be male :(
Im sorry

Forgiveness?

its all cool

---

