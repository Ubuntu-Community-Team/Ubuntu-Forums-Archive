---
title: "Revo Uninstaller [free ware]"
date: 2009-05-06
forum: Wine
---

### Post by StormRoBoT2 on 2009-05-06
guys just wan to share with you guys about this application, i install this using wine 1.1.16.

the reason i install this is because, some time when u try to un-install using wine it just dont work.

so i install this and when i wan to remove program i just use this tool to remove it

---

### Post by asdfoo on 2009-05-06
> **StormRoBoT2 said:**
> guys just wan to share with you guys about this application, i install this using wine 1.1.16.

the reason i install this is because, some time when u try to un-install using wine it just dont work.

so i install this and when i wan to remove program i just use this tool to remove it

uninstalling is a low priority in Wine

if you want to keep things simple, use one application per prefix and remove the prefix if you nolonger want to use the application

---

### Post by cogadh on 2009-05-07
Uninstalling is not a low priority at all (whatever gave you that idea?) and the only apps that have serious issues with the Wine uninstaller app are those that were [installed via a MSI file]("http://bugs.winehq.org/show_bug.cgi?id=9114"). In fact, fixing that particular bug is one of the milestones that needs to be met before the Wine 1.2 release.

Setting up a single "bottle" for every application is a huge waste of space. Yes, there are certainly occasions where you would definitely want to do that (installing Office or Steam springs to mind), but to do that for every individual app is just wasteful.

StormRoBoT2, this is an excellent recommendation, especially for those apps installed via an MSI file, as I mentioned above. Thanks for the "heads up".

---

### Post by asdfoo on 2009-05-07
> **cogadh said:**
> Uninstalling is not a low priority at all (whatever gave you that idea?) and the only apps that have serious issues with the Wine uninstaller app are those that were [installed via a MSI file]("http://bugs.winehq.org/show_bug.cgi?id=9114"). In fact, fixing that particular bug is one of the milestones that needs to be met before the Wine 1.2 release.

Setting up a single "bottle" for every application is a huge waste of space. Yes, there are certainly occasions where you would definitely want to do that (installing Office or Steam springs to mind), but to do that for every individual app is just wasteful.

StormRoBoT2, this is an excellent recommendation, especially for those apps installed via an MSI file, as I mentioned above. Thanks for the "heads up".

bottle is the term that the commercial product crossover uses.

Wine uses prefixes.

From comments I've read on the Wine forum and bugzilla, uninstaller bugs are not as big a deal as installer or other bugs that prevent people from using their software.

---

### Post by cogadh on 2009-05-07
Bottles... prefixes... its all the same thing and debating the semantics of that particular term is pointless.

I don't know who would have said that, but they were wrong. Uninstalling apps is just as important to Wine's development as installing them. Like I said, fixing the MSI uninstall problem is one of the [milestones for the 1.2 release]("http://bugs.winehq.org/buglist.cgi?bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&product=Wine&target_milestone=1.2.0&order=bugs.bug_severity"), along with fixing the issue with uninstalls leaving behind menu shortcuts (the only other uninstall problem Wine still has).

---

### Post by Trackieman on 2009-08-19
Even if you had installed that on a computer running windows you would probably find the uninstall to be broken.

---

### Post by NightMKoder on 2009-08-20
> **cogadh said:**
> Bottles... prefixes... its all the same thing and debating the semantics of that particular term is pointless.

I don't know who would have said that, but they were wrong. Uninstalling apps is just as important to Wine's development as installing them. Like I said, fixing the MSI uninstall problem is one of the [milestones for the 1.2 release]("http://bugs.winehq.org/buglist.cgi?bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&product=Wine&target_milestone=1.2.0&order=bugs.bug_severity"), along with fixing the issue with uninstalls leaving behind menu shortcuts (the only other uninstall problem Wine still has).

True, but if you remember correctly, it took 15 years to get to stable 1.0 . The true fact of the matter is that wine devs care more about having apps install and run. If someone has some free time/is learning about wine these dogfood bugs will get fixed. Or if some app actively uses the functionality.

For example: bug 421 (DIB engine) is a necessary fix, but its not a priority for anyone since there are mechanisms in place to make it at least slightly work.

---

