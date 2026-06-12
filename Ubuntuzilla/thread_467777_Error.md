---
title: "Error"
date: 2007-06-08
forum: Ubuntuzilla
---

### Post by Brightrock on 2007-06-08
Hi, 

I run a thunderbird profile on a "in-between" fat32 partition and I'm having trouble updating thunderbird with your script.  The firefox update worked great.  Thanks!

Here's the error message I get after I ask it not to backup my profiles.

File "/home/peter/Desktop/ubuntuzilla_4.0.0.py", line 493, in backupProfile
    if os.path.lexists(os.path.expanduser('~/.thunderbird')) and stat.S_ISDIR(os.lstat(os.path.expanduser('~/.thunderbird'))[stat.ST_MODE]) and os.stat.lexists(os.path.expanduser('~/.mozilla-thunderbird')) and stat.S_ISDIR(os.lstat(os.path.expanduser('~/.mozilla-thunderbird'))[stat.ST_MODE]):
AttributeError: 'builtin_function_or_method' object has no attribute 'lexists'


I don't understand this at all.  Does anyone else here?

Thanks,

BR

---

### Post by nanotube on 2007-06-08
> **Brightrock said:**
> Hi, 

I run a thunderbird profile on a "in-between" fat32 partition and I'm having trouble updating thunderbird with your script.  The firefox update worked great.  Thanks!

Here's the error message I get after I ask it not to backup my profiles.

File "/home/peter/Desktop/ubuntuzilla_4.0.0.py", line 493, in backupProfile
    if os.path.lexists(os.path.expanduser('~/.thunderbird')) and stat.S_ISDIR(os.lstat(os.path.expanduser('~/.thunderbird'))[stat.ST_MODE]) and os.stat.lexists(os.path.expanduser('~/.mozilla-thunderbird')) and stat.S_ISDIR(os.lstat(os.path.expanduser('~/.mozilla-thunderbird'))[stat.ST_MODE]):
AttributeError: 'builtin_function_or_method' object has no attribute 'lexists'


I don't understand this at all.  Does anyone else here?

Thanks,

BR

hi, yes, that's a typo i made apparently. :)
please change that line so that instead of "os.stat.lexists" it has "os.path.lexists". then it should run. please let know how that goes. :)
**edit: i made the bugfix-only release, 4.0.1. get the latest from [the project site]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla"). (if you want to avoid editing the script yourself)

---

