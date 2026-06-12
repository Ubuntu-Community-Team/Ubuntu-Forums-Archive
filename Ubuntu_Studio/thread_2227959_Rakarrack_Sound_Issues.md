---
title: "Rakarrack Sound Issues"
date: 2014-06-04
forum: Ubuntu Studio
---

### Post by Jeff_Spitzer on 2014-06-04
Everything works as it should in Rakarrack, but only Rakarrack audio works after starting the program.  I can't play any other audio from any other source on my computer even after quitting Rakarrack.  I also have no idea what I'm doing here so please pretend I'm more of an idiot than I actually am.

---

### Post by jejeman on 2014-06-05
Rakarrack uses JACK. When JACK runs only JACK aware applications plays sound. After quiting rackarrack se if  jackd or jackdbus are really dead.

---

### Post by Jeff_Spitzer on 2014-06-05
Thanks for the response!  Would I check that using the System Monitor program?  Or is there a terminal command to check or kill the process?  Please excuse my ignorance.

---

### Post by jejeman on 2014-06-05
You can check with system moniitor or with
```
pgrep
```
You can kill with
```
killall
```

---

### Post by Jeff_Spitzer on 2014-06-06
Thank you so much!  This solved my issue!!

---

