---
title: "Missing items in System Settings"
date: 2014-03-12
forum: Ubuntu Development Version
---

### Post by Zhu_Ge_Liang on 2014-03-12
I've just upgraded my OS to version 14.04 from version 13.10, then met a problem: Missing many items in System Setting, such as Text entry setting, Appearance,... See the following image.

How do I fix it? Thank you.

[IMG]http://drp.io/files/53203011b96e5.png[/IMG]

---

### Post by newb85 on 2014-03-12
I've never used a beta release, but I would suspect it had something to do with that. Beta isn't for beginners. And there's a dedicated forum for beta release.

---

### Post by bapoumba on 2014-03-12
Moved to Ubuntu +1.

---

### Post by grahammechanical on 2014-03-12
Your experience shows that it is too soon to upgrade from 13.10 to 14.04. I would suggest that you do daily updates in the hope that the problem will be resolved.

Over the last few weeks we have had gnome control center replaced by unity control center. I am not sure if the transition is complete. I did see an update to unity control center when I updated just a few minuets ago.

I doubt if the developers have thought much about the upgrading of 12.04 to 14.04 or 13.10 to 14.04. That must happen much closer to the release date.

You could also look in the Dash to see if the Utilities are represented there.

Regards.

---

### Post by philinux on 2014-03-12
+1 I tried an update from 13.10 too. Ended up doing a clean install from the daily iso.

Running smoothly now. Few glitches here and there as is to be expected.

---

### Post by kansasnoob on 2014-03-12
I just did an upgrade yesterday from Saucy to Trusty and things looked good until I blew it up fiddling with screen resolutions. I used:

```
update-manager -d -c
```

What method did you use to upgrade?

---

### Post by Doug S on 2014-03-12
I guess if one has been updating for awhile (I have since the start of the cycle) then things are O.K, at least it is for me:```
[COLOR=#ff0000]DistroRelease: Ubuntu 14.04[/COLOR]
ExecutablePath: /usr/bin/compiz
ExecutableTimestamp: 1392729263
[COLOR=#ff0000]InstallationDate: Installed on 2013-09-04 (174 days ago)
InstallationMedia: Ubuntu 13.10 "Saucy Salamander" -[/COLOR] Alpha amd64 (20130903)
```

---

### Post by mc4man on 2014-03-12
> **Zhu_Ge_Liang said:**
> I've just upgraded my OS to version 14.04 from version 13.10, then met a problem: Missing many items in System Setting, such as Text entry setting, Appearance,... See the following image.

How do I fix it? Thank you.


That's likely caused from not having unity-control-center installed, ck. & install if not already.

---

### Post by Cavsfan on 2014-03-12
I re-installed 2 days ago and the updates after that have been fantastic!

```
cavsfan@cavsfan-MS-7529:~$ ls -ld /var/log/installer | awk '{ print $6 " " $7 " " $8 }'
Mar 10 10:38



```

[ATTACH=CONFIG]251074[/ATTACH]

---

### Post by Cavsfan on 2014-03-12
> **mc4man said:**
> That's likely caused from not having unity-control-center installed, ck. & install if not already.

That comes pre-installed now. I just checked. I remember adding it on a previous install.

---

### Post by Castea_Min on 2014-04-20
I alredy have solved my problem, similar to this. Check this link [http://tanyadong.co.vu/6/after-upgrade-ubuntu-some-items-are-missing-system-settings](http://tanyadong.co.vu/6/after-upgrade-ubuntu-some-items-are-missing-system-settings)

---

