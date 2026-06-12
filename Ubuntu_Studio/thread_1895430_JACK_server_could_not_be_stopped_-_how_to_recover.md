---
title: "JACK server could not be stopped - how to recover?"
date: 2011-12-14
forum: Ubuntu Studio
---

### Post by Ansible on 2011-12-14
I'm able to get JACK to run using qjackctl, and make use of various audio programs.  

The problem is when its time to shut down JACK, I get an error:

D-BUS: JACK server could not be stopped

At this point I'm pretty much stuck - I can't stop the jack server or restart it either.  My MPD server can still play, but audio programs like sooperlooper won't work.

Questions:

1) is there something I can do to kill off the old jack server so that I don't have to reboot?
2) any tips on getting jack to shut down normally?

More info:

64 bit ubuntu studio
AudioFire4 1394 IO box.

---

### Post by jejeman on 2011-12-15
There should be no problem to kill jack with
```
killall -9 jackd
```

---

### Post by dawiba on 2011-12-15
Or...

In Jack Settings Window, click on 'Misc' tab and make sure

'Enable D-Bus interface'

is unchecked

---

### Post by Sith2112 on 2012-01-13
> **dawiba said:**
> Or...

In Jack Settings Window, click on 'Misc' tab and make sure

'Enable D-Bus interface'

is unchecked

Ok that solved the issue.. I have been trying to find out how to get the "jackdbus" process to stop automatically and this worked... 
Thanks for the help.  This is appreciated by one Linux Newbie.

Sith2112

---

