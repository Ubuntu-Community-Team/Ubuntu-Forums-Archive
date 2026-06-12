---
title: "Wine [Access Denied]"
date: 2011-01-28
forum: Wine
---

### Post by feme on 2011-01-28
Hello guys, I've a problem with wine when I try to install Call Of Duty: world at war in ubuntu. I mounted an ISO Image in a virtual drive and I searh the installer and I right-click open with wine on setup.exe. But the problem is that the wine says 'Access Denied'. Any solution?
I read that it's a problem of ubuntu, not of wine I try what says [this article]("http://www.clockworkhare.com/2010/07/penguin-post-how-to-install-starcraft-2-on-linuxwine-if-you-get-weird-permissions-issues.html") but wine keep saying it.

Thanks..

Off: sorry if my English isn't good..

---

### Post by cogadh on 2011-01-31
Run the installer from the terminal, you won't have this problem:
```
cd /path/to/mounted/iso
wine setup.exe
```
Obviously replace the path I typed with the correct one.

---

