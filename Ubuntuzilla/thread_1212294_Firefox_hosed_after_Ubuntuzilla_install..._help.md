---
title: "Firefox hosed after Ubuntuzilla install... help?"
date: 2009-07-13
forum: Ubuntuzilla
---

### Post by JPorter on 2009-07-13
Install went without a hitch.

On launching Firefox, I get a bright red bar across the top with this:
> **The bookmarks and history system will not be functional because on of Firefox's files is in use by another application. Some security software can cause this problem.**

This persists after reboot.


When I run the original system FF 3.0 manually, it doesn't even give me the error... but has nothing in the bookmarks toolbar and it doesn't appear to be loading any profile at all.


I've tried to restore previous bookmark backups that I have and it errors out.


Any ideas?

---

### Post by nanotube on 2009-07-13
Hi,
not sure why that could be happening - maybe you didn't exit firefox before installing with ubuntuzilla?

at any rate, ubuntuzilla makes a complete backup of your profile - in your home dir, you should find a directory called ".mozilla_backup_**" where ** stands for the date of backup.

you could always go back to the previous state with the following steps: (1), use ubuntuzilla to uninstall the mozilla build, (2), restore the backup profile. 

of course, make sure to exit firefox before you do anything. 

alternatively, try starting with a fresh profile (exit firefox and rename your .mozilla/firefox directory), start ff3.5 again, then manually import bookmarks from your profile backup (in ff3.5, click bookmarks -> organize bookmarks -> import and backup -> restore, and browse to the file you want to restore.

---

### Post by JPorter on 2009-07-14
Weird, it seems as though it hosed my profile somehow.  Firefox was definitely not running when I installed originally.

I changed the name of the .mozilla/firefox directory, which caused a new profile to be generated on next run, then imported my bookmarks manually from the old one.  Works fine now.  Very odd.

---

### Post by Df8 on 2009-07-17
I just now had the same problem.

I solved it (in the original profile) by
[INDENT][LIST]
[*]shutting down firefox
[*]renaming places.sqlite to places_.sqlite
[*]starting firefox (it will create a new empty places.sqlite and do something else)
[*]shutting down firefox again
[*]deleting places.sqlite
[*]renaming places_.sqlite to places.sqlite
[*]starting firefox
[/LIST][/INDENT]

After this I got al my bookmarks and full history back .

Df

---

