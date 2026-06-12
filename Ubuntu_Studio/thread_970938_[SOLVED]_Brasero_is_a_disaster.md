---
title: "[SOLVED] Brasero is a disaster"
date: 2008-11-04
forum: Ubuntu Studio
---

### Post by ingeva on 2008-11-04
When making audio CDs with Brasero under 8.04 about 50% of the CD players could not play the CDs. I don't know how many blank CDs I wasted trying.

Brasero under 8.10 can't make audio CDs at all. It complains that a new, blank CD is already full. After the first attempt the CD is reported to be written, with 0MB in it.

I puchased a new DVD burner even if the one I had was brand new, hoping that it would solve the problem. It did not. I upgraded to 8.10, hoping that it would help. Most things do work better than before, but CD burning does not.

Do I REALLY need to install Windows again to make this work? I make recordings and need to burn CDs for distribution. This is terribly frustrating!

Actually I tried to install Windows on this computer several times, but failed. I need to keep the old computer to run Windows, and I had planned to send it to recirculation.

Any ideas? Is there a CD burner program for Linux that actually works?

inge

---

### Post by paulmerchant on 2008-11-04
I use Brasero for data CDs. For Audio CDs, I've been using Serpentine Audio CD Creator. Just sudo apt-get install serpentine.

---

### Post by VanCardboardbox on 2008-11-04
I, too, had difficulties with Brasero in 8.04. It rendered two brand new DVD-RW discs unwritable, turned several DVD+R's into coasters and does not deal with dual layer DVDs at all. I switched to K3B which has been working great. Its a KDE app, but like most KDE apps will work just fine under Gnome. It can be found in the Ubuntu repositories.

---

### Post by soldar79 on 2008-11-04
I've been using K3B since 6.06. It's almost perfect, by far the best cd-burning app for gnu/linux. Go and get it. It's in the repositories.

---

### Post by partsdale on 2008-11-04
> **paulmerchant said:**
> I use Brasero for data CDs. For Audio CDs, I've been using Serpentine Audio CD Creator. Just sudo apt-get install serpentine.
+1

I've never had any problems with Serpentine.

---

### Post by quantum8 on 2008-11-04
I never had any issues with brasero under 8.04, but 8.10 complains about an audio cd being full, even after removing any tracks that make the cd run over 80 mins. A work around I've found is to start a new project :mad:

Also, I've noticed CD Text has stopped working :mad:

---

### Post by bangeko on 2008-11-04
I've never had any problem with Brasero since 7.10

---

### Post by babarosa on 2008-11-05
Hello Ingeva,

I know what you mean, I faced the same problems. It seems that brasero is very hardware-dependent.

At [www.getdeb.net](www.getdeb.net) you can download "gnomebaker"'s newest version. It works much better than brasero on my system.

Keep burning!
Michael

---

### Post by ingeva on 2008-11-05
> **paulmerchant said:**
> I use Brasero for data CDs. For Audio CDs, I've been using Serpentine Audio CD Creator. Just sudo apt-get install serpentine.

Thanks, I'll try that. I just installed it.
...
I burned 4 WAV files. The CD player finds nothing at all.

Totem player was unable to find a suitable codec (Audio CD source), but Rhythmbox player could find and play them.

These CDs must be playable in old and new CD players. Mine is quite old, so it's an excellent test medium.

My CD/DVD burner is brand new with SATA interface. There is no IDE interface in my computer, so I can't use an older model.
If the programs hare hardware dependent, it might indicate that there's a HAL problem, or a violation of hardware abstraction programming rules.

---

### Post by ingeva on 2008-11-05
> **VanCardboardbox said:**
> I, too, had difficulties with Brasero in 8.04. It rendered two brand new DVD-RW discs unwritable, turned several DVD+R's into coasters and does not deal with dual layer DVDs at all. I switched to K3B which has been working great. Its a KDE app, but like most KDE apps will work just fine under Gnome. It can be found in the Ubuntu repositories.

Thanks!

I tried K3B before but it wouldn't work any better.
I now tried K3B and Gnomebaker. Both work fine and produce playable CDs, but I like K3B better. A more intuitive interface, and it's faster.

Thanks for all help, everyone!

---

### Post by fjf on 2008-11-05
K3B is a great program.  I do not use it because it does not verufy the burnt DVDs.  The best is nerolinux.

---

### Post by rad_sci_guy on 2008-11-07
I can't even get brasero to burn an audio cd as it mistakenly thinks the 80 minute disk I put in the tray doesn't have enough disk space to hold 53 minutes of an album I'm trying to burn.

I got gnomebaker to burn the disk for me but no cd text :(

I used to use k3b as it handled all my needs perfectly in hardy, however it has stop working in ibex (along with amarok).  Seems like a no KDE software issue for my clean ibex install.

---

### Post by ingeva on 2008-11-07
> **rad_sci_guy said:**
> I can't even get brasero to burn an audio cd as it mistakenly

Same problem here. It wouldn't even burn 0MB but it closed the disk, making it unusable.

I don't care about texts. All the songs that I record have an audible identification.

K3B works fine for me. I like the simplicity and elegance. Very easy to use.
Verification can be done by playing it in the CD player! :)

---

### Post by TenPlus1 on 2008-11-07
I use Basero 0.8.2 from [www.getdeb.net](www.getdeb.net) and everything burns perfectly...

Remember to use good media for your writer as cheap disc's have a habit of going bad on other players...

---

### Post by ingeva on 2008-11-07
> **TenPlus1 said:**
> I use Basero 0.8.2 from [www.getdeb.net]("http://www.getdeb.net") and everything burns perfectly...

Remember to use good media for your writer as cheap disc's have a habit of going bad on other players...

Version 0.8.2 was the version I used. I can see no reason to continue experimenting since I have found two programs that actually work.

Brasero was bad in 8.04, and worse in 8.10. The media or the burner has nothing to do with it since I have tried different burners on different computers. It has cost me lots of time and money (for a new burner), and one day it's enough.

I'll mark this thread as solved even if the problem with Brasero is not.

inge

---

### Post by cor2y on 2008-11-07
Personally i use brasero for data discs only.
Haven't tried a 1 to 1 copy of audio cds or image files (iso) or creating a video dvd or audio cds out of mp3s with it.
Just don't trust it enough for that.
If the time ever comes for any of those things i prefer the use of k3b which hasn't failed me in any of those tasks.
Since i have been using 8.10 haven't installed k3b yet.

---

