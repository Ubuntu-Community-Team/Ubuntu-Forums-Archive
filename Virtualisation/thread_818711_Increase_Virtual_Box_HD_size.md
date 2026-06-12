---
title: "Increase Virtual Box HD size?"
date: 2008-06-04
forum: Virtualisation
---

### Post by iheartubuntu on 2008-06-04
I have an XP setup running in VB... Is there any way I can increase the size of the XP virtual drive? I need more space! Thanks. I set it originally to expand when needed.... its not expanding.

---

### Post by ptempel on 2008-06-04
Looks like you need to make a new virtual disk image (vdi) and use a utility to clone the files from the old image to the new larger one.  Here's a link about it:

[http://forums.virtualbox.org/viewtopic.php?p=24053&sid=de1fd28e86b709c026271d8822ce3531](http://forums.virtualbox.org/viewtopic.php?p=24053&sid=de1fd28e86b709c026271d8822ce3531)

the link it refers to is in German.  Never tried this myself.  Would be curious to see how it works for you.

---

### Post by ptempel on 2008-06-04
Found a better link:

[http://forums.virtualbox.org/viewtopic.php?t=1878](http://forums.virtualbox.org/viewtopic.php?t=1878)

that copies the stuff from the old vdi to the new vdi using the selfimage utility in windows.

---

