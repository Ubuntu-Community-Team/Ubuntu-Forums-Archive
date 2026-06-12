---
title: "Few questions before upgrading to Ubuntu 15.10"
date: 2015-10-18
forum: Ubuntu Development Version
---

### Post by aljosa2 on 2015-10-18
Hi all,
I always perform a clean installation of the new Ubuntu version... I will do the same next week too. But in order to help a long-distance friend, I need to know few things before he upgrade his Ubuntu 15.04 to 15.10:

[I]- is there a need for some special command for X.Org Server, Mesa and kernel upgrade?

- will everything (Ubuntu settings, downloaded application Google Chrome, restricted extras, Skype) remain the same after upgrading from one release to another (fortunately, he don't use any PPA)?

- his Nvidia driver (Optimus notebook) will automatically receive the update too, no need to select the new driver inside additional drivers?

- I would like to avoid eventual [black screen of death]("http://ubuntuforums.org/showthread.php?t=2293682"), so this is the most important question: what will happen with the current prime-switch Intel? will it automatically change to Nvidia?[/I]


Thanks in advance for your replies :)

---

### Post by grahammechanical on 2015-10-18
My advice? Tell your friend to

1) Revert the OS back to default as much as possible. I would expect Chrome & Skype to be outside the planning of the Ubuntu developers who work out the upgrades process for us.
2) Revert to using an open source video driver. I would suggest the Intel one. It may not apply to your friend's machine but Ubuntu 15.10 will come with the latest stable proprietary video drivers and the latest drivers often drop support for older graphic adapters. As a matter of policy I would upgrade running on an open source video driver.

The choice is: spend a little time afterwards re-installing certain software and drivers or spend a lot of time afterwards trying to fix the black screen problem. The upgrade should not wipe the configuration files of Chrome or Skype. So, I would expect the applications to pick up their settings once re-installed. 

3) Get him to practice going into recovery mode and using the Resume option. Just in case he needs to do that to get to a working desktop.
4) Backup.

Regards.

---

### Post by zika on 2015-10-18
You will need boot-able CD/USB anyhow. So, before embarkin into either upgrade or install, do try 15.10 as on vanilla CD/USB on target machine and note any problem emerging so You could be prepared. No idea if there are some PPAs added on previuos install, guess not.
That test should be the most informative one and much more informative than our guesses because we do not have that piece of HW in front of us. Do install everything he needs so You could be sure it would work on (vanilla) install eventually.

---

