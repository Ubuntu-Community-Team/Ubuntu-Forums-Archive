---
title: "Sudo'd instead of gksudo"
date: 2009-08-06
forum: Ubuntuzilla
---

### Post by jfg69 on 2009-08-06
And apparently I've screwed my permissions.. after un-installing through ubuntuzilla I cant re-install it again, I get an error.

What exactly needs to get switched back?

I tried deleting the places.sqlite and restarting but that didn't fix permissions..

```
Backing up old Firefox preferences

Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1225, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 283, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 310, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 675, in install
    self.backupProfile()
  File "/usr/local/bin/ubuntuzilla.py", line 836, in backupProfile
    self.checkDiskSpaceForBackup("~/.mozilla")
  File "/usr/local/bin/ubuntuzilla.py", line 458, in checkDiskSpaceForBackup
    requiredForBackup = int(self.util.getSystemOutput(executionstring="du -sk "+target+" |awk '{print $1}'"))
ValueError: invalid literal for int() with base 10: "du: cannot read directory `/home/jerry/.mozilla/firefox/y41iapo5.default/ScrapBook/data/20090806104119': Permission denied"

```

---

### Post by nanotube on 2009-08-06
hi,
you need to change the ownership of all files in your profile dir to yourself. run this command:

```
sudo chown -R jerry:jerry ~/.mozilla
```

that should fix you right up. :)

---

### Post by jfg69 on 2009-08-10
Sorry for late reply.. worked like a charm, TY


> **nanotube said:**
> hi,
you need to change the ownership of all files in your profile dir to yourself. run this command:

```
sudo chown -R jerry:jerry ~/.mozilla
```

that should fix you right up. :)

---

### Post by nanotube on 2009-08-10
no prob. :)
this is such a common problem, that i have posted an item in the FAQ about it now. :)

---

