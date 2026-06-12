---
title: "gksudo missing"
date: 2013-03-30
forum: Ubuntu Development Version
---

### Post by pfeiffep on 2013-03-30
Anyone notice that gksudo is NOT installed by default?

Also once installed it fails to recognize password. If I execute a simplistic command ie ```
sudo ls
``` then enter my password  and then enter ```
gksudo bleachbit
``` all is well.

I suspect that installing gksudo after the install has caused it not to be associated correctly with my keyring, however I'm at a loss on how to fix (especially since the work around is secure)

---

### Post by grahammechanical on 2013-03-30
Yes. I noticed it. It was a bit strange because gksudo worked on a Raring install that was several months old but not on an install I put in a couple of weeks ago. I thought that I was developing forgetfulness in my old age. But once I installed gksudo then I have not had problems using it.

Regards.

---

### Post by The Cog on 2013-03-30
I had noticed that gksu was broken - keeps asking for the password over and over.

gksudo seems to be there by default in Xubuntu 13.04, and working fine.

---

### Post by oldfred on 2013-03-30
I vaguely remember a while back someone mentioning that some commands with gksudo or just gksudo do not work first time, but need a sudo command issued first, then it works?

---

### Post by mc4man on 2013-03-30
gksu was missing from some recent images though it's been returned.
I know there was some mention of getting rid of gksu, maybe that's why it was removed & then returned as the replacement (pkexec) isn't ready yet (or just an inadvertent mistake

> From Sebastien Bacher (seb128)  on 2013-03-15: 
> ..about gksudo (which should be <not> used nowadays, we are replacing it by pkexec in
the standard desktop)


Happen to have one of those installs, will maybe try it later & see if gksu can get working if installed
(I just use a root terminal for such stuff

---

### Post by mc4man on 2013-03-30
Tried on that other install - 
After installing gksu had to open gksu-properties & change auth mode to sudo (defaults to su), then it worked fine
So give that a try
```
gksu-properties
```

---

### Post by Frogs Hair on 2013-03-30
I set up a Nautilus root launcher right after installation using  gksudo nautilus via the main menu.   gksudo (name) is working  from the terminal also.

---

