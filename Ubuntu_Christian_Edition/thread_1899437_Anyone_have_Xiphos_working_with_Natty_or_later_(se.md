---
title: "Anyone have Xiphos working with Natty or later? (segfaults here)"
date: 2011-12-23
forum: Ubuntu Christian Edition
---

### Post by Ibidem on 2011-12-23
I recently upgraded from Maverick to Precise (I want everything working at release, so I test beforehand).
Xiphos did not recognize modules installed in /usr/share/sword, but that was a minor issue:
After I installed modules, it segfaulted as soon as it attempted to show the main window.
I checked Launchpad, and found that there had been no updates since Natty, and this bug was first reported then.
Bug report: [https://bugs.launchpad.net/ubuntu/+source/xiphos/+bug/783019](https://bugs.launchpad.net/ubuntu/+source/xiphos/+bug/783019)
Does anyone have Xiphos working in Natty (11.04) or later?  I'd like to know if it's universal or if a solution exists.

---

### Post by stlsaint on 2011-12-23
Xiphos has not been developed since its last release of October 2010 according to its site. I have a strong feeling that this may be the cause of your issue and the last UCE tested with it stable was 9.10 karmic. This brings us to our current state of needing a update UCE. Works have already began to bring a updated version to our community. Stay tuned for further news! ;)

---

### Post by Ibidem on 2011-12-24
From what I saw in the SVN repo, the last code change was this summer.  There was a translation update this fall.

What (native) bible study programs are known to work from Natty on?  I don't want Wine + E-sword, just native Linux ones.
I currently know that Cheatah/XSword and diatheke work.

---

### Post by warroomcbw on 2011-12-29
> **Ibidem said:**
> From what I saw in the SVN repo, the last code change was this summer.  There was a translation update this fall.

What (native) bible study programs are known to work from Natty on?  I don't want Wine + E-sword, just native Linux ones.
I currently know that Cheatah/XSword and diatheke work.

Xiphos and bibletime work super for me ubuntu 11.10 and fedora 16

---

### Post by trulan on 2011-12-30
Xiphos works well here on Oneiric, was also working on Natty before I upgraded.  Now, I have mostly migrated my desktop to Lubuntu, so I'm not using Unity.  I don't know if that could make a difference or not.  But it did work with Unity in Natty before I upgraded.  I've been intending to set up a testing install of Precise but I haven't gotten around to it yet.

---

### Post by hangtuff on 2012-01-06
Hello, Xiphos and Bibletime works just fine in 11.10. But there is another bible program that works just as good and it is Bibleanalyzer it was done for windows and than was done for linux. Check it out and enjoy.:)

---

### Post by Ibidem on 2012-01-20
I'm using IceWM, so it's not Unity...
So something started causing segfaults in Precise, rather than the last change having never worked.

---

### Post by Ibidem on 2012-02-11
FYI, it looks like a bit of work has been done just recently.
Also, someone else reported a bug in the display under "12.04" (I'm assuming Ubuntu, though I may be wrong..), and it looks like a fix was committed
This would mean that there is a chance of getting it working.


Second--I just rebuilt Sword 1.6.1, and it makes Xiphos work.
TODO: Upload this to my PPA

---

### Post by Ibidem on 2012-02-11
[https://launchpad.net/~ibid-ag/+archive/oldgtk1/?field.series_filter=precise](https://launchpad.net/~ibid-ag/+archive/oldgtk1/?field.series_filter=precise)

Done.

But I guess this means that sword 1.6.2  is not binary compatible with 1.6.1 (as shipped by Debian/Ubuntu)

---

### Post by Kyrio on 2012-02-12
I also tried Xiphos and Bibletime today and they crashed on my system (Debian). However the newer version of Bibletime available in the Crosswire repository seems to work fine: [https://launchpad.net/~pkgcrosswire/+archive/ppa](https://launchpad.net/~pkgcrosswire/+archive/ppa)

---

### Post by Ibidem on 2012-03-28
> **Kyrio said:**
> I also tried Xiphos and Bibletime today and they crashed on my system (Debian). However the newer version of Bibletime available in the Crosswire repository seems to work fine: [https://launchpad.net/~pkgcrosswire/+archive/ppa]("https://launchpad.net/%7Epkgcrosswire/+archive/ppa")
See [https://bugs.launchpad.net/ubuntu/+source/sword/+bug/935574](https://bugs.launchpad.net/ubuntu/+source/sword/+bug/935574)
Libsword 1.6.2 broke the ABI but was marked as not doing so, so the main SWORD frontends are currently broken.
They'll need to rebuild the packages to get them working.

---

### Post by Anastasis on 2012-03-28
I'm currently running a hacked up Frankenstein version of Debian Wheezy (sid) with Gnome 3 and Xiphos and BibleTime are both working fine.

Haven't tried on Ubuntu because I haven't run Ubuntu in about 6 months.

---

### Post by fredbird67 on 2012-04-03
I'm running Xiphos on Xubuntu Oneiric and not having any problems.

---

### Post by stlsaint on 2012-04-04
Currently running on Ubuntu 11.10 just fine:

quelea
bibledit
bible memorizer
xiphos 
bible time
lyricue
Wine 1.3

---

### Post by krash182 on 2012-04-07
I have not been able to get Xiphos or Bibletime to work on 12.04 myself.  All I get are the flash screens and then the dreaded crash.  I file the error report but when I get the reply it shows it is a repeat of a bug.  When I search the old bug it does not exist in the system.  May have to do the Wine/Sword route, but I don't want to do that either.

---

### Post by lisati on 2012-04-10
Works OK on 11.04 here.
> **Anastasis said:**
> That's not the only thing that doesn't work on 12.04.
 
You do realise that 12.04 isn't officially released yet?

---

### Post by RememberWhenItRained on 2012-05-02
seems to be working for me in Precise KDE & Unity. Not tested on Gnome.

---

### Post by Irihapeti on 2012-05-02
Works in Gnome-fallback in 12.04

---

### Post by Ibidem on 2012-05-08
Should be solved now.

For all those who are wondering why anyone was talking about Precise (12.04) before release, some of those here (myself included) were alpha or beta testing it, so any bugs would be solved before release.
To summarise, SWORD 1.6.2 (available with Precise) was not binary-compatible with SWORD 1.6.1; the SWORD maintainers thought it was.
Xiphos and other packages were compiled against 1.6.1 before the update to 1.6.2, and were not rebuilt (since it was thought that 1.6.2 used the same ABI).
This broke everything except Diatheke (which built with SWORD) and some applications that used a small subset of the API (an Xsword/Cheatah binary I built previously being the main one).
Xiphos and the SWORD packaging have both been updated, resolving the issue.

I'd seen that there were crashes for some reason on Natty; hence I asked whether that was an unsolved bug.

---

