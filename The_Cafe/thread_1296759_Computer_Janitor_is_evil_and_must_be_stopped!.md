---
title: "|Computer Janitor is evil and must be stopped!"
date: 2009-10-21
forum: The Cafe
---

### Post by t0p on 2009-10-21
Okay, so I was surfing my System menus in Jaunty, and I thought "Oh, Computer Janitor!  I never used that before!"  So I clicked on it and typed in my password, thus giving the power to do whatever it could trick me into asking it to do.  Bad Janitor!

It said it wanted to help keep my system "clean", and put up a list of possible cruft.  This list consisted of:

```
adobe-certs (.deb package)
eeepc-tray (.deb package)
get_iplayer (.deb package)
nxclient (.deb package)
truecrypt (.deb package)
```

Please note that this is all stuff I installed myself by downloading .deb files.  Also note the words (.deb package) that appears after each name.

I thought, "Ah, these are the .debs that I downloaded.  I don't need them anymore, now the stuff's installed.  They can go."  And I clicked "Cleanup" (Computer Janitor had helpfully ticked "Remove/clean" for each item).

Those package names disappeared from the list.  And were replaced by more.  Packages with more obscure names, like "ldv32 (.deb package)" and "libid3-3.8.3c2a (.deb package)".  I started to feel uneasy.  Were these dependencies of the applications whose ".deb packages" I had just "cleaned up"?  I closed Computer Janitor and, with trepidation, opened my Applications menu.  And guess what?  You got it.  Truecrypt and NXClient had gone!  A quick "which get_iplayer" revealed that get_iplayer had also gone.  Not the ".deb packages" - or at least, not what *I* recognize as ".deb packages".  The applications themselves!

Why oh why does Computer Janitor operate in this way?  If the list had labelled the items (Applications) rather than (.deb packages) I would never have done this ridiculous thing.  As it is, I now have to go scooting around the web re-downloading all this stuff that I actually need.

Computer Janitor is obviously a more newbie-oriented tool.  Old hands don't need it.  And it presents itself extremely poorly.  I hate the janitor and I want to sack him!

---

### Post by NoaHall on 2009-10-21
+1

I hate it so much, that I've hidden it from my menu to prevent madness overcoming me.

---

### Post by hoppipolla on 2009-10-21
lol! I'm sure it will improve - this kind of tool is useful for noooobies but maybe it needs some refining! hehe :)

---

### Post by 3rdalbum on 2009-10-21
Computer Janitor is useful in the correct hands; it does actually suggest configuration changes that will improve performance although most people don't see that side of it because Ubuntu is configured correctly by default.

I'm beginning to think that it shouldn't remove Debian packages at all, unless they have been explicitly listed by Canonical as problematic or obsolete. Not just "locally-installed".

---

### Post by hoppipolla on 2009-10-21
> **3rdalbum said:**
> Computer Janitor is useful in the correct hands; it does actually suggest configuration changes that will improve performance although most people don't see that side of it because Ubuntu is configured correctly by default.

I'm beginning to think that it shouldn't remove Debian packages at all, unless they have been explicitly listed by Canonical as problematic or obsolete. Not just "locally-installed".

Couldn't it just do an apt-get autoremove, and offer to remove any applications which haven't been used in say... a month or so?

---

### Post by Paqman on 2009-10-21
Hmm, mostly a PEBKAC issue, with perhaps a smidgen of a genuine usability gripe ;) It probably shouldn't offer to remove locally installed stuff by default.

---

### Post by wilee-nilee on 2009-10-21
Auto-remove and auto-clean will do most of the work, but Ubuntu Tweak has a nice cleaner that has never failed me, and doesn't remove important installs.

---

### Post by Tmi on 2009-10-21
I was close to doing the same think a week or so ago. In the last second the thought occured to me that I think I've manually removed the .deb and that it might mean that it will remove the whole application instead. Thus I didn't click, luckily enough.

---

### Post by Tristam Green on 2009-10-21
It did what it said it would - clear your hdd of stuff it deems you don't need.

...and you people say that Microsoft has a stranglehold on how you use your computers.

---

### Post by joey-elijah on 2009-10-21
> **wilee-nilee said:**
> Auto-remove and auto-clean will do most of the work, but Ubuntu Tweak has a nice cleaner that has never failed me, and doesn't remove important installs.

QFT.

I look at Computer Janitor.. and look at UT package cleaner and i know which one wins.

(It's the one that actually cleans.)

---

### Post by t0p on 2009-10-21
> **hoppipolla said:**
> Couldn't it just do an apt-get autoremove, and offer to remove any applications which haven't been used in say... a month or so?

That seems a better idea.

> **Paqman said:**
> Hmm, mostly a PEBKAC issue, with perhaps a smidgen of a genuine usability gripe ;) 

  Of course it's a PEBKAC issue.  The stupid program asked me if I wanted it to remove the stuff, and stupid me said yes.  Mea culpa.

But I believe the use of the expression ".deb package" is unclear.  To me, ".deb package" suggests the .deb archive I downloaded in order to install an application.  The term "application" would be a better one to use to describe an application. And Tmi's post indicates I am not utterly alone in this belief.

But yes, the fault is ultimately mine.  If I hadn't told the janitor to do the deed, the deed would have remained undone.

Still, the Janitor *is* evil.
> **Paqman said:**
> 
It probably shouldn't offer to remove locally installed stuff by default.

Damn right it shouldn't.  What's the big problem with locally installed programs?  There's a lot of useful stuff that doesn't appear in repositories. Truecrypt and NXClient being 2 rather popular examples!

---

### Post by Paqman on 2009-10-21
> **t0p said:**
> 
But I believe the use of the expression ".deb package" is unclear. To me, ".deb package" suggests the .deb archive I downloaded in order to install an application. The term "application" would be a better one to use to describe an application. And Tmi's post indicates I am not utterly alone in this belief.

Looks like it's been discussed at some length, and the related [bug has been closed]("https://bugs.launchpad.net/ubuntu/+source/computer-janitor/+bug/285746"), although I don't see how the change they've made actually solves the problem.

---

### Post by TenPlus1 on 2009-10-21
Remove COmputer Janitor and use BleachBit instead...  It's MUCH better...

[http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)

---

### Post by FuzzyFeat on 2013-01-09
It is designed for the new user- the very person who is least equiped to use it.

Like giving a loaded pistol to a one year old. DANGEROUS!!

The smiley face it shows when it has "Cleaned" your system should show a demonic grin instead!

---

### Post by nothingspecial on 2013-01-09
Please don't bump old threads to the top.

Closed.

---

