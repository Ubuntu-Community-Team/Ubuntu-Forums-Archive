---
title: "Really bloody annoying firefox bug"
date: 2006-11-24
forum: The Cafe
---

### Post by Beamerboy on 2006-11-24
OK this bug has been annoying me for over 6 months now and I can't find a reference for it anywhere and everyone I talk to has never experienced it.

As you can see from the following screenshot [[Click Here]](http://www.paladine.org.uk/images/firefox-bug.png)

It opens a page in a window called "Untitled Window".  This window has no menus/buttons/url bar.  Also when you try to move or minimise the window it corrupts the display (see bottom of the image).  The only way to fix the problem is to close the window which in turn kills -ALL- firefox processes.

This bug occurs -frequantly- (as many as several times a day for me) and happens randomly when clicking on a link or refreshing a page already open and it is royally pi$$ing me off.

Has anyone else encountered this bug?
Does anyone know how to fix it?
Is this an Ubuntu specific bug?
Should I report this bug to Ubuntu or to Mozilla?

_Version Details_
Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.8.0.7) Gecko/20060921 Ubuntu/dapper-security Firefox/1.5.0.7

_System Details_
Linux main 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686 GNU/Linux

CPU: Athlon 64 3700+ San Diego Core
RAM: 2x 1GB DDR400
Graphics: 2x Nvidia Geforce 6600GT 128MB (SLI Capable)
Motherboard Chipset: NForce 4

I really am sick of this bug.

Paladine

---

### Post by kleeman on 2006-11-24
Is it specific to one user or does it occur on every users account? If the former is true try backing up your bookmarks somewhere using the export command on Bookmarks----> Organize Bookmarks and then do the following using a terminal:

unalias rm
rm -R .mozilla

This will kill all your settings on firefox (and sunbird) products which may be causing the problem.

---

### Post by Beamerboy on 2006-11-24
I only have 1 user setup on the box, but I don;t think it is the problem you are hinting at because this has happened with completely fresh installations of Ubuntu for me.  It happened with AMD64 version of Ubuntu, I then did a fresh install of 32Bit Ubuntu (and didn't bother backing up ~/.mozilla), then when I reinstalled Ubuntu 32bit a couple of months ago (again I didn't bother backing up ~/.mozilla) it has happened again.

This really happens very frequantly (as I said often several times a day) irrespective of whether it is a fresh OS installation or not.

I do a great deal of research and can read literally hundreds of web pages in any single day, sometimes I might have as many as 30 firefox windows open and I hate bookmarking (I am way to disorganised to keep them manageable) so when I close the window after this annoying bug I lose every single page I have open, which then invariably takes a long time to get back to where I was.  however, it doesn't seem to be consistant with having a large number of brwoser windows open.  The bug I caught with the screenshot this evening was when I only had 3 tabs open in firefox, where as an hour prior to that I had closer to 20 and had no problems.  It is just completely random but very frequant.  I am really suprised no-one has come across this before.

Paladine

---

### Post by kleeman on 2006-11-24
Try firefox 2.0 then. Just download the standard mozilla binary and install in your home directory.

---

### Post by Beamerboy on 2006-11-24
That was my next move if I couldn't find a solution to the problem.

Paladine

---

### Post by argie on 2006-11-25
I've never had this problem. Perhaps it's an extension you are using? SessionSaver used to lock up Firefox on start once or twice.

---

### Post by maddog39 on 2006-11-25
I dont understand why you dont just upgrade. FF 2.0 is pretty much better all across the board.

---

### Post by Dale61 on 2007-02-05
The untitled window drama also happens to me, running Firefox 2.0.

I have just the one account set up, but have allocated a work space for myself and another for my gf.  Untitled window happens in both.

When it does occur, I just open another bookmark in another tab, then close the offending tab that caused the untitled window.  However, a bug is still active (I don't know what it is) that eventually requires Firefox to be closed.

This also happened in Firefox 1.5.0.9 (and previous releases) so it's not restricted to a certain release.

I tried the suggested fix, and this is what I got:

xxxx@desktop:~$ unalias rm
bash: unalias: rm: not found
xxxx@desktop:~$ rm -R .mozilla

The untitled window I've learnt to live with, but an answer to why it's happening would be good, and another step in my Ubuntu learning curve.

---

