---
title: "How often do you need to delete all your config files to fix problems?"
date: 2010-02-14
forum: The Cafe
---

### Post by lovinglinux on 2010-02-14
I guess most people will agree that clean installs are better than upgrades, to avoid problems when installing a new Ubuntu release. But I have been thinking about the problems resulted from keeping config files across several upgrades. 

I have no doubt that keeping a separate home partition saves a lot of time configuring the system, not to mention keeping personal documents, e-mails, Firefox profiles, keyrings, gpg keys and other important data. When using a separate home and *dpkg --get-selections*, I can have my system back the way it was in less than 2 hours. But is it really worthy to keep all your config files when installing a new Ubuntu version?

When I installed Karmic for the first time I experienced a mysterious excessive CPU usage, so I decided to delete all my config files from home. Problem solved. Two days ago, I installed KDE 4.4 and experienced several crashes in the window decorator and plasma, along with several glitches in plasma functionality. After deleting ~/.kde, problems were solved.

So I'm wondering how often other users need to take such "drastic" measures to fix serious problems after upgrades? Which .folders do you delete?

Do you prefer to start with a clean slate? If yes, then what folders do you backup first, to restore later, after the upgrade?

I always backup all my settings before installing a new Ubuntu version. I have a separate home, but I like to keep backups of all settings in case something really bad goes wrong. Additionally I make regular backups of the following folders, since they contain important data, not only settings:

~/.ssh
~/.gnupg
~/.gnome2/keyrings 
~/.kde/share/apps/kwallet
~/.kde/share/apps/kmail
~/.mozilla/firefox

All my personal documents are stored in separate partitions and are symlinked to home. This way I can make my home partition really small (only 9Gb), since it only need to store the hidden configuration folders.

---

### Post by Hetor on 2010-02-14
Never.

---

### Post by GeneralZod on 2010-02-14
> **Hetor said:**
> Never.

Same here.  Needs a poll :)

Incidentally, most KDE projects treat a lack of backwards compatibility of config files as a bug (in some projects, a blocker), so it would be helpful if instead of just deleting them, bug reports could be filed.  I'm not sure if Plasma is one such project, but it has a stable API and ABI now so it *really* should be robust in the face of upgrades.

---

### Post by ajgreeny on 2010-02-14
I've never done a distro upgrade but always a clean install, but when I restore my files and folders from the old /home backup, or now with a separate /home partition, just install the new /root partition, I tend to only keep the config files and folders for things that also keep personal files in them, eg ~/.mozilla and same for thunderbird, ~/.purple, ~/.openoffice.  Those are the most important ones for me, other people will no doubt have others that are similarly important to them.  I never bother with things like ~/.gconf, etc etc as that is so easy to reset, and I tend to change very little in them in any case

---

### Post by tjwoosta on 2010-02-14
When reinstalling I always do clean installs, I just backup configs that I know Ill want. But If I have a problem like you mentioned I usually get to the bottom of it rather then just delete everything.

---

### Post by falconindy on 2010-02-14
Never, because I choose my software wisely. The majority of my config files are hand written and maintained.

---

### Post by bruno9779 on 2010-02-14
I never need it when running, but when i backup my home to make a new release install, I remove all the config files (except for .bashrc and /.thunderbird)

---

### Post by Yes on 2010-02-14
I may have had to after an Ubuntu update once, but I never have to in Arch.

---

