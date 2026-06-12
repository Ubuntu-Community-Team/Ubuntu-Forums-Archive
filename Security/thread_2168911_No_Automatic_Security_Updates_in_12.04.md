---
title: "No Automatic Security Updates in 12.04?"
date: 2013-08-19
forum: Security
---

### Post by BuntuSeriously on 2013-08-19
Greetings!

It seems as though setting the "Software Sources" applet to "Download and install automatically" in 12.04 does nothing: All is set for a daily security updates run; and nothing will happen for an indefinite timeframe until a manual check is made via the Update Manager UI.  Of note, Update Notifier is set to launch @ startup per distro defaults.

I need unattended and automatic security updates on a daily basis here; as the end-user target is totally clueless in this case...

Is this a known problem?  Is there a solution???

Thanks for the help!

---

### Post by ibjsb4 on 2013-08-19
This is dated, but me wonders ..

[http://ubuntuforums.org/showthread.php?t=1004021&p=6425831&viewfull=1#post6425831](http://ubuntuforums.org/showthread.php?t=1004021&p=6425831&viewfull=1#post6425831)

[https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)

---

### Post by CharlesA on 2013-08-20
I run unattended updates on my Precise Desktop with no problems.

Granted I actually use the unattended-upgrades package, and not the software sources thing.

---

### Post by BuntuSeriously on 2013-08-20
Thanks, folks, for the tips.  Looks like I'll be heading on over to the "unattended-upgrade_**s**_" feature for my daily security update chores.  It seems as though this might do an end-run around some apparent "Update Manager" bugginess...

Now, in accord with the info which ibjsb4 so kindly linked, is the following commandline still correct; enabling unattended-upgrades to start at each boot and do the work of checking the servers for and installing updates in accord with the preferences selected via the "Software Sources" applet UI:

```
sudo dpkg-reconfigure -plow unattended-upgrades
```

Or, is there something else I should know to robustly enable this feature to always run on a 12.04 install (and beyond?)

Indeed, if I can count on this, I'll simply turn off the alarm and get on with life...

Thanx so much :)

---

