---
title: "Apparmor profile for Dropbox?"
date: 2010-10-31
forum: Security
---

### Post by thaidog on 2010-10-31
Does anyone have a profile for Dropbox? I was thinking about something that does not allow anything to execute in the Dropbox directories... etc

---

### Post by foorgol on 2011-03-07
Hi,

I just create an apparmor profile for dropbox myself. See here:

[http://dl.dropbox.com/u/22843507/usr.bin.dropbox](http://dl.dropbox.com/u/22843507/usr.bin.dropbox)

My primary intention was to prevent dropbox from sniffing through private files in my home directory except for the shared folder and some configuration files (e. g. fontconfig).

Unluckily dropbox -- or one of its child processes -- requires access to the console devices in /dev. I hope it doesn't intercept all my keystrokes now... ;)

Read access to /proc is necessary because it calls "ps" sometime during the start process.

With this profile, apparmor still throws some warnings in the log files, but dropbox seems to work fine. And I didn't want to grant more permissions.


Please note that this is my first apparmor profile. Maybe something can be done better or easier... especially the two lines for each directory access (one for the dir itself, one for the files in the dir) are somehow annoying.


Good luck with "fine tuning" the profile to your needs!

---

