---
title: "Can You/How Do You Change the GRUB Bootloader skin?"
date: 2006-03-21
forum: The Cafe
---

### Post by Swiss on 2006-03-21
Can You/How Do You Change the GRUB Bootloader skin?

---

### Post by Brunellus on 2006-03-21
uh, GRUB loads before X, and so thus is not really "skinnable"

---

### Post by Swiss on 2006-03-21
Look here: [http://www.gnusolaris.org/gswiki/Getting_Started#head-76c76195679b0098d0d34e2d28e2e8c55a9e087f](http://www.gnusolaris.org/gswiki/Getting_Started#head-76c76195679b0098d0d34e2d28e2e8c55a9e087f)

And elseware on this forum I have heard mention of "skinning GRUB"

---

### Post by Bandit on 2006-03-21
[QUOTE=Brunellus]uh, GRUB loads before X, and so thus is not really "skinnable"[/QUOTE]
Actualy SuSE and Mandrake have been doing that for the past 6 years..

---

### Post by cyberb0b on 2006-03-21
Do you mean adding a splash image?  See this post:

[http://www.ubuntuforums.org/showthread.php?t=30341](http://www.ubuntuforums.org/showthread.php?t=30341)

---

### Post by Swiss on 2006-03-21
Yep, Thanks! Thats exactly what I was looking for! :D \\:D/

---

### Post by Jucato on 2006-03-21
I wonder when we'll have those GRUB GUI splash screens, like some of the distros out there. Not really a necessity. Just makes things look nicer. :D

---

### Post by Brunellus on 2006-03-21
[QUOTE=Fenyx]I wonder when we'll have those GRUB GUI splash screens, like some of the distros out there. Not really a necessity. Just makes things look nicer. :D[/QUOTE]
Ick.

Now having looked at the bootsplash pages, I think I might go about disabling it for dapper.  ever since ubuntu went to bootsplash, my textmode consoles are all messed up.

---

### Post by localzuk on 2006-03-21
Take a look at [http://ruslug.rutgers.edu/~mcgrof/grub-images/](http://ruslug.rutgers.edu/~mcgrof/grub-images/)

There is a wealth of info there :)

---

### Post by Jucato on 2006-03-21
Hmm.. let me get my terms correct (please correct me if I'm wrong)

GRUB splash - splash image seen in the GRUB bootloader
Bootsplash - the part where you see all those initializing/loading lines
USplash/KSplash - splash screen when logging into GDM/KDM

So if I'm not mistaken, in Ubuntu, GRUB splash is text, Bootsplash is graphic, and of course USplash is graphic.

What I was wondering about was a graphical GRUB splash like SUSE ([http://shots.osdir.com/slideshows/slideshow.php?release=464&slide=1)](http://shots.osdir.com/slideshows/slideshow.php?release=464&slide=1)).

---

### Post by jmn2k1 on 2006-03-26
In gnome-look ([http://www.gnome-look.org/content/show.php?content=29985](http://www.gnome-look.org/content/show.php?content=29985)) theres is grubs splash and the instructions to install...

---

### Post by infoseeker on 2006-03-26
Just be careful which splash image file you use. I downloaded a number of splash images and a small number of them caused my Ubuntu to hang on bootup...even before grub loads.  I had to sift though them one at a time and dumped those that caused a problem.  Right now I am using 'daren.xpm.gz' which works fine.
I had to edit the 'menu'lst' file with a bootable live cd (KNOPPIX) each time the hangs/lockups occured, but thats what Linux is all about, isn't it  :D

---

