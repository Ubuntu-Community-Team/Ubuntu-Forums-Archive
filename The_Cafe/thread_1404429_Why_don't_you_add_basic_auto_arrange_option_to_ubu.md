---
title: "Why don't you add basic auto arrange option to ubuntu?"
date: 2010-02-11
forum: The Cafe
---

### Post by aviramof on 2010-02-11
at least something basic to the desktop that would prevent files from going one on top of the other.

is there any particilular reason for that?

thanks in advance.

---

### Post by LKjell on 2010-02-11
Could be that metacity is stupid. Anyway try out xmonad it will do that for you.

---

### Post by aviramof on 2010-02-11
thank you very much i'll look into it.

ok i have managed to install it but now how do i use it?

---

### Post by jpeddicord on 2010-02-11
> **LKjell said:**
> Could be that metacity is stupid. Anyway try out xmonad it will do that for you.

That's not a very productive way to go about things. Regardless, Nautilus handles the managing of icons on the desktop, not the window manager.

---

### Post by LKjell on 2010-02-11
Obs I better read carefully. Xmonad is a tiling windows manager. So it will arrange the windows not the icon files on the Desktop.

---

### Post by emarkay on 2010-02-11
Something better that "Clean up by Name" I presume?

---

### Post by 23meg on 2010-02-11
Moved to Community Cafe.

---

### Post by ElSlunko on 2010-02-11
Clean up by name and Keep Aligned should work as long as you don't exceed the max number of icons on your desktop.

---

### Post by aviramof on 2010-02-12
i don't have any icons on my desktop but say i download some files after they all finished downloading
i need to clean by name because they are one on top of the other and then i need to do clean by name
or drag them manuall the option keep align doesn't do nothing about this.

and i can i switch between metacitiy compiz and  Xmonad?

in the past it was in main menu other where is it now?

thanks in advance.

---

### Post by Swagman on 2010-02-12
Downloads should automatically go in the ***"Downloads"*** folder <-- Surprisingly enough.

Not be spattered all over the desktop

---

### Post by ElSlunko on 2010-02-12
> **aviramof said:**
> i don't have any icons on my desktop but say i download some files after they all finished downloading
i need to clean by name because they are one on top of the other and then i need to do clean by name
or drag them manuall the option keep align doesn't do nothing about this.

and i can i switch between metacitiy compiz and  Xmonad?

in the past it was in main menu other where is it now?

thanks in advance.

I might be missing something but do you have "Keep Aligned" checked when you rightclick the desktop?

---

### Post by aviramof on 2010-02-12
yes of course and yet when i download files they immediatly go to the top right corner(i'm using ubuntu in hebrew)and if there is already something there it just go on top of it i also had it in ubuntu 8.10 and i never managed to understand why nobody fixed it till today because it's such an obvious problem but now i'm starting to think that maybe because i use hebrew ubuntu the Keep Aligned option doesn't work.

maybe.

or maybe it's something eles i don't know but the fact is that if i download say five files then those five files will go one on top of the other in the same place at the top right side of the screen and then i have to clean by name to allign them seperetly.

and actually there is another thing about that that i just noticed i have jus int this very second extracted a pdf file from a zip file and he automatilcy allinged him self at the top right of the screen regardless of the fact there is already a link there and not below the last file on the screen and again i had to clean by name to solve this problem.

---

### Post by t0p on 2010-02-12
> **Swagman said:**
> Downloads should automatically go in the ***"Downloads"*** folder <-- Surprisingly enough.

Not be spattered all over the desktop

Downloads will go whereever you choose to have them go.  But ~/Desktop is set as default when using Firefox (and probably other browsers).  You can set this behaviour in firefox at **Edit > Preferences > General**.

If you use the DownloadHelper add-on, downloads will go to the folder ~/dwhelper.  No, I have no idea why it's called dwhelper.

If you use wget, downloaded files will go to your present working directory - unless you tell it to do otherwise, I think by using the -P or --direcory-prefix flags.

Incidentally Swagman: *you* might think it's obvious that downloaded files should go to the "Downloads" folder; but I certainly don't see it as obvious.  You can see the contents of ~/Desktop and click on them etc without needing a file manager window open.  How is it better to have your downloads go to a directory you can't see?

---

### Post by aviramof on 2010-02-12
i personaly always prefer to change it do desktop unless i'm downloading torrents and etc with multple files but single files download should always go the desktop the big problem i have is that in ubuntu this files goes one on top of the other and not one after the other or after the last file who is already presenece there maybe it had something do to because i'm using ubuntu in RTL rather then is LTR but what ever the reason is i think that this problem should be fix as soon as possible.

---

### Post by LowSky on 2010-02-12
This is why I turn off desktop icons for mounted drives, and just use the pael applet to do most of my bidding. I do make firefox downloads go to the deskotp, If I keep them they go into my /home folder, otherwise I install/use and delete.

---

### Post by aviramof on 2010-02-12
and how do i do that?desktop icons for mounted drives?i don't need that after all i can use places button
and pael apple what about that?

and by the way i have installed xmonad because of a previous reply how do i use it?and how do i switch between metacity compiz and xmonad?

in previous version it was possible via applications-other but now there is nothing in others.

thanks in advance.

---

### Post by Simian Man on 2010-02-12
I like the way Thunar does desktop icons better.  They *can't* be in arbitrary locations and have to be on a grid.  It's one less feature than Nautilus, but I hate having disorganized icons, so why have that as an option?

---

### Post by aviramof on 2010-02-12
how do i use Thunar?does he support lucid?

---

### Post by swoll1980 on 2010-02-12
> **aviramof said:**
> and how do i do that?desktop icons for mounted drives?i don't need that after all i can use places button

use ```
gconf-editor
``` it's like apps>nautilus>desktop I think. You will find it. You could also install tweak Ubuntu. It's a nice easy program that helps you configure Ubuntu.

---

### Post by aviramof on 2010-02-12
thank you very much.

in any case i still would like to see a good basic auto arrange option for desktop.

---

### Post by blur xc on 2010-02-12
> **t0p said:**
> Incidentally Swagman: *you* might think it's obvious that downloaded files should go to the "Downloads" folder; but I certainly don't see it as obvious.  You can see the contents of ~/Desktop and click on them etc without needing a file manager window open.  How is it better to have your downloads go to a directory you can't see?

You do realize you can click files from the download dialog in firefox?  When I discovered that, it was like an epiphany moment.  You can also right click it and tell it to open the containing folder...  

I don't like a littered desktop- much rather have a littered downloads folder.

BM

---

### Post by squilookle on 2010-02-12
I'm not running Ubuntu on the desktop, but I am running GNOME 2.28.2, and Clean Up By Name seems to do the trick. 

I know I'm not the first to say that, so I imagine Ubuntu has not removed this from GNOME... (that and the fact it would be pointless to remove it...)

---

### Post by aviramof on 2010-02-12
i don't understand there was a time thet there was auto arrange in gnome?

i'v read that kde has that option but becuase i'm using lucid 10.04 and kde is 9.10 it didn't worked so well i'v 

tried and who know how much damage did it do when i uninstalled it and what it left behind.

---

