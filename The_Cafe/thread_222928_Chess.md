---
title: "Chess"
date: 2006-07-25
forum: The Cafe
---

### Post by Cyfr on 2006-07-25
Hello could anyone recommend a chess client that WORKS. Eboard simply breaks all the time for both me and my friend (even on a clean ubuntu install so ruling out a crappy system)...

I just want a multiplayer chess app... any good ones? :D

---

### Post by sapo on 2006-07-25
[http://games.yahoo.com](http://games.yahoo.com)

Just play the yahoo chess.. it works like a charm here :)

---

### Post by AndyCooll on 2006-07-25
Well I use xboard with the gnuchess engine. Not had any problems with it so far.

:cool:

---

### Post by Kvark on 2006-07-25
xboard works fine for me. It can do hotseat, netowork play, email play or use any of the 4 chess engines in the repos (gnuchess, sjeng, phalanx and fruit) but polyglot is needed to make it talk to fruit.

It has a ton of command line options so make one shortcut for each kind of game you want to play. For example to play against phalanx in 60% easy mode wihout time limit the shortcut is: xboard -clockMode false -fcp "phalanx -e 60"

The only major downside I've found is that it's not using the lovely GTK+ widgets but thats not a real flaw since widgets are a matter of personal taste.

---

### Post by sapo on 2006-07-25
> **Kvark said:**
> xboard works fine for me. It can do hotseat, netowork play, email play or use any of the 4 chess engines in the repos (gnuchess, sjeng, phalanx and fruit) but polyglot is needed to make it talk to fruit.

It has a ton of command line options so make one shortcut for each kind of game you want to play. For example to play against phalanx in 60% easy mode wihout time limit the shortcut is: xboard -clockMode false -fcp "phalanx -e 60"

The only major downside I've found is that it's not using the lovely GTK+ widgets but thats not a real flaw since widgets are a matter of personal taste.
Hum.. could you please tell me if you can configure the level in one of these engines?

I hate xboard with gnuchess.. it always beat me in 2 minutes :(, yes i m a n00b :(

---

### Post by Kvark on 2006-07-26
Gnuchess has an easy level:
xboard -fcp "gnuchess -e"

I use Phalanx instead because it has a whole easy scale that goes from 100% Easy:
xboard -fcp "phalanx -e 100"

To 0% Easy = hardest:
xboard -fcp "phalanx -e 0"

Sjeng and Fruit doesn't seem to have any difficulty settings. The only way to make them dumber is to read up on how to change advanced options to decrease the size of search caches and turn off all the smart features. Which is too much hassle, at least for me.

---

### Post by sapo on 2006-07-27
> **Kvark said:**
> Gnuchess has an easy level:
xboard -fcp "gnuchess -e"

I use Phalanx instead because it has a whole easy scale that goes from 100% Easy:
xboard -fcp "phalanx -e 100"

To 0% Easy = hardest:
xboard -fcp "phalanx -e 0"

Sjeng and Fruit doesn't seem to have any difficulty settings. The only way to make them dumber is to read up on how to change advanced options to decrease the size of search caches and turn off all the smart features. Which is too much hassle, at least for me.
Thanx! i ll try this once i get home.. sometimes i play some chess in flash on the internet but they are too dumb.. and gnuchess is too smart for me.. .

---

