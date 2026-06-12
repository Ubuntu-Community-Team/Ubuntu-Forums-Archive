---
title: "Does Wine survive distro upgrades/reinstalls?"
date: 2009-01-29
forum: Wine
---

### Post by Noblacktie on 2009-01-29
Hi guys,

I'm thinking of running Steam and my collection of Steam games via Wine but would like to find out if it's possible to carry over programs installed in Wine over to new versions of Ubuntu.

This is because games like TF2 and the like will be downloading gigabytes worth of updates just to get up and running with the latest versions and I don't want to bother if Wine breaks after each distribution upgrade/change.

Any info will be greatly appreciated!

---

### Post by 0bso on 2009-01-29
I don't know about wine itself but you can back up the steamapps folder (drive_c/Program Files/Steam/steamapps). That way if you do have to reinstall steam you just have to download the client and then copy over the old steamapps folder. It will keep all your games and login info.

---

### Post by Brynster on 2009-01-29
Its never been problematic to me.

However your mileage may vary as they say. Many because at upgrade time it seems to be 50/50 split on the boards about congratulatory post saying upgrade process was brilliant and the other option of upgrade borked my system......

---

### Post by YokoZar on 2009-01-29
Wine's virtual windows installation is kept in a hidden directory in your home folder, at ~/.wine.  As long as you bring that folder with you, you can use all the Wine applications you install wherever you like - after removing/upgrading Wine, or even upgrading the entire system.

If you're erasing an entire disk and reinstalling, the only thing you need to do to preserve Wine is back up the /home folder; after that, just copy the old home folder into the new installation, reinstall Wine and it'll pick up where it left off.  As a rule, Ubuntu system updates will never touch anything inside the home folder -- this, in turn, makes it very safe to upgrade (or downgrade) Wine.

---

### Post by Noblacktie on 2009-01-30
Thanks for the confirmation, guys.

I have a separate /home partition that gets backed up and stays intact throughout OS upgrades/installs so as long as Wine keeps Steam in there, everything is super.

TF2 in Linux, here I come!

---

