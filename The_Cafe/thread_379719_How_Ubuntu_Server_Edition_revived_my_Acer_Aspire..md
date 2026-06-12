---
title: "How Ubuntu Server Edition revived my Acer Aspire."
date: 2007-03-08
forum: The Cafe
---

### Post by phibxr on 2007-03-08
Recently, I got my hands on an Acer Aspire 1362LC for free - with one hook, of course, namely the CD-drive was all messed up and could only read the first few sectors on a disc, and reading DVDs was out of the question.

I first tried to install Ubuntu the regular way, with the graphical Live CD, but at 47% the installation stopped and the whole system froze.

"Well then," I thought, and burned out the alternative text based installer. It got to just around the same place when it stopped and started complaining about unreadable sectors on the disc.

"To hell with this," I figured and popped in the most minimal installation CD that Ubuntu has to offer - the server version.

It installed perfectly in a few minutes, and after 'apt-get xubuntu-desktop epiphany-browser <the name of the driver of my video card> vlc' the once stone cold dead laptop was brought back to life again.

Sure, I could have bought an external CD/DVD-drive, but I don't have a clue if I would be able to boot from it, but this solution has given me a free laptop, so cheers! *raises a cup of steamingly hot ubuntu branded coffee* =D>

---

### Post by maniacmusician on 2007-03-08
the server version has its own CD?

---

### Post by az on 2007-03-08
> **phibxr said:**
> 

"To hell with this," I figured and popped in the most minimal installation CD that Ubuntu has to offer - the server version.

It installed perfectly in a few minutes, and after 'apt-get xubuntu-desktop epiphany-browser <the name of the driver of my video card> vlc' the once stone cold dead laptop was brought back to life again.

Be sure to install the desktop kernel.  The server kernel may not play well with desktop doodads.

sudo apt-get install linux-generic

---

### Post by BarfBag on 2007-03-08
Give more details on the specs.  I wanna hear more.  :popcorn:

---

### Post by Yfrwlf on 2007-03-08
> **phibxr said:**
> Recently, I got my hands on an Acer Aspire 1362LC for free - with one hook, of course, namely the CD-drive was all messed up and could only read the first few sectors on a disc, and reading DVDs was out of the question.

I first tried to install Ubuntu the regular way, with the graphical Live CD, but at 47% the installation stopped and the whole system froze.

"Well then," I thought, and burned out the alternative text based installer. It got to just around the same place when it stopped and started complaining about unreadable sectors on the disc.

"To hell with this," I figured and popped in the most minimal installation CD that Ubuntu has to offer - the server version.

It installed perfectly in a few minutes...

I've seen this happen several times on both desktops and laptops, but mostly older laptops.  In your case it sounds like the drive really *was* bad, but it's very strange.  They will tell me "but the Windows XP install CD works" so then I think OK, it's probably it not reading burned CDs very well then, and still is the drive that is bad.  However, it seems like some laptops have a problem with *live* CDs.  Normal install-only CDs seem to work fine, but if you try a live CD they get really weird random errors.  It's almost like there isn't enough RAM for the live environment (even though I'm pretty sure they are supposed to, and are able to, cope with that), or there is some hardware incompatibility with the way live CDs work.  Anyone else have a similar experience with this?  The server CD is still 500 megs, even if it doesn't install everything on it, but you'd think you would still get errors while trying to install if it really was a bad CD-Rom drive.  Maybe it's something else that's the problem?

---

### Post by zachtib on 2007-03-08
> **phibxr said:**
> Recently, I got my hands on an Acer Aspire 1362LC for free - with one hook, of course, namely the CD-drive was all messed up and could only read the first few sectors on a disc, and reading DVDs was out of the question.

I first tried to install Ubuntu the regular way, with the graphical Live CD, but at 47% the installation stopped and the whole system froze.

"Well then," I thought, and burned out the alternative text based installer. It got to just around the same place when it stopped and started complaining about unreadable sectors on the disc.

"To hell with this," I figured and popped in the most minimal installation CD that Ubuntu has to offer - the server version.

It installed perfectly in a few minutes, and after 'apt-get xubuntu-desktop epiphany-browser <the name of the driver of my video card> vlc' the once stone cold dead laptop was brought back to life again.

Sure, I could have bought an external CD/DVD-drive, but I don't have a clue if I would be able to boot from it, but this solution has given me a free laptop, so cheers! *raises a cup of steamingly hot ubuntu branded coffee* =D>

you're using epiphany in XFCE? doesn't that need a lot of gnome-libs?

---

### Post by Quillz on 2007-03-08
> **phibxr said:**
> Recently, I got my hands on an Acer Aspire 1362LC for free - with one hook, of course, namely the CD-drive was all messed up and could only read the first few sectors on a disc, and reading DVDs was out of the question.

I first tried to install Ubuntu the regular way, with the graphical Live CD, but at 47% the installation stopped and the whole system froze.

"Well then," I thought, and burned out the alternative text based installer. It got to just around the same place when it stopped and started complaining about unreadable sectors on the disc.

"To hell with this," I figured and popped in the most minimal installation CD that Ubuntu has to offer - the server version.

It installed perfectly in a few minutes, and after 'apt-get xubuntu-desktop epiphany-browser <the name of the driver of my video card> vlc' the once stone cold dead laptop was brought back to life again.

Sure, I could have bought an external CD/DVD-drive, but I don't have a clue if I would be able to boot from it, but this solution has given me a free laptop, so cheers! *raises a cup of steamingly hot ubuntu branded coffee* =D>
Good story, but the CD/DVD reader is still messed up, isn't it?

---

### Post by H.E. Pennypacker on 2007-03-08
Why not just replace the internet CD/DVD drive instead of buying an external one?  Since you got the laptop for cheap, a new/used CD/DVD drive isn't going to be a financial PITA.

---

