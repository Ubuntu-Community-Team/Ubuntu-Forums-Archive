---
title: "does apparmor work against codecs, flash player, videodriver?"
date: 2009-01-07
forum: Security
---

### Post by q.dinar on 2009-01-07
hello.
does apparmor work against these:
codecs, flash player, videodriver?

i have seen there that it is possible to lock directories for firefox, pidgin and xchat. but if i want to use firefox with flash player enabled, can i lock flash player also? i think yes. then can i lock videocodecs if i install them?

by the way: are codec packages in the repository open-source (i.e. can be checked against vulnerability (and probably are checked))?

where is flash player binary file that i will need to know to generate general profile for it? i can look binary file name of standart packages in synaptic with right click -> files. where can i see flash player's files?
can i lock videodriver with apparmor?
can i lock ports with apparmor?
does apparmor work separate way with every user? i think yes and think that probably i cannot use apparmor against videodriver because it does not run separately for every user (and [think that] apparmor just does not work on that level). does codecs run separately for every user? - i think yes.


28th of january:
see also [AppArmor Support Thread](http://ubuntuforums.org/showthread.php?t=1049698) .

---

### Post by bodhi.zazen on 2009-01-07
Apparmor works against any and everything.

I can not tell from your post exactly what you are wanting.

apparmor does not directly have a separate profile for each user. You can make a hard link and have a separate profile for each hard link.

IMO the best way to learn Apparmor is to start to use it. It is intimidating at first but after 30-60 minutes you should have a fairly good understanding of how to use it. See the sticky on these forms.

For what you are asking SELinux *may* be a better option as users on selinux have "roles".

---

