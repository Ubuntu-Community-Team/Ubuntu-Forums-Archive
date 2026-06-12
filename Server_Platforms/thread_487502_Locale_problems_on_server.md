---
title: "Locale problems on server"
date: 2007-06-29
forum: Server Platforms
---

### Post by mholst on 2007-06-29
Hi all,

I have had a problem with my server for quite some time now, and I can't solve it myself. I have no clue to what causes the problem.

I come from denmark and therefore want the support æ,ø,å in filenames and such. However I use english for applications and Ubuntu overall. Locale is en_DK:en ISO-8859-1. I think I finally changed it all the places I can imagine, and the locales look right.

Scenario:
If I make a new file on the desktop and save it as Hæst.txt, it looks ok in the GUI of Ubuntu, but not in the terminal.
test af æøå becomes test af Ã¦Ã¸Ã¥.txt

If I save a file from an SSH connection to the desktop it look allright, but editing it makes all the special characters look like crap again. 

I have tried dpkg-reconfigure localeconf, and set the locale to en_DK ISO-8859-1, and rebooted.

What the .... is wrong.
It is this way on both my machines.

Morten Holst

---

