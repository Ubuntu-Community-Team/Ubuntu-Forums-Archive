---
title: "wine has no menu items, installed programs, no menu items anywhere"
date: 2018-04-14
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2018-04-14
There is a 'wine' main category only and it is entirely empty.
I have installed several programs,, none appear.
I installed  wine 3.0

---

### Post by sdowney717 on 2018-04-14
I really expect no solution to this, as it is a long standing issue with ubuntu.
And the problem has never gone away for me in prior releases either.

[https://bugs.launchpad.net/classicmenu-indicator/+bug/1289801](https://bugs.launchpad.net/classicmenu-indicator/+bug/1289801)

Wine menu items work fine in Mint. When you install a program, they show up in the menu listing, without needing to go through hoops.

I am sure people know about this, I am not alone here. Must be the right people dont care enough to resolve the problem.

---

### Post by Claus7 on 2018-04-14
Hello,

I do not know exactly if this:
[https://ubuntuforums.org/showthread.php?t=650738&page=3&p=10358697#post10358697](https://ubuntuforums.org/showthread.php?t=650738&page=3&p=10358697#post10358697)

will solve your problem, as it is an old post, yet you might find it helpful. I searched my ubu-box, which is the ubuntu development release at the time, and I was able to find:
gnome-flashback-applications.menu file  (similar to the one from the old post) which is under:
.config/menus folder [edit]

If you check it you might be able to restore your menus.

Regards!

---

### Post by sdowney717 on 2018-04-14
> **Claus7 said:**
> Hello,

I do not know exactly if this:
[https://ubuntuforums.org/showthread.php?t=650738&page=3&p=10358697#post10358697](https://ubuntuforums.org/showthread.php?t=650738&page=3&p=10358697#post10358697)

will solve your problem, as it is an old post, yet you might find it helpful. I searched my ubu-box, which is the ubuntu development release at the time, and I was able to find:
gnome-flashback-applications.menu file  (similar to the one from the old post) which is under:
.config.menus folder 

If you check it you might be able to restore your menus.

Regards!

applications.menu does not exist
Thanks for trying.

---

### Post by Claus7 on 2018-04-15
Hello,

you are welcome. Please verify that you went in the right folder, since I had made a typo (which is already corrected) in the folder name. Don't you have any other folders-files there that include names with list of -available- applications?

Since I'm using flashback session, our files might be different. 

I suppose that specifying your session might be helpful for other users as well.

Regards!

---

### Post by mc4man on 2018-04-15
Was going to ask what session but ^ post already did.
From here the repo wine-stable is useless, whoever is not maintaining should quit..

Going with the builds from here which at least saw the usefulness of inc. the various wine .desktop files
[https://launchpad.net/~zorinos/+archive/ubuntu/wine-testing](https://launchpad.net/~zorinos/+archive/ubuntu/wine-testing)
(- one could add the missing files for repo installs..

---

### Post by sdowney717 on 2018-04-16
> **Claus7 said:**
> Hello,

you are welcome. Please verify that you went in the right folder, since I had made a typo (which is already corrected) in the folder name. Don't you have any other folders-files there that include names with list of -available- applications?

Since I'm using flashback session, our files might be different. 

I suppose that specifying your session might be helpful for other users as well.

Regards!

applications.menu does not exist either in that folder or doing a file search.
But the 2 folders do have wine names of apps with identical looking content

I am running stock standard ubuntu development version.

UPDATE editing, for some reason wine menu entries exist today, after doing a system update. I just looked and the HotCPU test program is there.
However it is just all shoved into the main wine folder, so no distinction. Does that mean all installed programs will simply be jumbled together under the wine menu?
I also thought I had installed more windows programs than the one.

---

### Post by Claus7 on 2018-04-21
Hello,

> **sdowney717 said:**
> applications.menu does not exist either in that folder or doing a file search.
But the 2 folders do have wine names of apps with identical looking content

I am running stock standard ubuntu development version.

UPDATE editing, for some reason wine menu entries exist today, after doing a system update. I just looked and the HotCPU test program is there.

nice!

> **sdowney717 said:**
> 
However it is just all shoved into the main wine folder, so no distinction. Does that mean all installed programs will simply be jumbled together under the wine menu?
I also thought I had installed more windows programs than the one.

If I understood correctly, you have all your wine programms under the same menu. That's pretty normal. In case you have doubts about the programms installed and showed up you could search a little bit more to find any names of applications in the files you have in your posted pictures. Also, now that you have your wine menu back, you could try and see if a new installed program would show up. I do not expect that installing a wine program would appear somewhere else instead of the wine menu, if this is what you mean.

Regards!

---

