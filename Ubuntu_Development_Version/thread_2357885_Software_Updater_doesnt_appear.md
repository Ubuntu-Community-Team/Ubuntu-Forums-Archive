---
title: "Software Updater doesnt appear"
date: 2017-04-07
forum: Ubuntu Development Version
---

### Post by linuxyogi on 2017-04-07
Hi, using 17.04. Problem is the software updater doesnt appear on its own. When I do sudo apt-get update && sudo apt-get upgrade packages get updated. Is this a known issue ?

---

### Post by deadflowr on 2017-04-07
What happens when you run
```
update-manager
```

---

### Post by linuxyogi on 2017-04-07
> **deadflowr said:**
> What happens when you run
```
update-manager
```

When I run update-manager from the command line I see no error messages. It launches, checks for updates and says "your computer is up to date".

I just finished updating from the command line before launching the update-manager.

I guess I will have to wait for the next set of updates to appear and see if update-manager launches or not.

I ran update-manager (from the terminal) again. There was no text whatsoever. Update manger launched as usual, checked for updates and found some updates. Please see screenshot. 
[ATTACH=CONFIG]274464[/ATTACH]

---

### Post by jbicha on 2017-04-07
Yes, it's a [known issue]("https://bugs.launchpad.net/bugs/1649709") before Ubuntu 17.04 is marked as final. It's mentioned in the [Release Notes]("https://wiki.ubuntu.com/ZestyZapus/ReleaseNotes") and I started a thread about it on this forum a few months ago.

But Ubuntu is in pre-release freeze so there won't be many updates until next Thursday.

---

### Post by linuxyogi on 2017-04-07
Thanks. I hope there will be fix next Thursday.

---

### Post by jbicha on 2017-04-07
It's not exactly fixed on Thursday, but it only affects the development releases of Ubuntu so Ubuntu 17.04 won't be affected after that date.

---

### Post by linuxyogi on 2017-04-07
Got it.

---

