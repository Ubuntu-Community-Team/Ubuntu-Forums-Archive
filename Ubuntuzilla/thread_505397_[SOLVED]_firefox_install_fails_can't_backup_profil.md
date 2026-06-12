---
title: "[SOLVED] firefox install fails: can't backup profile"
date: 2007-07-20
forum: Ubuntuzilla
---

### Post by tivolives on 2007-07-20
I'm running Ubuntu 6.06 LTS, and the versions of Thunderbird and Firefox are the
ones that came with it. I want to update to the 2.x versions.

I have succesfully updated Thunderbird using ubuntuzilla/py, but when I attempt to
update firefox, I get the following error. I tried removing the Cashe directory to no
effect.

<error>
Backing up old Firefox preferences

cp: reading `/home/lou/.mozilla/firefox/ogh6smdx.default/Cache/_CACHE_001_': Input/output error
cp: reading `/home/lou/.mozilla/firefox/ogh6smdx.default/Cache/_CACHE_002_': Input/output error
cp -R ~/.mozilla ~/.mozilla_backup_$(date -Iseconds)
Failed to back up profile.
Error code: 256
Traceback (most recent call last):
  File "/home/lou/ubuntuzilla.py", line 757, in ?
    bs.start()
  File "/home/lou/ubuntuzilla.py", line 74, in start
    fi.start()
  File "/home/lou/ubuntuzilla.py", line 97, in start
    self.install()
  File "/home/lou/ubuntuzilla.py", line 344, in install
    self.backupProfile()
  File "/home/lou/ubuntuzilla.py", line 491, in backupProfile
    self.execSystemCommand(executionstring="cp -R ~/.mozilla ~/.mozilla_backup_$(date -Iseconds)", errormessage="Failed to back up profile.")
  File "/home/lou/ubuntuzilla.py", line 474, in execSystemCommand
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla)
</error>

---

### Post by nanotube on 2007-07-23
well, it seems that there's something wrong with some files in your cache directory.
since cache doesn't store anything of long-term usefulness, it's not worth it to try to figure out exactly what's wrong - you can just delete everything in that directory, and then see if it backs up for you.

---

