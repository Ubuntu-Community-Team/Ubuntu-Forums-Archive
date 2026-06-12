---
title: "Snap Store"
date: 2018-09-24
forum: Ubuntu Development Version
---

### Post by Frogs Hair on 2018-09-24
After installing an application the snap store stayed on the application  installation page and wont return to the main page where one can browse  or install other applications. Bug [Here]("https://bugs.launchpad.net/snapstore/+bug/1794191")

---

### Post by idkwhatimdoing1.0 on 2018-09-24
I found a small work around to get around this problem without having to reboot anything. If it stuck and no matter how many times you click the big red x button and reopen it it shows the same thing simple click on the "Show Applications" button (bottom left for default) and select any app and right click on it's icon. You will see many options. Click "Show details" and automatically it will open the snap store with the details of your application and from there simply press wherever you need to go. Here is an example.

Scenerio: I decided to install firefox so I went into the snap store and installed it. Now I want to install Spotify but I can't leave the Firefox page and I really don't want to reboot anything.

[ATTACH=CONFIG]281182[/ATTACH]



so i then press the My Applications and select some random app and right click it then press Show details and this will pop up

[ATTACH=CONFIG]281181[/ATTACH] then from there I can just click on all or search for whatever I wish to look at. 


Note: THIS IS JUST A WORKAROUND UNTIL THIS BUG CAN BE FIXED PLEASE DON'T USE THIS AS A PERMANENT SOLUTION...

---

### Post by Frogs Hair on 2018-09-24
No luck with the W/O /, but thanks and give the bug report a me too if possible.

---

### Post by corradoventu on 2018-09-25
From system monitor: end process of gnome-software and then restart from applications. I'm unable to find an open bug about.

---

### Post by Frogs Hair on 2018-09-25
> **corradoventu said:**
> From system monitor: end process of gnome-software and then restart from applications. I'm unable to find an open bug about.

This regarding the snap store application installable from Ubuntu Software . Is it using the same process ?

Edit: Snap store is returning to the main applications page on reboot, but not all available applications  are listed there.

---

### Post by mc4man on 2018-09-26
> **Frogs Hair said:**
> After installing an application the snap store stayed on the application  installation page and wont return to the main page where one can browse  or install other applications. Bug [Here]("https://bugs.launchpad.net/snapstore/+bug/1794191")
After installing did you try the back button or just close snap store, then reopened at some point to see this?
( at least here c[closing ubuntu-software on an app page ]("https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1794649")presents this behaviour when re-opened

---

### Post by corradoventu on 2018-09-27
same problem, same bypass for Ubuntu Software 3.30.0 on Cosmic installed from Ubuntu 18.10 "Cosmic Cuttlefish" - Beta amd64 (20180927)

---

### Post by Frogs Hair on 2018-09-27
> **mc4man said:**
> After installing did you try the back button or just close snap store, then reopened at some point to see this?
( at least here c[closing ubuntu-software on an app page ]("https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1794649")presents this behaviour when re-opened

The back button for the snap store doesn't function for me. Ubuntu software appears to work normally so far.

---

