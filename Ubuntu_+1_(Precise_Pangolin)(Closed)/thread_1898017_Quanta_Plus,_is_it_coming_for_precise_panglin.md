---
title: "Quanta Plus, is it coming for precise panglin?"
date: 2011-12-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by irv on 2011-12-20
Quanta Plus is available on natty, maverick, and lucid but not for precise pangolin yet. Just wondering if someone is working on this one. It is not in the repository yet.
[ATTACH]209429[/ATTACH]

---

### Post by jbicha on 2011-12-20
No, quanta was abandoned a few years ago. It was never ported from kde3 and kde3 support has been dropped in Debian and Ubuntu.

---

### Post by irv on 2011-12-21
> **jbicha said:**
> No, quanta was abandoned a few years ago. It was never ported from kde3 and kde3 support has been dropped in Debian and Ubuntu.

It is still listed in the Software Center online. 
[ATTACH]209512[/ATTACH]
There is a problem with older packages that are no longer being worked on, they die by the wayside but are still showing up in the software center. It would be nice if someone would clean out the old abandon ones.

---

### Post by jbicha on 2011-12-21
If you look at the screenshot or the page a bit more closely, you'd see  that it shows that Quanta Plus is available for Natty but not Oneiric.

Perhaps a notice like the Problems section at [http://packages.qa.debian.org/k/kdelibs.html](http://packages.qa.debian.org/k/kdelibs.html)  could be added so that visitors are aware that that particular app for  whatever reason is not in the most recent stable release.

Not directly related, but there's also bug [887262]("http://pad.lv/887262") (about apps.ubuntu.com continuing to default to natty).

---

### Post by cariboo on 2011-12-21
There are still quite a few people using Quanta +, it's number 4431 of 201307 packages, according to  [http://popcon.ubuntu.com/by_inst](http://popcon.ubuntu.com/by_inst), the text version of Ubuntu popularity contest

---

### Post by irv on 2011-12-22
I guess when I posted the 3rd post in this thread I didn't take into consideration the fact that other users were still using this package on older releases of Ubuntu. I am still running 10.04 LTS on my server and could use it there, but will not be using it when 12.04 comes out. Maybe I will just keep my server at 10.04 until it runs its course.

---

### Post by Rog131 on 2011-12-22
[http://askubuntu.com/questions/66716/quanta-plus-not-supported](http://askubuntu.com/questions/66716/quanta-plus-not-supported)

Ubuntu 11.10. The Quanta is depending the deprecated KDE 3.5 libs ([https://bugs.launchpad.net/ubuntu/+source/kdelibs/+bug/794513](https://bugs.launchpad.net/ubuntu/+source/kdelibs/+bug/794513)). The Quanta was removed from the repositories when the KDE 3.5 libraries were removed.

The new Quanta with the KDE4/Qt4 didn't find the developers to do the upgrade.

The Quanta's KDE mailinglist archives: [http://lists.kde.org/?l=quanta&r=1&w=2](http://lists.kde.org/?l=quanta&r=1&w=2)

A topic (Any progress on Quanta for KDE 4?) : [http://lists.kde.org/?t=130763123700002&r=1&w=2](http://lists.kde.org/?t=130763123700002&r=1&w=2)

---

