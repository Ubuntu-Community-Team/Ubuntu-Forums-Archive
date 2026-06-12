---
title: "Using gksudo to run a wine launcher"
date: 2008-12-14
forum: Wine
---

### Post by Lunchbox05 on 2008-12-14
I am trying to get a old game to work (lineage 1) with wine, but the error im getting is that gameguard is having problems with me not using an administrator account. I have read the posts about using a desktop launcher to run anything you drag into it in root. But when I do so it asks for my password then does nothing. I checked my sysmon and neither wine nor the child process is running. 

The command in the gksudo launcher im using is:

gksudo "gnome-open %u"

The command the launcher is using is:

env WINEPREFIX="/home/ryan.wine" wine "Z:\home\ryan\lineage\Lin270.exe" 68.186.218.167 2600

When i don't use the gksudo launcher it runs the program but i get the permission error.

Thoughts? Ideas? Need more info?

---

### Post by CatKiller on 2008-12-14
> **Lunchbox05 said:**
> I am trying to get a old game to work (lineage 1) with wine, but the error im getting is that gameguard is having problems with me not using an administrator account.

That will be to do with the pretend Windows environment that Wine creates. Nothing to do with your Linux environment. Running Wine as root will not help you.

I don't know if it's possible to configure Wine to pretend that the user is Administrator, but that's the kind of thing you'd be looking for.

[Wine's AppDB]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=911") says that the game doesn't work for precisely this reason.

---

### Post by Lunchbox05 on 2008-12-14
Thanks, i was hoping to maybe find some answers here but o wells, back to windows

---

### Post by bodhi.zazen on 2008-12-14
You should NOT run wine as root.

---

