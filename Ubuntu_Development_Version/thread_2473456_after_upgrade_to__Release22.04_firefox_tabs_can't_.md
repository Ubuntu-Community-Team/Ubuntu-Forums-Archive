---
title: "after upgrade to  Release:	22.04 firefox tabs can't be move left or right"
date: 2022-04-05
forum: Ubuntu Development Version
---

### Post by hoboy on 2022-04-05
After upgrade to  Release:	22.04 firefox tabs can't be drag left or right.

---

### Post by ajgreeny on 2022-04-05
Is your jammy install fully upgraded and which version of firefox do you currently have?

My bet is that the upgrade changed Firefox to the default in jammy which is the snap version. I can't help with details of that as all snap infrastructure has been removed from my jammy installs, none of them the standard gnome Ubuntu. I now download Firefox as the .tar.gz version from Mozilla and run it from the executable file in the extracted archive. This self upgrading so no worries about it becoming outdated.

I'm not sure about moving tabs as I seldom have enough open that I need to move them.

---

### Post by hoboy on 2022-04-05
I am using firefox 98.0.2 (64) well I have used full upgrade, but something went wrong 
I had to redoo it

---

### Post by guiverc on 2022-04-05
I can move my firefox tabs without issue, however I'm using Xorg & the LXQt desktop.

I suspect you're using Wayland?  and not Xorg.   Is that true?

You can file a bug with `ubuntu-bug firefox`   (at least I can; I'll get asked if I want to file the bug against the *deb* package or *snap* package even though the *deb* package is only the *stub* that loaded the *snap* package)

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by hoboy on 2022-04-05
My godness how do I check I suspect you're using Wayland? and not Xorg. Is that true?

---

### Post by hoboy on 2022-04-05
I have changed to  Xorg is is working

---

### Post by guiverc on 2022-04-05
Please file a bug about the issue.. 

Either earlier today, or yesterday I noted a reddit user (*I think*) who reported a like issue to what you describe; and the fact that it's working in Xorg (*as it does for me*) & you, but not when you're using the Wayland default is the sort of detail that is wanted on bug reports.

Ubuntu *jammy* is currently in ***beta***, where fixes are still easier to implement, than post-release time.. ie. where bugs are reported now, they'll have a far higher chance of getting fixed before release, as post-release they will often get fixed in the next release (ie. 22.10) and only back-ported to older releases where it's a security issue (*this type of issue wouldn't qualify*).

---

### Post by corradoventu on 2022-04-05
[https://bugzilla.mozilla.org/show_bug.cgi?id=1710344](https://bugzilla.mozilla.org/show_bug.cgi?id=1710344)
[https://bugzilla.mozilla.org/show_bug.cgi?id=1748873](https://bugzilla.mozilla.org/show_bug.cgi?id=1748873)
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1964541](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1964541)

---

