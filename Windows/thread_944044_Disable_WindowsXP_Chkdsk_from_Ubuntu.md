---
title: "Disable WindowsXP Chkdsk from Ubuntu?"
date: 2008-10-10
forum: Windows
---

### Post by aureliano on 2008-10-10
I have Windows XP on a seperate partition. It is stuck in a perpetual chkdsk: it's unskippable, and reboots when it completes.

Since I can access the windows partition in Ubuntu (the files anyway), is there anything I can do to disable Chkdsk from running at boot?

Using safe mode causes my system to freeze, and I can't use the recovery console (in college, windows disk at home).

Anyway, I downloaded Wine thinking I could use RegEdit to disable it, but I'm unable to edit the registry on the windows partition.

Any help would be really appreciated.

---

### Post by stinger30au on 2008-10-11
thats a worry.

id be checking the hdd for bad sectors

i suggest a free dos boot cd like this one to test it with

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by shaggy999 on 2008-10-11
I have ran into a problem similiar to this before. My solution was first to install a package that had some ntfs tools in it (I don't remember the name) and I told it to basically clear the 'dirty bit' on the NTFS partition. Then I had to boot w/ my windows CD and go into recovery mode and tell it to fix my hard drive. After rebooting it booted just fine.

---

### Post by aureliano on 2008-10-11
Thanks for the suggestions, guys. I managed to fix it (well, it boots but chkdsk still crashes) with chntpw. I edited the windows registry files using the Terminal, and disabled chkdsk from there.

For reference:
[http://home.eunet.no/pnordahl/ntpasswd/]("http://home.eunet.no/pnordahl/ntpasswd/")

---

