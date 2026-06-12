---
title: "ubuntuzilla fails to update to firefox 3.5.6"
date: 2009-12-27
forum: Ubuntuzilla
---

### Post by ronewolf on 2009-12-27
tried a manual run of ubuntuzilla to upgrade from from firefox 3.5.3 to the current latest version 3.5.6. seems to be two problems (see attached terminal log). first is that while i'm running firefox 3.5.3 and even tho 3.5.6 is detected as the latest version:

[INDENT]The most recent release of Firefox is detected to be 3.5.6.[/INDENT]

ubuntuzilla concludes:

[INDENT]firefox is already the newest version.[/INDENT]

still things seem to move forward and then there is some sort of permissions problem (i guess??)

[INDENT]Backing up old Firefox preferences

cp: cannot open `/home/rone/.mozilla/eclipse/cookies.txt' for reading: Permission denied[/INDENT]

and, btw, the i have the ubuntuzilla firefox updater installed but it hasn't been informing me of updates.... maybe related?

just in case it adds some insight, Ubunutuzilla upgraded Thunderbird without any problem.

---

### Post by nanotube on 2009-12-28
you have some files in ~/.mozilla that are apparently owned by root and not world-readable, which makes the profile backup fail.

you have two choices: 

skip the backup process by adding the '-b' option to your ubuntuzilla run

or, fix the permissions in your profile, by running:
```
sudo chown -R rone:rone ~/.mozilla
```

either of those should fix you up and let you carry out the upgrade.

---

### Post by ronewolf on 2009-12-28
thanks! the chown did the trick and ubutuzilla installed 3.5.6 with no add'l issues. appreciate the hand holding on this!

---

### Post by nanotube on 2009-12-28
> **ronewolf said:**
> thanks! the chown did the trick and ubutuzilla installed 3.5.6 with no add'l issues. appreciate the hand holding on this!

great :)

---

