---
title: "unreal lock-out: hotspot switches crashes config window"
date: 2014-02-23
forum: Ubuntu Development Version
---

### Post by buntuyu on 2014-02-23
So, i am with Trusty 14.04, gnome metacity, and it's making me bleed

I don't have the networking applet in the top bar (malfunction), so I alternatively have been using the system settings window/dialog, where I click on networking and select my wi-fi network.  Suddenly, that method is failing because, for no apparent reason, the window is showing me my hotspot is on, with a switch to turn it off. I toggle the switch, get a confirmation dialogue, confirm, and the whole window crashes, and I am left with the same setting.  Next invocation of the settings shows that hotspot is still there.

I don't remember doing anything other than uninstalling / purging ibus.

I just re-installed it and rebooted.  Hotspot is still obnoxiously imposing itself, and preventing me from getting to a wifi as access consumer (rather than provider)

please help!?

Is there a way to turn off or purge the hostpot from the command line, or some other alternative?

Perhaps needless feedback to developers:  PLEASE be extra cautious with network access!  That's the ONE single thing that cripples the user the most! Without network access you can't do any repair, updates, bug reporting, etc... 

thanks

---

### Post by buntuyu on 2014-02-23
> **buntuyu said:**
> So, i am with Trusty 14.04, gnome metacity, and it's making me bleed

I don't have the networking applet in the top bar (malfunction), so I alternatively have been using the system settings window/dialog, where I click on networking and select my wi-fi network.  Suddenly, that method is failing because, for no apparent reason, the window is showing me my hotspot is on, with a switch to turn it off. I toggle the switch, get a confirmation dialogue, confirm, and the whole window crashes, and I am left with the same setting.  Next invocation of the settings shows that hotspot is still there.

I don't remember doing anything other than uninstalling / purging ibus.

I just re-installed it and rebooted.  Hotspot is still obnoxiously imposing itself, and preventing me from getting to a wifi as access consumer (rather than provider)

please help!?

Is there a way to turn off or purge the hostpot from the command line, or some other alternative?

Perhaps needless feedback to developers:  PLEASE be extra cautious with network access!  That's the ONE single thing that cripples the user the most! Without network access you can't do any repair, updates, bug reporting, etc... 

thanks

"dmesg | tail" said I should install "nss-myhostname", so I did 

sudo apt-get install libnss-myhostname

after which, the settings window stopped crashing.  Still, this is a bug (thus, I don't want to mark it as "SOLVED"), PARTICULARLY and ESPECIALLY because it can be circumstantially fatal to network access... (luckily, I had an ethernet connection close by, but in other circumstances I may have been locked out severely, with the vicious circle of not having network access to fix my network access)

---

### Post by sammiev on 2014-02-23
14.04 has not been released yet. You should have posted this in the Ubuntu + 1 forums. I'm sure a Mod/Admin will move it shortly.

---

### Post by Iowan on 2014-02-23
> **sammiev said:**
> ... I'm sure a Mod/Admin will move it shortly.
Moved.

---

