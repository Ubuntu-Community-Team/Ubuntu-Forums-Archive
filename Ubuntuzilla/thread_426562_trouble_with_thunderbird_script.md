---
title: "trouble with thunderbird script"
date: 2007-04-28
forum: Ubuntuzilla
---

### Post by olvlo on 2007-04-28
Hi; when installing the firefox script (installnewfirefox.sh), everything went smooth, but after trying to do the same with the thunderbird one, I get an error message and the installation stops:


[I]Backing up old thunderbird preferences

ln: invalid option -- T
Try `ln --help' for more options
Previous command did not complete succesfully. Exiting
[/I]
This was just after asking to make (or skip) a backup of  the previous profile at ./mozilla-thunderbird

Am I doing something wrong or what? Can anybody offer some advice? thanx!

---

### Post by nanotube on 2007-04-28
> **olvlo said:**
> Hi; when installing the firefox script (installnewfirefox.sh), everything went smooth, but after trying to do the same with the thunderbird one, I get an error message and the installation stops:


[I]Backing up old thunderbird preferences

ln: invalid option -- T
Try `ln --help' for more options
Previous command did not complete succesfully. Exiting
[/I]
This was just after asking to make (or skip) a backup of  the previous profile at ./mozilla-thunderbird

Am I doing something wrong or what? Can anybody offer some advice? thanx!

hmm... what version of ubuntu are you running? ln definitely should have the -T option in it. could you look and see also what version of the script you are running (open it in text browser and look at the top). also, please post the output of "ln --help" (i want to make sure it lists the -T option).

anyway, let's go from here. :)

---

