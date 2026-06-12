---
title: "Blackberry sync software"
date: 2007-11-22
forum: Tennessee Team - US
---

### Post by madmax04 on 2007-11-22
So is there a good package for keeping a Blackberry 8700C in sync with Evolution?

---

### Post by DoctorMO on 2007-11-23
Not yet, as such. There are several packages that when installed combine into an awesome command line syncing engine; so if you need to install barry, opensync and the opensync plugin for barry. Conduit will in future support opensync and you'll be able to use a nice gui, for now use the cli.

---

### Post by saltydog on 2007-12-11
> **DoctorMO said:**
> Not yet, as such. There are several packages that when installed combine into an awesome command line syncing engine; so if you need to install barry, opensync and the opensync plugin for barry. Conduit will in future support opensync and you'll be able to use a nice gui, for now use the cli.

...and how can I use the cli to sync my BB with Evolution/Thunderbird thru barry?

---

### Post by DoctorMO on 2007-12-11
saltydog, you need to make sure you install opensync barry plugin as well as opensync thunderbird/evo plugins; you then need to set up a syncing set up with those two plugins using multi-sync package.

---

### Post by saltydog on 2007-12-12
> **DoctorMO said:**
> saltydog, you need to make sure you install opensync barry plugin as well as opensync thunderbird/evo plugins; you then need to set up a syncing set up with those two plugins using multi-sync package.

Thanks, doctorMo. The principles are clear. Is there an available howto?

---

### Post by DoctorMO on 2007-12-12
Not that I know of, it's more of a stack all the bits together, sacrifice a lamb to the great gods and cross your fingers.

If you hold onto your pants we can see about getting blackberry support built into the next version of ubuntu.

---

### Post by saltydog on 2007-12-12
> **DoctorMO said:**
> Not that I know of, it's more of a stack all the bits together, sacrifice a lamb to the great gods and cross your fingers.

If you hold onto your pants we can see about getting blackberry support built into the next version of ubuntu.

I have sacrified more than one lamb, but gods don't seem to give me a chance.
Anything I can do to push/help blackberry support on ubuntu 08.04?

---

### Post by DoctorMO on 2007-12-15
> Anything I can do to push/help blackberry support on ubuntu 08.04?

Help program conduit, opensync and barry. Complain at RIM for not giving us spec's; researching the RIM usb protocol; gather existing information into one place (would be nice too)

---

### Post by alek01 on 2008-05-15
> **saltydog said:**
> I have sacrified more than one lamb, but gods don't seem to give me a chance.
Anything I can do to push/help blackberry support on ubuntu 08.04?

SaltyDog, It has been proven for a long while now, that god, gods and godesses have no power over digital machines. So save blood and prayers and read this [http://www.linux.com/feature/123251](http://www.linux.com/feature/123251) . It worked fine for me on Ubuntu 7.10. Now on Hardy I need to re-do the whole process. KitchenSync is a good coordinator of all these pieces and once correctly configured works everytime.

Best,

Alek

---

### Post by chipbennett on 2008-05-31
All,

I have written a bit of a how-to for synchronizing my BlackBerry 8310 with KDE-PIM. [Here's the link]("http://www.chipbennett.net/wordpress/index.php/2008/05/synchronizing-a-blackberry-in-linux/"); would it be worthwhile starting a new thread to re-post the whole thing here?

Note to the poster who asked about synching with Evolution: the process is the same, only replace sync-kdepim with sync-evo2 (I think?). To do so, you'll need to install the appropriate opensync plugin (the opensync-plugin-evolution package, available in the repositories).

Please, let me know if the how-to is helpful. I found all the necessary information online, but it was fairly scattered and I tried to pull it all into one place.

---

### Post by anco on 2008-07-01
Just got a blackberry 8700 donated. my laptop is running Hardy and I'm wondering if I should just try the .deb for 7.10 as I cannot find anybody describing his setup on Hardy 8.04

Does anyone have .deb files for Hardy. I have no clue in compiling all this stuff myself following perfectly somebody's example is as far as I dare to go.

By the way I complained at RIM about no linux synchronizing software and explained them that they should do at least some thing for Ubuntu as that is one of the more popular desktop linux version. Just general replies is what they do...

Thanks,

---

### Post by chipbennett on 2008-07-01
> **anco said:**
> Just got a blackberry 8700 donated. my laptop is running Hardy and I'm wondering if I should just try the .deb for 7.10 as I cannot find anybody describing his setup on Hardy 8.04

Does anyone have .deb files for Hardy. I have no clue in compiling all this stuff myself following perfectly somebody's example is as far as I dare to go.

By the way I complained at RIM about no linux synchronizing software and explained them that they should do at least some thing for Ubuntu as that is one of the more popular desktop linux version. Just general replies is what they do...

Thanks,
The .DEB files for 7.10 seem to work just fine for 8.04. They are what I'm using for Kubuntu Hardy, anyway.

---

