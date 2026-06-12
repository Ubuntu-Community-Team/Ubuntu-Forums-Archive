---
title: "Steam issue"
date: 2010-07-07
forum: Wine
---

### Post by Speed Racer on 2010-07-07
I just installed steam via the steaminstall.msi (msiexec /a /path/to/msi/file) and now when I go to log onto my acct I am unable to type in the steam log in box. 

All the text just goes into other open windows

---

### Post by skinnyj on 2010-07-07
I searched support for anything, and the only thing I can say is that Valve doesn't have a Linux client available. The only things they have that support Linux are the dedicated servers for Half Life 1.

All I can say is that it may be a problem between Linux and the Steam client trying to read keyboard input, even with compatibility support running.

---

### Post by asdfoo on 2010-07-08
you have not mentioned which version of wine you are using, open a terminal and type 'wine --version', it should print wine-1.2-rc6

---

### Post by Espionage724 on 2010-07-09
I was able to start Steam with no issues on Ubuntu 10.04 x64 + Latest Wine from PPA.

I just downloaded the MSI, right-clicked it and ran with Wine Windows Loader, installed it like normal, let it update, logged in, no issues. I'm even downloading CS:S atm.

---

