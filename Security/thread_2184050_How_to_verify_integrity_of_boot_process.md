---
title: "How to verify integrity of boot process?"
date: 2013-10-27
forum: Security
---

### Post by phoenix1963 on 2013-10-27
I already have a Live-USB that I use to run chkrootkit on my main system.

Is there a similar way to check the integrity of the files used to boot from a Live-USB?

Thanks,
phoenix1963

---

### Post by JKyleOKC on 2013-10-28
Investigate the tripwire program. You use it immediately after a clean install, before connecting to the internet; it creates hash codes for every critical program and saves them. Best practice is to copy that set of hashes to read-only memory such as a CD. You then run the program daily, with its --check option, to verify that nothing has changed. After each legitimate system update, you allow the known changes via interactive dialog with the daily report, and create a new read-only file to use.

It's not absolutely foolproof but will catch most infections so long as you're careful about authorizing changes. I used it for years before deciding that it was overkill for my needs...

---

