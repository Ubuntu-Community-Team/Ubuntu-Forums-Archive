---
title: "HOW-TO remove AVG Anivirus"
date: 2007-04-28
forum: Tutorials
---

### Post by mikewhatever on 2007-04-28
Have you downloaded and installed AVG as the [COLOR="DarkRed"]avg75fld-r45-a0973.i386.deb[/COLOR] file following [this how-to]("http://ubuntuforums.org/showthread.php?t=136064") or perhaps another? If it does not work the way expected, or you just don't like it, uninstalling it with the following command gives en error:
> sudo dpkg -P (or -r) avg75fld

(Reading database ... 131758 files and directories currently installed.)
Removing avg75fld ...
* Stopping avgdkill: 246: Illegal number: -
local: 246: 4183: bad variable name
( not running)
* [fail]
invoke-rc.d: initscript avgd, action "stop" failed.
dpkg: error processing avg75fld (--remove):
subprocess pre-removal script returned error exit status 150
Errors were encountered while processing:
avg75fld

Try the following now:
> sudo dpkg -R -P avg75fld

Then remove the leftovers in /opt/grisoft

> sudo rm -r /opt/grisoft

---

### Post by zainka on 2010-01-11
For avg 8.5 as latest (afaik) when reading 8.Januar.2010 (happy new year by the way) use the following command:

```
sudo dpkg -R -P avg85flx
```

---

### Post by mikewhatever on 2010-03-06
Hey, thanks for updating this. I haven't used AVG on Ubuntu for quite some time.:D

---

### Post by nagubhai on 2011-10-23
Try below for latest avg2011

```
sudo dpkg -R -P avg2011flx
```

---

### Post by anGel_OnE on 2011-11-29
Thank you so much!

---

### Post by Cassist on 2013-06-21
Can anyone post how you do this for AVG 2013, because simply replacing 2011flx with 2013flx doesn't work. (I use Lubuntu btw).

---

### Post by mikewhatever on 2013-08-31
This thread is not about installing or replacing, but rather about removing, and removing avg2013flx seems to work as well as before.
```

~$ sudo dpkg -P -R avg2013flx
(Reading database ... 148706 files and directories currently installed.)
Removing avg2013flx ...
 * Stopping avgd.                                                                                                [ ok ]
Uninstalling 'avgd' service initscripts...
Unregistering 'avgd' service ...
 Removing any system startup links for /etc/init.d/avgd ...
   /etc/rc0.d/K20avgd
   /etc/rc1.d/K20avgd
   /etc/rc2.d/S20avgd
   /etc/rc3.d/S20avgd
   /etc/rc4.d/S20avgd
   /etc/rc5.d/S20avgd
   /etc/rc6.d/K20avgd
Purging configuration files for avg2013flx ...
dpkg: warning: while removing avg2013flx, directory '/opt' not empty so not removed.
Processing triggers for man-db ...

```
Done!

---

### Post by jooge on 2013-10-26
> **mikewhatever said:**
> This thread is not about installing or replacing, but rather about removing, and removing avg2013flx seems to work as well as before.
```

~$ sudo dpkg -P -R avg2013flx
(Reading database ... 148706 files and directories currently installed.)
Removing avg2013flx ...
 * Stopping avgd.                                                                                                [ ok ]
Uninstalling 'avgd' service initscripts...
Unregistering 'avgd' service ...
 Removing any system startup links for /etc/init.d/avgd ...
   /etc/rc0.d/K20avgd
   /etc/rc1.d/K20avgd
   /etc/rc2.d/S20avgd
   /etc/rc3.d/S20avgd
   /etc/rc4.d/S20avgd
   /etc/rc5.d/S20avgd
   /etc/rc6.d/K20avgd
Purging configuration files for avg2013flx ...
dpkg: warning: while removing avg2013flx, directory '/opt' not empty so not removed.
Processing triggers for man-db ...

```
Done!

Thx a ton!

---

