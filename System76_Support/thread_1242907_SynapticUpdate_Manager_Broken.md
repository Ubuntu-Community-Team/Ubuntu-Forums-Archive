---
title: "Synaptic/Update Manager Broken"
date: 2009-08-17
forum: System76 Support
---

### Post by AlexInBlack on 2009-08-17
I'm running Xubuntu on a daru3. I'd booted Xubuntu for the first time in a week and the first thing I did was to use the Update Manager. However, something broke, so that neither Synaptic or the Update Manager will launch.
This had happened to me before and I either fixed it/reinstalled, but my memory and Google-fu failed me this time around.

If it helps, the only non-official repos I have are System76's and Medibuntu.

Any help/input would be appreciated. Thanks.

---

### Post by gila_monster on 2009-08-17
Try running synaptic from a terminal and let us know what errors it shows.

---

### Post by Lee_Machine on 2009-08-17
In a Terminal try:

sudo apt-get update

then

sudo apt-get upgrade.

You should also run

sudo dpkg --configure -a

---

### Post by AlexInBlack on 2009-08-18
I've already tried those commands, but to no avail.
After another restart, fsck failed and asks me to fix the filesystem manually. When I press Ctrl-D to continue a normal bootup and then login, a warning message pops up saying, "Your home directory is listed as '/home/alexinblack' but it does not appear to exist. Do you want to log in with the / (root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session."

When I click 'Yes', another message pops up saying, "User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

Yet another message follows after I click "OK": Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problems or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem."
The details show that essentially, none of the directories necessary can be created.

I then try logging in failsafe gnome, which fails, and shunts me into a failsafe xterm session.

This had happened to me before as well, but as before, I forget how to fix it.

Booting into an earlier kernel made no difference.

---

### Post by jdb on 2009-08-18
> **AlexInBlack said:**
> I've already tried those commands, but to no avail.
After another restart, fsck failed and asks me to fix the filesystem manually. When I press Ctrl-D to continue a normal bootup and then login, a warning message pops up saying, "Your home directory is listed as '/home/alexinblack' but it does not appear to exist. Do you want to log in with the / (root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session."

When I click 'Yes', another message pops up saying, "User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

Yet another message follows after I click "OK": Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problems or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem."
The details show that essentially, none of the directories necessary can be created.

I then try logging in failsafe gnome, which fails, and shunts me into a failsafe xterm session.

This had happened to me before as well, but as before, I forget how to fix it.

Booting into an earlier kernel made no difference.

The "644 permissions" thing is because the root directory in Ubuntu isn't for logging in & has the wrong permissions.
The easiest thing is to boot from a live CD.

Your main problem is your home directory not existing.

If it is on a different partition it may not be mounting due to corruption.
If that's the case and fsck won't fix it, you'll  have to restore your home directory from backup.

jdb

---

