---
title: "Reinstalled wine, no wine icons"
date: 2010-10-17
forum: Wine
---

### Post by dewdrop_world on 2010-10-17
Google directed me to [a prior thread]("http://ubuntuforums.org/showthread.php?t=1536265") with a similar problem -- that was resolved by enabling the wine menus using the main menu configuration. Mine is a little different, so I'm starting a new thread.

I had installed wine previously to use NaturallySpeaking, then uninstalled it sometime later due to stability problems (which turned out to be faulty RAM). Now the RAM is replaced and I reinstalled wine using the software center. It's running fine -- reinstalled NaturallySpeaking and it's working so far -- but the wine menu doesn't appear under applications.

The other thread also recommended reinstalling from the commandline, which I did...

sudo apt-get --reinstall wine1.2

This ran successfully but did not restore the wine menus.

So, what next? I don't mind creating the menus by hand but don't know the names of the executables. Specifically I need the wine configuration panel and the program loader. Anybody know?

I'm not confident of uninstalling and reinstalling wine -- how would that be different from the last reinstall?

Thanks --
James

---

### Post by dewdrop_world on 2010-10-17
Heh... that'll teach me to read a little further down the google results...

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

wine (program name)
winecfg

Silly me.

---

