---
title: "Uninstalling"
date: 2008-07-07
forum: The Cafe
---

### Post by Mateo on 2008-07-07
One thing I like about Ubuntu is the ease of uninstalling. I notice some things that I no longer use and fire up Synaptic, search for them and mark them to uninstall, then uninstall all at once.  I was cleaning up a Windows machine this morning and had to uninstall each piece of software one-by-one.  Many of these required *many* clicks to get through, with the uninstaller seemingly wanting to confirm every move I made.  One particular instance was annoying.  The Adobe Palm converter would not uninstall because I had already uninstalled Palm Desktop.  So I had to redownload Palm Desktop (50mb), reinstall it, then uninstall the Adobe Palm converter and finally reuninstall Palm Desktop.  After I had completely uninstalled all that I wanted (which took well over an hour), I of course had to restart my computer (even though most programs asked me to after each uninstall, I simply ignored their advice), I finally had to go into the Program Files directory and clean up the files the uninstallers had missed (which was plenty).  Just reiterated my love for the Ubuntu package management system.

---

### Post by RiceMonster on 2008-07-07
Ha, I thought this was going to be a thread about how you were getting rid of Ubuntu.

Anyway, yeah I love having a package manager. It really does make installing/uninstalling software really convenient. On Ubuntu to uninstall, I used:
```
sudo apt-get remove package && sudo apt-get autoremove
```

Because I didn't feel like going through synaptic or add/remove.

On arch, I use:
```
sudo pacman -Rs package
```

---

### Post by FuturePilot on 2008-07-07
True True. That's only half of it though. I hate updating Windows machines. It's such a pain. You have to start each program and use the program's updater and if it doesn't have one it's off to Google. Whereas in Ubuntu I almost never have to worry about that. I just let Update Manager take care of that. I feel spoiled. :mrgreen:

---

### Post by Mateo on 2008-07-07
> **RiceMonster said:**
> Ha, I thought this was going to be a thread about how you were getting rid of Ubuntu.

Anyway, yeah I love having a package manager. It really does make installing/uninstalling software really convenient. On Ubuntu to uninstall, I used:
```
sudo apt-get remove package && sudo apt-get autoremove
```

Because I didn't feel like going through synaptic or add/remove.

On arch, I use:
```
sudo pacman -Rs package
```


I do it that way sometimes, but i don't always know the name of the package so synaptic is fine even though the search is a little slow.

---

### Post by RiceMonster on 2008-07-07
> **FuturePilot said:**
> True True. That's only half of it though. I hate updating Windows machines. It's such a pain. You have to start each program and use the program's updater and if it doesn't have one it's off to Google. Whereas in Ubuntu I almost never have to worry about that. I just let Update Manager take care of that. I feel spoiled. :mrgreen:

That makes me think, I almost never updated software on Windows, other than the Windows updates. I remember using iTunes and getting a popup message saying "There's a new version of iTunes available, download? <y/n>" and I would think "NO, I DON'T CARE ALREADY!". Now I find myself updating all the time :lolflag:.

---

