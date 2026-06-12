---
title: "app armor logs with snap"
date: 2020-05-03
forum: Security
---

### Post by ashokpappu on 2020-05-03
hi All
I am getting inundated with the log messages.  I don't know where the profile is and what to adjust.  this happens as soon as i open the snap store.
Can you please advise

```
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04 LTS
Release:	20.04
Codename:	focal
```



```
type=AVC msg=audit(1588524534.236:6171): apparmor="DENIED" operation="open" profile="snap.snap-store.ubuntu-software" name="/var/lib/snapd/hostfs/usr/share/icons/hicolor/scalable/stock/object/" pid=2270 comm="snap-store" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
type=AVC msg=audit(1588524534.236:6172): apparmor="DENIED" operation="open" profile="snap.snap-store.ubuntu-software" name="/var/lib/snapd/hostfs/usr/share/icons/hicolor/icon-theme.cache" pid=2270 comm="snap-store" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
type=AVC msg=audit(1588524534.236:6173): apparmor="DENIED" operation="open" profile="snap.snap-store.ubuntu-software" name="/var/lib/snapd/hostfs/usr/share/icons/hicolor/scalable/stock/table/" pid=2270 comm="snap-store" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
type=AVC msg=audit(1588524534.236:6174): apparmor="DENIED" operation="open" profile="snap.snap-store.ubuntu-software" name="/var/lib/snapd/hostfs/usr/share/icons/hicolor/icon-theme.cache" pid=2270 comm="snap-store" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
type=AVC msg=audit(1588524534.236:6175): apparmor="DENIED" operation="open" profile="snap.snap-store.ubuntu-software" name="/var/lib/snapd/hostfs/usr/share/icons/hicolor/scalable/stock/text/" pid=2270 comm="snap-store" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
type=AVC msg=audit(1588524534.236:6176): apparmor="DENIED" operation="open" profile="snap.snap-store.ubuntu-software" name="/var/lib/snapd/hostfs/usr/share/icons/hicolor/icon-theme.cache" pid=2270 comm="snap-store" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
type=AVC msg=audit(1588524534.236:6177): apparmor="DENIED" operation="open" profile="snap.snap-store.ubuntu-software" name="/var/lib/snapd/hostfs/usr/share/icons/hicolor/symbolic/apps/" pid=2270 comm="snap-store" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
type=AVC msg=audit(1588524534.240:6178): apparmor="DENIED" operation="open" profile="snap.snap-store.ubuntu-software" name="/var/lib/snapd/hostfs/usr/share/icons/gnome/index.theme" pid=2270 comm="snap-store" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
type=AVC msg=audit(1588524534.240:6179): apparmor="DENIED" operation="open" profile="snap.snap-store.ubuntu-software" name="/var/lib/snapd/hostfs/usr/share/icons/" pid=2270 comm="snap-store" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
type=AVC msg=audit(1588524534.240:6180): apparmor="DENIED" operation="open" profile="snap.snap-store.ubuntu-software" name="/var/lib/snapd/hostfs/usr/share/pixmaps/" pid=2270 comm="snap-store" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
```

---

### Post by EuclideanCoffee on 2020-05-03
I found the profile here. 

/var/lib/snapd/apparmor/profiles/snap.snap-store.ubuntu-software

[https://ubuntu.com/server/docs/security-apparmor](https://ubuntu.com/server/docs/security-apparmor)

Then add something like this:

```

/var/lib/snapd/hostfs/usr/share/icons/hicolor/scalable/stock/object/ r,
/var/lib/snapd/hostfs/usr/share/icons/hicolor/icon-theme.cache  r,
 /var/lib/snapd/hostfs/usr/share/icons/hicolor/scalable/stock/table/ r,
 /var/lib/snapd/hostfs/usr/share/icons/hicolor/icon-theme.cache r,

```

You can also add * to folders with multiple objects, so like this.

```

/var/lib/snapd/hostfs/usr/share/icons/hicolor/*

```

Then run the latest update.

apparmor_parser -r /var/lib/snapd/apparmor/profiles/snap.snap-store.ubuntu-software

---

### Post by TheFu on 2020-05-03
No answer for the problem, but you can setup logrotate to rotate based on the size of a log file.  Check out /etc/logrotate.d/ for a number of working, examples.

---

### Post by EuclideanCoffee on 2020-05-04
I've submitted a bug request.[COLOR=#000000]

Please list anymore directories needed, and I'll add those to the request.[/COLOR]

Edit: I made a mistake. This is a generated profile. So fixing it how I recommended is the wrong solution. I've filed a bug to the correct team and will be working on looking into the correct solution.

---

### Post by rlvargas on 2020-05-06
I'm having DENIED issues with the following directories:

/var/lib/snapd/hostfs/usr/share/pixmaps
/var/lib/snapd/hostfs/usr/share/icons
/var/lib/snapd/hostfs/usr/share/fonts
/var/lib/snapd/hostfs/usr/share/mime
/var/lib/snapd/hostfs/usr/share/gdm

According  to the documentation ([https://ubuntu.com/server/docs/security-apparmor](https://ubuntu.com/server/docs/security-apparmor)) adding new rules to "/etc/apparmor.d/local" should fix this.

I've tried but **without success :cry:**. The the rules are ignored.

```

sudo touch /etc/apparmor.d/local/snap.snap-store.ubuntu-software
sudo nano /etc/apparmor.d/local/snap.snap-store.ubuntu-software

```

Add the following lines, save and restart apparmor
```

# fix the 'apparmor="DENIED" operation="open" profile="snap.snap-store.ubuntu-software"' issues...
"/var/lib/snapd/hostfs/usr/share/{pixmaps,icons,fonts,mime,gdm}{,/,/**}" rk,

```

```

sudo systemctl restart apparmor.service

```

Could you please share the link to the bug report you created? I'm also trying to have this resolved.
Thanks!

Edit: ok, I found out why the rules  were ignored.... there is an error while parsing the file. ](*,) 
Also it seems the *local* folder can only be used by the profiles in the parent folder */etc/apparmor.d.*
```

sudo apparmor_parser -r /etc/apparmor.d/local/snap.snap-store.ubuntu-software
AppArmor parser error for /etc/apparmor.d/local/snap.snap-store.ubuntu-software in /etc/apparmor.d/local/snap.snap-store.ubuntu-software at line 10: syntax error, unexpected TOK_MODE, expecting TOK_OPEN

```

---

### Post by TheFu on 2020-05-06
Specific rules are playing whack-a-mole.  The solution needs to provide 100% local control over which directories **every** snap can be constrained inside.

Or have I completely missed the point and this is purely for 1 piece of software?  That just means it is whack-a-mole times .... 50K.

---

### Post by EuclideanCoffee on 2020-05-06
> 
Edit: ok, I found out why the rules  were ignored.... there is an error while parsing the file. [IMG]https://ubuntuforums.org/images/smilies/eusa_wall.gif[/IMG] 


Yup.

I've submitted a patch, but it's still being reviewed.

---

### Post by tony7622 on 2020-11-09
Hello, any news related to this?
Ubuntu 20.10 (Upgrade from 20.04) have a same behavior.

Could You append a link to bug report?

---

### Post by EuclideanCoffee on 2020-11-09
Sure. The issue was closed with no resolution. Labelled Won't Fix.

[https://bugs.launchpad.net/snapd/+bug/1876804](https://bugs.launchpad.net/snapd/+bug/1876804)

I could go back and look into the snapd-desktop and see if there's a related fix. I guess my proposal was denied because it should be in the desktop, not snapd.

---

