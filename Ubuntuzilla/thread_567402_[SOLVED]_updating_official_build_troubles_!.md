---
title: "[SOLVED] updating official build troubles !"
date: 2007-10-04
forum: Ubuntuzilla
---

### Post by the.phantom on 2007-10-04
i checked and i have the latest build of ubuntuzilla

i got the popup this morning saying a new build of t-bird is out (2.0.0.61)
and ran 
gksudo thunderbird &

from the terminal
and t-bird says i have the latest version

5 hours later i tried again and same thing so i ran 
ubuntuzilla.py -a checkforupdatetext -p thunderbird
from the terminal
and it said latest version is 2.0,0,61
so i tried 
gksudo again and still says i have the latest version ?

1. anyone else having this trouble?
and maybe their site is sick?

or a problem with ubuntuzilla?

---

### Post by the.phantom on 2007-10-04
UPDATE

i fired up a old win98 box and it did the same so might be t-bird with the confusion? it said i was current also

---

### Post by nanotube on 2007-10-06
are you sure its "2.0.0.61"? the latest version is 2.0.0.6, there is no 2.0.0.61

what happens if you run
```
ubuntuzilla.py -a checkforupdatetext -p thunderbird
```
?

---

### Post by the.phantom on 2007-10-08
yep
might had been 2.0.0.6.1

i have ubuntuzilla to check for updates and i got that small popup on both systems with U on them
and i checked on the win 98 box and it said also nope i am current

i don't know how the scripts are checking, but maybe there was a bobo on mozilla?

it happend starting at 7am and i was getting the popup after 3pm  ( pacific time)
and have not had it since ?

and when i do the terminal  command check for updates it said there was that one?

but haven't got the popup all week....
so i suspect a hickup with mozilla?


and to answer the next obvious question

no i have not had a drink since 1978 ;)

but i'll call this solved as it happened just the one day on two systems and not since !

---

### Post by nanotube on 2007-10-09
hmm... might have been some snafu on their site - ubuntuzilla pulls the latest version directly from the main mozilla.com website. 

well.. if it went away, nothing we can do now. :) thanks for reporting it, though, i'll be on the lookout for any future problems!

---

