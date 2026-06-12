---
title: "Foxit Reader installation"
date: 2010-01-13
forum: Wine
---

### Post by Corvidious on 2010-01-13
Hi there,

I had an odd problem trying to install Foxit Reader 3.1 under Wine (1.0.1, under Ubuntu 9.10). Different ways of installing under Wine (including from the shell) did not run the install routine but actually started the main program!

On the other hand, I tried just moving the files from the Program Files directory on a Windows machine to a directory under .wine, and Foxit seems to run just fine from there, although I can understand why that wouldn't be recommended. Can you think of any gotchas or other things I should try?

I'm trying this because native PDF readers for Linux (including the current version of the Foxit Reader) don't have the commenting and markup features I need, as far as I know. The Adobe Reader has other problems that make it less than useful.

---

### Post by gitmo333 on 2010-01-30
I used to launch the .exe file for foxit using wine directly under ubuntu 8.10 but I am currently having trouble getting it to work on Karmic. The pointer indicates 'busy' for a bit but nothing happens. 
My system is Ubuntu 9.10 for amd, running on a 64-bit processor, if that helps.

---

### Post by beastrace91 on 2010-01-30
Wine tip: Always start with the [AppDB Entry](http://appdb.winehq.org/objectManager.php?sClass=version&iId=16286) for the program you are trying to get working.

That being said - try upgrading your Wine version to a new beta version (instead of the 1.0.1 "stable"), the results other people have posted show good news with newer Wine versions.

Regards,
~Jeff

---

### Post by inxonic on 2011-01-05
had the same issue and found a solution. i'm posting it here since i didn't find a solution on the net.

just install foxit reader version 2.0 (needed to run "winetricks vcrun6" before)

you can then upgrade to the latest foxit reader by selecting "check for updates now".

---

### Post by jac_tict on 2011-03-28
Good suggestion!
Installing foxit reader version 2.0 and updating is the best solution (installing directly v4 doesn't create the menu shortcut).

Thanks

---

### Post by mips on 2011-03-28
What's wrong with the native linux version?

[Foxit Reader for desktop Linux]("http://www.foxitsoftware.com/pdf/desklinux/index.html")

---

### Post by r_avital on 2012-07-31
> **mips said:**
> What's wrong with the native linux version?

[Foxit Reader for desktop Linux]("http://www.foxitsoftware.com/pdf/desklinux/index.html")


Nothing "wrong" with it, it just does not annotate.

---

