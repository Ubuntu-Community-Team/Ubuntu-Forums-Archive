---
title: "Firefox reinstalls everytime I update"
date: 2010-03-03
forum: Ubuntuzilla
---

### Post by mercury7 on 2010-03-03
I have ubuntzilla installed, and I am happily running Mozilla Firefox 3.6.  But everytime I do sudo aptitude update; aptitude safe-upgrade it downloads and reinstalls the firefox3.5 and other files from the Ubuntu repository.  Help, how can I make it stop doing this?

Thanks for any help!

---

### Post by nanotube on 2010-03-04
> **mercury7 said:**
> I have ubuntzilla installed, and I am happily running Mozilla Firefox 3.6.  But everytime I do sudo aptitude update; aptitude safe-upgrade it downloads and reinstalls the firefox3.5 and other files from the Ubuntu repository.  Help, how can I make it stop doing this?

Thanks for any help!

/every/ time? or only when a firefox 3.5 update is available from the ubuntu repos?

the former is weird, the latter is expected, and harmless, behavior.

---

### Post by sleepee on 2010-03-04
i get the same issue, but like nanotube says, only updates are available...
but shouldn't ubuntu know that i have a newer version??
or isn't there a way to take out the firefox 3.5 updates and make them stop??

---

### Post by nanotube on 2010-03-04
> **sleepee said:**
> i get the same issue, but like nanotube says, only updates are available...
but shouldn't ubuntu know that i have a newer version??
or isn't there a way to take out the firefox 3.5 updates and make them stop??

no it shouldn't, because the packages come from different repositories and have different names. the 3.5 updates are completely harmless, just let them do their thing. 

if you have really strong feelings about it, you can go in synaptic, find the firefox-3.5 package, and 'freeze' it at the version it's at... 

or you can uninstall ff3.5 package completely. 

but it's easiest to just let it be. :)

---

### Post by sleepee on 2010-03-04
> **nanotube said:**
> no it shouldn't, because the packages come from different repositories and have different names. the 3.5 updates are completely harmless, just let them do their thing. 

if you have really strong feelings about it, you can go in synaptic, find the firefox-3.5 package, and 'freeze' it at the version it's at... 

or you can uninstall ff3.5 package completely. 

but it's easiest to just let it be. :)

well, i dont know if i want updates for a version of a program i'm not using, so i guess i could just take it out of the repo list right?
anyway, that's what i'm doing now, and it doesn't appear to give me anymore notifications about FF3.5 updates anymore...
thanx

hope the op has the same luck

---

