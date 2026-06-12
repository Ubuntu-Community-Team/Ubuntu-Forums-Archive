---
title: "Questions about Auto-Updates"
date: 2009-06-08
forum: Server Platforms
---

### Post by oasisbhrnw on 2009-06-08
Hi all,

I just installed Ubuntu Server 9.04.  During the install there was an option for auto updates which I turned on.  My question is:  What commands can I use to find out info about my auto updates?  For instance, is there a way to tell when it has updated?  Is there a way to manually check for updates?  Any help is appreciated.

Robert

---

### Post by LepeKaname on 2009-06-08
I don't use the "auto-update" option, but you can use synaptic or aptitude to manually download and apply updates (they are very easy to use).

You can turn off your automatic-updates. Maybe this could help: [http://www.howtogeek.com/howto/ubuntu/configure-how-often-ubuntu-checks-for-automatic-updates/](http://www.howtogeek.com/howto/ubuntu/configure-how-often-ubuntu-checks-for-automatic-updates/)

Hope it helps

---

### Post by cariboo on 2009-06-09
With Jaunty server, when you log in remotely, it will tell you on screen if there are any updates available. Jaunty is setup to install security updates as they are available, while for other updates you will only get a notification once a week.

---

### Post by Interpreter on 2009-06-09
Mine says 0 security updates needed, but 1 package can be updated..and ah hm how do i do that?

The server manual tells me how to disable/enable a variety of updates, the use of screen and what not, but I can't for the live of me seem to find a simple command to tell it to go ahead and "update that one package"

I suppose thee is one though, rooite?

Thanks in advance.

---

### Post by LepeKaname on 2009-06-09
If you want to use aptitude:

sudo aptitude
press "u" to update package list.
then press "shift-U" (U upper case)
This is to specify to select all available upgrades.
Then, press "g", this will show you a screen before proceeding to install. 
You can select there what to install and what not to install. For example, over the package press 
":" to deselect a package for installation.
"-" remove that package (uninstall)
"_" purge package (uninstall and remove config files)
"+" install
If aptitude is telling you that you have some broken packages, then press "!" or ("." or ",") to navigate other alternatives to fix the problem.
After that, just press "g" again and will install what you selected.
Aptitude is really easy to use... check some tutorials...

---

