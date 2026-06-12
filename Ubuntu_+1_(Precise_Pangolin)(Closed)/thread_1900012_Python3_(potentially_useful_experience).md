---
title: "Python3 (potentially useful experience)"
date: 2011-12-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by zika on 2011-12-25
For a week or so I did get warnings that there is a problem with python3, which I disregarded...
Today I was doing some cleaning (ppa-purge) and that became an obstacle. Message was that python3 was not there...
Simple ```
 sudo ln -s /usr/bin/python3.2mu /usr/bin/python3
```made it all easier...
It seems that somewhere it was forgotten...

Update: It seems that this symbolic link solved [http://ubuntuforums.org/showthread.php?p=11552631#post11552631](http://ubuntuforums.org/showthread.php?p=11552631#post11552631) ... ;)

---

### Post by fabricator4 on 2011-12-26
> **zika said:**
> 
It seems that somewhere it was forgotten...
[/url] ... ;)

Should there be a bug report about this?  I have 63 updates for Precise held back because of the missing python (apparently).

63 at last count; I've been away from home and my test machine for a few days...

Chris.

---

### Post by zika on 2011-12-26
> **fabricator4 said:**
> Should there be a bug report about this?  I have 63 updates for Precise held back because of the missing python (apparently).

63 at last count; I've been away from home and my test machine for a few days...

Chris.I do not know, I did not check lately...
Did You try dist-upgrade or full-upgrade? [COLOR=Red](carefull!!!)[/COLOR]
I do not have any package waiting (even before this patch of mine...)...

---

### Post by fabricator4 on 2011-12-26
> **zika said:**
> I do not know, I did not check lately...
Did You try dist-upgrade or full-upgrade? [COLOR=Red](carefull!!!)[/COLOR]
I do not have any package waiting (even before this patch of mine...)...

I've learned to be rather wary of partial upgrades; it can be pretty hard to know what has broken sometimes.  I'll probably try a re-install and see if fixes it but something seems to have been forgotten along the way.

Chris

---

### Post by zika on 2011-12-26
> **fabricator4 said:**
> I've learned to be rather wary of partial upgrades; it can be pretty hard to know what has broken sometimes.  I'll probably try a re-install and see if fixes it but something seems to have been forgotten along the way.

ChrisIf anything (which happens very rarely) goes wrong with dist-upgrade, reinstall is the last of all resorts... By all means...
You're in total control all the time, during dist-upgrade... Just check what is offered, consult change-logs...
It is not something that is forgottern along the way, it is testing, some new packages need to be installed for the 1st time and some need to be removed...

---

