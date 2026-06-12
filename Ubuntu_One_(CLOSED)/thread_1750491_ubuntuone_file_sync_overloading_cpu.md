---
title: "ubuntuone file sync overloading cpu"
date: 2011-05-05
forum: Ubuntu One (CLOSED)
---

### Post by glendavee on 2011-05-05
After upgrading to 11.04 I find that if I launch ubuntuone my machine immediately slows to a crawl and there is intense hard drive activity.This persists for hours. Only solution so far is to close ubuntuone and remove it from list of startup applications. I have made no changes to the files marked for ubuntuone syncing, and everything worked fine in 10.10. I've seen a couple of references to this problem, but can't find any solution.

---

### Post by demilord on 2011-05-06
I find Ubuntu 11.04 anyway a bit unstable and unuseable... there are to much quircks in it for me atm... I downgraded back to 10.10 which is in my opinion a definition of a good stable release and wait for some months till 11.04 is stable enough for me..

BTW you can file a bug report at their launchpad if you wish

---

### Post by demonboy on 2011-05-06
For my sake (and anyone else with the same problem) could you post your findings on this issue? I have exactly the same problem and even though I disabled it from start-up, Ubuntu One appears to re-sync of its own accord. I bought a new laptop with an i5 processor and Natty is running like Windows 95 when Ubuntu One kicks in. It gets stuck on the same file and those annoying pop-up bubbles keep telling me that same file is sync-ing.

I found this command to purge Ubuntu One:

```

apt-get remove --purge python-ubuntuone-client

```

... but I'm unsure exactly how much it gets rid of. I'd really like to get Ubuntu One working rather than delete it but because it grinds my laptop to a halt I'm very tempted to get rid of it and just use Dropbox instead.

---

### Post by Lylex11 on 2011-05-15
I seem to have the same issue. HP-g60t with AMD64 Natty. On start up, I get a pop-up saying so many files are being synced (though these should have been synced already) and the U1 launcher icon shows a progress bar over it that never seems to progress. After a while desktopcouch uses 99% of cpu. The is solved by opening U1 and clicking on "disable sync". Or a hard reboot. This behaviour seems a little erratic, but happens on most boots.

I saw on the U1 facebook page that a syncing database issued had recently been solved, so I'm hoping it's solved. But as I write the progress bar is not progressing.

---

### Post by nicognu on 2011-07-06
After upgrading 11.04, i have same issue.
So I have:

[LIST]
[*]remove ubuntuone client packages
[*]drop folder ~/.local/share/ubuntuone
[*]reinstall ubuntuone client
[/LIST]

=> no more file sync overloading

Empirical method, but it works :)

---

