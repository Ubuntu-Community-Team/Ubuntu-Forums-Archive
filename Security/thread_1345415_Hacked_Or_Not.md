---
title: "Hacked Or Not?"
date: 2009-12-04
forum: Security
---

### Post by caffeinated blood on 2009-12-04
[SIZE=2]This is my first post - please be kind. I'm still in limbo with an XP/Ubuntu dual-boot PC. I have some encrypted files in Documents that are shown to have been accessed at a time while I was online doing other things. All these files were accessed at the exact same time, yet none of my regular files were accessed. Is there some system/program check that may have caused this such as an update? Looking in Log Files I couldn't find anything to coincide with the time event. I found CRON events listed throughout that I don't know why have started. I did a search and found others having this issue with CRON. Remote Desktop is/was off. I looked at Empathy IM settings, which I have never used, and found the settings to be as if I had been using it - is this just the Ubuntu install default? Could someone use Empathy to access these files without my knowledge? Any response is greatly appreciated.[/SIZE]

---

### Post by cariboo on 2009-12-04
I seriously doubt you've been cracked. To see what cron jobs are running, check /etc/cron.hourly, /etc/cron.daily. /etc/cron.weeky and /etc/cron.monthly

---

### Post by caffeinated blood on 2009-12-04
[SIZE=2]Thanks for responding. My concern is how all my encrypted files were accessed at the same time(time event in properties), yet my other files were untouched. This happened while online and not by me. I only mentioned the cron jobs because I had not noticed them before. Something accessed these particular files. I can't find anything in any log that coincides with the time event. Any ideas of a cause? [/SIZE]

---

### Post by oOarthurOo on 2009-12-04
Under cron there used to be an entry to updatedb, an indexing service to make locating files quicker. I'd manually run the program and then check the time stamps on the file. Then check to see if it is scheduled to run ever.

I wouldn't be too concerned about this at the moment. It's something interesting to look into, but it doesn't strike me as being particularly worrisome.

A second "experiment" you might want to try is to try to open the encrypted files, but give an incorrect password. Then check the timestamps again. If it's changed then accessed probably isn't the one you want to look at. Perhaps modified would be a better indicator.

Lastly, I seem to recall a virus scanning program on windows that caused every file scanned to update its last accessed time. Or at least, that was the working theory at the time. Something else you may want to look at as a possible explanation.

---

