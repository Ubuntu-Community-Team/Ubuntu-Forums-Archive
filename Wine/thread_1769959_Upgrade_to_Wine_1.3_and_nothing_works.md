---
title: "Upgrade to Wine 1.3 and nothing works?"
date: 2011-05-28
forum: Wine
---

### Post by HandLotion on 2011-05-28
I'm running Ubuntu Lucid. I decide to upgrade wine 1.2 to Wine 1.3 beta. I noted that the upgrade deleted wine 1.2 as part of the upgrade. Now nothing runs under wine - not even the wine config program.

Nevermind. A system reboot fixed my issue.

---

### Post by bobwyajnr on 2011-05-30
[q4wine]("http://sourceforge.net/projects/q4wine/") is a useful Qt utility that will show all the Wine-associated Linux processes are running on your system (it's in the repositories I think). Wine should update, without a reboot, if there are no active Wine processes running (since it runs entirely in userspace). q4wine lets you kill off all the Wine processes - which are pain to find manually with the likes of: **ps**, **pkill** or the system monitor GUI.

Can you mark this thread as **[SOLVED]** to stop other people wasting their time reading it! :popcorn:

Bob

---

