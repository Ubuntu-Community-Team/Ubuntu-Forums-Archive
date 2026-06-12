---
title: "Stratego: No CD found"
date: 2010-01-30
forum: Wine
---

### Post by mister_playboy on 2010-01-30
I'm stumped on this one.  I have extracted the contents of the CD to /home/misterplayboy/Stratego, and WINE has this folder set as drive X: (CD-ROM).

The game installs just fine, but always says "Please insert the Stratego CD-ROM" when I attempt to launch it.  The game generates a trace.txt file, and that says:

```
Starting STRATEGO at Sat Jan 30 10:30:52 2010



Version 3.09

Total Memory = 2074189824 (2025576K)(1978Mb)

_chdir(C:\Program Files\Hasbro Interactive\Stratego)

Language directory = '0009'

Searching for a volume labelled 'Stratego'

Can't find 'Stratego' drive.

CloseApp(TRUE)

CloseApp done.
```

I have given the label Stratego to Drive X:, but it still doesn't work.  If I browse to /home/misterplayboy/.wine/dosdevices/x:, I can see the CD contents.

What else could be causing this problem?  I'm using Wine 1.1.37.

---

### Post by asdfoo on 2010-03-12
> **mister_playboy said:**
> I'm stumped on this one.  I have extracted the contents of the CD to /home/misterplayboy/Stratego, and WINE has this folder set as drive X: (CD-ROM).

The game installs just fine, but always says "Please insert the Stratego CD-ROM" when I attempt to launch it.  The game generates a trace.txt file, and that says:

```
Starting STRATEGO at Sat Jan 30 10:30:52 2010



Version 3.09

Total Memory = 2074189824 (2025576K)(1978Mb)

_chdir(C:\Program Files\Hasbro Interactive\Stratego)

Language directory = '0009'

Searching for a volume labelled 'Stratego'

Can't find 'Stratego' drive.

CloseApp(TRUE)

CloseApp done.
```

I have given the label Stratego to Drive X:, but it still doesn't work.  If I browse to /home/misterplayboy/.wine/dosdevices/x:, I can see the CD contents.

What else could be causing this problem?  I'm using Wine 1.1.37.


It could be copy protection.

---

### Post by heyniceaddress on 2010-03-31
I have the same paradoxical problem with my Ubuntu 9.10:

I place a CD/DVD into the drive, and run its .exe just fine so that it installs in Wine.

I go to Wine, and run the program: then, it asks me to insert the CD.

It asks me to insert the CD that it just installed from and is reading just fine! I don't understand :)

If someone knows what silly thing I haven't done, please let me know. Thank you!

---

### Post by JimSBjd on 2010-04-16
I got the same problem with Railroad Tycoon II recently.  Installed using PlayOnLinux with wine, from the cd, in the cd drive, and when run, prompts me to insert the CD.

I know this is some sort of copy protection.  (I remember a decade ago when my game was new, and ran on Win 98, that if I tried to play it without the CD inserted, it would give the same prompt).

I know "no-cd" patches exist to circumvent the copy protection.  The problem is a:) I'm not too tech savvy and can't get it to work, and b:) I shouldn't have to because I paid for it, and have the real retail cd in the frickin' drive!

I haven't figured out how to make it work, but I'll keep looking, and if I find an answer, I'll share it here.

---

### Post by cogadh on 2010-04-16
The answer is really simple: Wine does not support all copy protection schemes fully. It doesn't matter that you paid for the product and shouldn't have to use a crack, if Wine doesn't do it and you want to use the game, your only options may be to use a crack or go back to Windows. Eventually, Wine may be able to support copy protection more fully, but until it does, you are really limited in what you can do.

That being said, the WineHQ AppDB entries for both games indicate they are known not to work with Wine already:
Stratego: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=10841](http://appdb.winehq.org/objectManager.php?sClass=application&iId=10841)
Railroad Tycoon 2: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1242](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1242)

---

