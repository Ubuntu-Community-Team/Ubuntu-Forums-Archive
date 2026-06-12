---
title: "Force removal of programs in Wine"
date: 2009-11-06
forum: Wine
---

### Post by MonsterMaxx on 2009-11-06
Running 9.10 and Wine Beta.

Trying to get iTunes to run (yea, right, give up on that crap.)

But now Wine is all crapped up with Apple software and none of it will uninstall the normal way.

Is there a way I can just purge out all of the Wine configuration and start over?  From a 'Windows Registry' perspective that's probably easiest.

There's nothing in Wine now that's been successful so purging and starting over won't hurt a bit.

I did try uninstalling Wine and reinstalling.  The process went fine, but all the old Apple programs came back.

Thanks in advance.

---

### Post by arubislander on 2009-11-06
I've always had the same problem in wine. Anything I install never uninstalls cleanly (mostly not at all)

If you want to start with a clean slate in wine (that is as if running it for the very first time) you can go to your home directory on the command line and type
```
rm -R .wine
```
This will delete your .wine drives, all installed programs under wine and your wine settings. So use with caution and double check your typing.

---

### Post by MonsterMaxx on 2009-11-06
I assume I should remove wine first, then do that command, then reinstall wine?

---

### Post by Jguy on 2009-11-06
That command is the equivilent of uninstalling all your programs and deleting any registry value not created for Windows in your registry. the next time you run wine, it will recreate for you a new config file and the appropriate file structure for wine. /.wine/dosdevices/c:, /.wine/drive_c, etc.

---

### Post by MonsterMaxx on 2009-11-07
thank you

---

### Post by arubislander on 2009-11-07
You are most welcome. Maybe you could mark this thread as solved? (Check under Thread Tools)

---

