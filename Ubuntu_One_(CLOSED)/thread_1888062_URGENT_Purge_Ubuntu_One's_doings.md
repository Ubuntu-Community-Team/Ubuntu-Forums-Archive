---
title: "URGENT: Purge Ubuntu One's doings"
date: 2011-11-28
forum: Ubuntu One (CLOSED)
---

### Post by jaywhy13 on 2011-11-28
I installed Ubuntu one some time ago... now I realize that it has appended the suffix .u1conflict to all my DEV files under a folder that I chose to sync. Now apart from this being TERRIBLY undesirable... how do I UNDO all of that madness. My SVN folders have been suffixed and all my php files and config files. I need to urgent undo this madness.

---

### Post by *^kyfds( on 2011-11-28
> **jaywhy13 said:**
> I installed Ubuntu one some time ago... now I realize that it has appended the suffix .u1conflict to all my DEV files under a folder that I chose to sync. Now apart from this being TERRIBLY undesirable... how do I UNDO all of that madness. My SVN folders have been suffixed and all my php files and config files. I need to urgent undo this madness.

sorry, i'm a newbie.

are you talking about a filesystem error caused by syncing your folders?
or an error in the files stored online?

---

### Post by jaywhy13 on 2011-11-30
Found a solution.. sorry that this question is actually re-asked. My problem was I was using UbuntuOne on windows so no fancy commands. I used MinGW32 and ran the following commands outside my NetBeansProjects directory.


$ for i in $(find . -iname "*.u1conflict"); do j=`echo $i | sed 's/\.u1conflict//g'`; echo "renaming $i $j; mv $i $j; done

Hope this helps someone.

---

### Post by coldraven on 2011-11-30
For those who prefer a GUI then install Krusader and use File>Multi Rename.
You can preview your renaming before making permanent changes.

---

