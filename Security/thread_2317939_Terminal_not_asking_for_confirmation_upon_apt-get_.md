---
title: "Terminal not asking for confirmation upon apt-get install"
date: 2016-03-21
forum: Security
---

### Post by zac13 on 2016-03-21
Upon booting this morning, Firefox started up on it's own and checked compatibility for extensions. This has never happened before, so i wanted to run a clamav scan on my system. Clamav is outdated, and i didn't feel like going through the update process, so i was going to be lazy and just purge and reinstall the program.

After apt-get purge clamav, the process confirmed itself, rather than my having to input "y" and "enter" to purge, and then install.

Why has this change occurred in the terminal? Has my system been compromised? I'm a bit of a noob, having only used ubuntu for about 12 months, so I am unsure...

---

### Post by Doug S on 2016-03-22
I am not aware that not asking for confirmation when installing one package is a change. I thought it always behaved that way. It asks for confirmation when a bunch of additional packages are required, due to dependencies, which might have been the case the first time you installed clamav, but not this time.

---

### Post by ian-weisser on 2016-03-22
Doug S is correct.
apt-get has never asked for confirmation for installing or removing merely the packages you specity, since you already told apt to do precisely that action.
apt-get has always asked for confirmation for installs or removals beyond what you specify, protection against the unforeseen.

---

