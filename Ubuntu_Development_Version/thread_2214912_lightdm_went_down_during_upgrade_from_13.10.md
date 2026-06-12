---
title: "lightdm went down during upgrade from 13.10"
date: 2014-04-03
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2014-04-03
I did a upgrade today using the debian method of changing the sources and running apt-get dist-upgrade
i started the upgrade and came back to it a little while later and i could not get the desktop back
i was able to get to a tty (ctrl+alt+f1) i figured xscreensaver was acting up, nope not the issue
i decided to just stop the lightdm service, not running
tried to start it, failed
check pid of apt-get, it was running still, probably asking for user input as i had no way to provide input i killed the process
i tried to instal updates with apt-get it told the to run dpkg --configure or something i did and got it finished upgrading
i did not remove my ppas or anything
once that was done i did a autoremove and rebooted and everything as good

anyone know if lightdm crashes when upgrading the recommended way, someone should check on that, i have always had god luck with the debian method, even done upgrades over ssh like that without issue

this system has a phenom II 965 and a GT 430 using the nvidia driver

---

### Post by 23dornot23d on 2014-04-03
I almost always upgrade by changing the source.list then using aptitude safe-upgrade then aptitude dist-upgrade

If the lightdm stops ........... then I install kdm ........ and run that ..........

But there have been some issues in the past with lightdm - as regards it accepting input - not sure if that got resolved yet
there was a thread not so long back on it .......... will look now login - problem [http://ubuntuforums.org/showthread.php?t=2209080](http://ubuntuforums.org/showthread.php?t=2209080)

 ........ there is one here also where they have moved the lightdm config files ( need this info for something else setting resolution )
 - [http://ubuntuforums.org/showthread.php?t=2205637](http://ubuntuforums.org/showthread.php?t=2205637)

There is also another thread on synaptic not working here ........ [http://ubuntuforums.org/showthread.php?t=2210892](http://ubuntuforums.org/showthread.php?t=2210892)

ok just taken a snapshot and will upgrade ....

After the upgrade there are a few problems - sound not working and synaptic not working 
if I run synaptic from Unity kde or gnome-shell ( its from a terminal ) ....... other than the sound which has gone. ( dummy output only now )

---

