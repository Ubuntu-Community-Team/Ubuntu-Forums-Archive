---
title: "aptitude scores"
date: 2007-03-26
forum: The Cafe
---

### Post by maxamillion on 2007-03-26
I have made the switch from apt-get to aptitude some time ago but I have finally gotten to the point where I am left with questions about aptitude "scores" when resolving unmet dependencies. I assume that a score of 0 or greater is good and a negative is bad but I can't find any documentation on this anywhere, anyone know something I don't?

Any info is greatly appreciated.


p.s.- anyone with any thoughts on SMART package manager vs. aptitude? (just something I am curious about)

---

### Post by macogw on 2007-03-26
Well, when any process exits on 0, that means it did exactly what it should have done.  Anything else is bad.

---

### Post by maxamillion on 2007-03-26
Is there any detailed documentation about this anywhere because "anything other than zero is bad" doesn't really explain the relation between the decision of the package manager and the score number being displayed.

---

### Post by zorkerz on 2009-01-30
Does anyone know more about this? I just quickly looked at man aptitude and did not see any mention of the score.

---

### Post by mrhhug on 2010-09-29
i know im bumping an ancient thread but Google keeps sending me here....

---

### Post by Bachstelze on 2010-09-29
Apparently, no one really knows what it means. :p It probably has to do with thr Pin priority of the various packages that would get installed or removed with a given solution.

---

### Post by NightwishFan on 2010-09-29
I think it sorts it by score. This solutions ranks highest kind of thing.

---

### Post by mrhhug on 2010-09-29
I am really seeking the algebra behind this number; so i know weather or not to give it merit. Also right now im not even sure if positive or negative is better!

i understand that when you see this exit status (or not actually exit status because aptitude waits for user input then sometimes continues) that if you enter ```
o
``` aptitude will give you dependency issues 

is anyone even sure that this number is based on future number of unresolved dependencies?  

Does anyone know ANYTHING about this score?

the aptitude man pages are pretty worthless (for this)

---

### Post by marshmallow1304 on 2010-09-30
When there are unresolved dependencies, aptitude creates a list of possible solutions and assigns them scores.  I assume that a greater score means that aptitude more highly recommends a solution over one with a lower score.  As for the calculation of the scores and the significance of negative scores, I have no idea.

These are **not** exit statuses.

---

