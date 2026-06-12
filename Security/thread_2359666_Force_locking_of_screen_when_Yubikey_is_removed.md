---
title: "Force locking of screen when Yubikey is removed"
date: 2017-04-26
forum: Security
---

### Post by swedishmike on 2017-04-26
Hi there,

I'm running into a bit of an issue when I'm trying to force the screensaver to kick in when I remove my Yubikey. I've sort of gotten things to work, as far as the udev rules kicking in when expected to.

The problem is though that I'm not getting the syntax for forcing the screen to lock to kick in.

Currently I got a very simple file that works when I run it as my own user, mike, but not when kicked off by the system.

The file looks as follows:

```
#!/bin/bash
/bin/su mike -c "DISPLAY=0: /usr/bin/light-locker-command -l"

```

If I run it interactively as 'mike' it immediately locks the screen.

If I run it interactively as 'root' it hangs for a bit and then exits with the error message: **** Message: Failed to get session bus: Could not connect: Connection refused**

If it is run automatically when I remove the Yubikey I get the following error in /var/log/syslog:** Apr 26 14:45:01 m-xubuntu systemd-udevd[7700]: Process '/usr/local/bin/mikelock' failed with exit code 1.**

To me it seems to have to do with 'not reaching the session' for the user mike in this case - but I might be barking up the wrong tree here?

I've tested to run "light-locker-command -l" as root in a terminal when logged in as mike to Xbuntu and that just executes with no error message at all but don't lock the screen either. Running it interactively as 'mike' locks the screen straight away.

Have anyone else tried something similar and got it to work?

Thanks in advance, MIke

---

