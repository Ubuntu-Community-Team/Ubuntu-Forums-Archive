---
title: "Thunderbird Not Working After Update"
date: 2012-08-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by zenarcher on 2012-08-14
Thunderbird email is not working for me, following an update for it this morning.  The installed version of Thunderbird is 15.0-b3+Build1-0ubun.  I'm running a 64 bit system.

Trying to start Thunderbird from the command line, here is what I'm getting:

zenarcher@stanmain:~$ thunderbird
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.
Fontconfig warning: "/etc/fonts/conf.d/65-droid-sans-fonts.conf", line 103: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/65-droid-sans-fonts.conf", line 138: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 26: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 31: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 40: Having multiple values in <test> isn't supported and may not works as expected
enigmail.js: Registered components

(thunderbird:3105): e-data-server-ERROR **: Error calling StartServiceByName for org.gnome.evolution.dataserver.Sources0: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ExecFailed: Failed to execute program /usr/lib/evolution/evolution-source-registry: Success
Trace/breakpoint trap (core dumped)

Anyone else finding this or have any ideas?

Thanks,
zenarcher

---

### Post by GreatDanton on 2012-08-14
There was a thread about font issue: [http://ubuntuforums.org/showpost.php?p=12159762&postcount=13](http://ubuntuforums.org/showpost.php?p=12159762&postcount=13)

Try to correct this and then try again.

Regards.

---

### Post by zenarcher on 2012-08-14
Thanks.  I'll give it a try.

Regards,
zenarcher

---

### Post by ventrical on 2012-08-14
Works great here.

---

### Post by GreatDanton on 2012-08-14
Also working great here, but I have 32-bit.

---

### Post by ventrical on 2012-08-14
Yes .. i386 here.

---

### Post by zenarcher on 2012-08-14
Weird.  It apparently only messed up on one system.  I have an identical system, also running exactly the same of everything and Thunderbird is working just fine on the second one.  Not sure what that's all about.  

Regards,
zenarcher

---

### Post by zenarcher on 2012-08-15
Not sure what the problem was.  I did a fresh install of 12.10 and Thunderbird is now working fine.

Regards,
zenarcher

---

### Post by jfernyhough on 2012-08-15
For me it was an issue with the Evolution Data Server plugin. Fixed by running in safe mode, disabling EDS Contact Integration, restarting Thunderbird normally.

For safe mode:
$ thunderbird -safe-mode

Or for Daily:
$ thunderbird-trunk -safe-mode

---

### Post by zenarcher on 2012-08-15
> **jfernyhough said:**
> For me it was an issue with the Evolution Data Server plugin. Fixed by running in safe mode, disabling EDS Contact Integration, restarting Thunderbird normally.

For safe mode:
$ thunderbird -safe-mode

Or for Daily:
$ thunderbird-trunk -safe-mode

Thanks for that info.  I also ran into that one this morning, as well.

Regards,
zenarcher

---

