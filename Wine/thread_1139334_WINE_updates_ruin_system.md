---
title: "WINE updates ruin system"
date: 2009-04-26
forum: Wine
---

### Post by hailholyghost on 2009-04-26
Hey,

I've kept a log on MS word since 2005, and since I switched to Linux WINE has let me keep on using the same configuration I had become accustomed to for the last 4 years.

Unfortunately, 2 weeks ago I updated the system and now the music player doesn't work, and MS Office shuts itself down.  I upgraded again a short while ago, and the problems became so bad that the program is not even usable any more.:(

I tried to reinstall the version I was using a few weeks ago, but got the error message "Dependency is not satisfiable".:confused:

Is there any way I could remove the last 2 updates?

In the attempt to solve minor problems, I have created major ones!

I appreciate your time!:KS

---

### Post by ajackson on 2009-04-27
How is this the fault of Wine?

---

### Post by Bakon Jarser on 2009-04-27
It might work if you uUninstall wine and remove it's dependencies.  Run
```
sudo apt-get remove wine
sudo apt-get autoremove

```

Then try installing the older version of wine.  If all your programs work with a certain version of wine you shouldn't upgrade to a new version.  Regressions are common in wine.

---

### Post by u235sentinel on 2009-04-27
> **Bakon Jarser said:**
> It might work if you uUninstall wine and remove it's dependencies.  Run
```
sudo apt-get remove wine
sudo apt-get autoremove

```

Then try installing the older version of wine.  If all your programs work with a certain version of wine you shouldn't upgrade to a new version.  Regressions are common in wine.

especially since the latest stable is 1.0.1 and they just released 1.1.20 today.

I'm using 1.1.18 personally and it seems to work well for most of what I do.  Some stuff simply don't work however without issues unless I downgrade to 1.0.1 again.  And then I have other issues :-)

Go figure.  But then I expected that from Windows as well.  I had OTHER issues ;-)

---

