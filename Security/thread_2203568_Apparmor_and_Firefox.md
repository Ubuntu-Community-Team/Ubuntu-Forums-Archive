---
title: "Apparmor and Firefox"
date: 2014-02-04
forum: Security
---

### Post by cogset on 2014-02-04
As I understand,Ubuntu is possibly the only distro coming with a preconfigured Apparmor profile for Firefox:as I'm willing to learn how Apparmor works,I've tried to enable the  **usr.bin.firefox** profile inside /etc/apparmor.d in complain mode,and I can see from the system logs that it is working.
But,upon restarting the system,the profile is disabled again:is this how it works? 
Is there any way to set it permanently in complain mode (maybe a script in /etc/rc.local would do?),and,furthermore,has anyone enforced the profile and observed any adverse effect?

Also,I've seen two other profiles,namely **usr.lib.firefox.firefox** and ** usr.lib.firefox.firefox.sh** in /usr/share/doc/apparmor-profiles/extras,how do you use them?

---

### Post by Dave_L on 2014-02-04
Once you enable a profile, it should remain enabled.

Did you delete /etc/apparmor.d/disable/usr.bin.firefox ?

If so, does that file (symbolic link) get recreated when you boot?

---

### Post by cogset on 2014-02-05
Frankly,I forgot about deleting that link:for the time being,I've put something  in rc.local and it apparently works-however,I suppose the proper way to do it would be deleting the link.

---

