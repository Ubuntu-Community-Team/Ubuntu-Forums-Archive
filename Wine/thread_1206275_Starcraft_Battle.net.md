---
title: "Starcraft Battle.net"
date: 2009-07-07
forum: Wine
---

### Post by element_G on 2009-07-07
I'm running xubuntu 8.10 on my laptop and I'm trying to play Starcraft online (Battle.net) but bnet complains saying "battle.net was unable to identify your application version. Please uninstall and then reinstall the application..."

I have applied the latest update patch for Starcraft and I am running the latest wine. (Starcraft runs fine in single player mode)

Google helped me find this post [http://ubuntuforums.org/showpost.php?p=6320978&postcount=2](http://ubuntuforums.org/showpost.php?p=6320978&postcount=2) about making a couple dll's native in winecfg but this has not fixed things for me:mad:

please help!:KS

---

### Post by element_G on 2009-07-07
anyone ?

---

### Post by bvanaerde on 2009-07-07
Is it possible you're using a crack to run the game (no-cd crack or something else)?
If not, please don't be offended by my comment... ;)

---

### Post by element_G on 2009-07-07
none taken ;)

I'm running a completely legit copy of SC. With the 1.16 patch, blizzard made SC able to run without the cd anyway, but regardless I did have the Broodwar CD in the drive when I got the error in the OP.

---

### Post by element_G on 2009-07-07
Searching Wine's appDB I have found a solution!!!

1. No Compiz allowed (wasn't running that anyway)

2. Uncheck the boxes:

Allow the window manager to control the windows       and

Allow the window manager to decorate the windows

in winecfg under the graphics tab

):P


edit: a quick matchup has proved it, SC on b.net under ubuntu 8.10 and wine works! On a side note, I am on 8.10 because 9.04's horrible intel drivers have caused SC to lag terribly (it is unplayable online, single player is OK, and yes I have tried fixing it with the fixes mentioned in 9.04's release notes). But I still found I could upgrade XFCE to 4.6 in 8.10 so now that SC is fixed I am a very happy camper. :lolflag:

---

### Post by beefcurry on 2009-07-20
Thanks, that solution worked like a charm, too bad compiz screws up b-net.

---

