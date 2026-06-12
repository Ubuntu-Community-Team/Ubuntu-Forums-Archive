---
title: "Vidalia detected that the Tor software exited unexpectedly."
date: 2012-01-17
forum: Security
---

### Post by mdavis1231 on 2012-01-17
Whenever I've had Vidalia running, stop Tor, and close Vidalia out, the next time I try to open Vidalia, I get the error message "Vidalia detected that the Tor software exited unexpectedly."  When I click on "Show Log", here is a screenshot.

Is there anything anyone knows of that I can do to correct this?

---

### Post by mdavis1231 on 2012-06-10
> **mdavis1231 said:**
> Whenever I've had Vidalia running, stop Tor, and close Vidalia out, the next time I try to open Vidalia, I get the error message "Vidalia detected that the Tor software exited unexpectedly."  When I click on "Show Log", here is a screenshot.

Is there anything anyone knows of that I can do to correct this?

I haven't found any way around this, since 'sudo killall tor' doesn't seem to do the trick.  I just restart my computer. :(

---

### Post by shymega on 2012-06-10
Hi,

Need to check some things first. First, have you changed the configuration of Tor/Vidalia?
Second, have you tried purging vidalia from the system and reinstalling?

Thanks,
SM


EDIT: Found this post (ubuntuforums.org/showthread.php?p=12014754#post12014754) which seemed to fit your problem. I would request that you try it with support from me and report back? Thanks

---

### Post by uRock on 2012-06-10
Moved to *Security Discussions*.

---

### Post by ottosykora on 2012-06-10
> **mdavis1231 said:**
> Whenever I've had Vidalia running, stop Tor, and close Vidalia out, the next time I try to open Vidalia, I get the error message "Vidalia detected that the Tor software exited unexpectedly."  When I click on "Show Log", here is a screenshot.

Is there anything anyone knows of that I can do to correct this?

sudo apt-get install sysv-rc-conf

sudo sysv-rc-conf

then scroll down to tor and unselect all tickboxes with spacebar

reboot

then you can operate the tor with vidalia

---

### Post by lee_can on 2012-06-11
This method doesnt work on backtrack (ubuntu lucid).
Any advice?

---

### Post by zombifier25 on 2012-06-11
(you may want to reset the settings first, e.g. purge and reinstall Tor and Vidalia)
First off, make sure you are allowed to control Tor. Add yourself to the group debian-tor if you are not a part.
```
sudo adduser username debian-tor
```

Then fire up Vidalia and see if it's fixed.

IMPORTANT NOTE: If you're not using Tor as a relay, but want to use it for actual browsing, then you should be using the Tor Browser Bundle itself. It's safer.

---

