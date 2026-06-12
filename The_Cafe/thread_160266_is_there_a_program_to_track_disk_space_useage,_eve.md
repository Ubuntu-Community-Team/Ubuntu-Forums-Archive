---
title: "is there a program to track disk space useage, even a CLI?"
date: 2006-04-14
forum: The Cafe
---

### Post by ice60 on 2006-04-14
i was just looking at the [window's log thread](http://www.ubuntuforums.org/showthread.php?t=160159). i know there are some nice programs for tracking disk space useage for windows -
[http://www.snapfiles.com/reviews/SpaceMonger/spacemonger.html](http://www.snapfiles.com/reviews/SpaceMonger/spacemonger.html)
[http://www.snapfiles.com/screenshots/disktective.htm](http://www.snapfiles.com/screenshots/disktective.htm)
is there something similar for Linux? even a CLI program would be useful. thanks.

---

### Post by fng on 2006-04-14
Maybe a bit hard, but it does the job :)
```

cd /
du

```

Graphical tool :
- baobab : [http://www.marzocca.net/linux/baobab.html](http://www.marzocca.net/linux/baobab.html) (it's in universe)

---

### Post by ice60 on 2006-04-14
[QUOTE=fng]Maybe a bit hard, but it does the job :)
```

cd /
du

```

Graphical tool :
- baobab : [http://www.marzocca.net/linux/baobab.html](http://www.marzocca.net/linux/baobab.html) (it's in universe)[/QUOTE]
Wow, Baobab is excellent, i really like it :cool: thanks for the help, fng, lol i like your name - FNG lol
hmm, i just looked it up [here](http://www.acronymfinder.com/af-query.asp?String=exact&Acronym=fng&Find=Find) and the closest to what i thought you ment is this - Friendly New Guy
edit i mean this - Freaking New Guy (polite form) :D

---

### Post by fuscia on 2006-04-14
conky's good and it tracks a bunch of other junk, too.

---

### Post by jasay on 2006-04-14
I like filelight.  I find the pi-chart-esque display to be very easy to understand.  It's also in the universe repo.  [http://www.methylblue.com/filelight/](http://www.methylblue.com/filelight/)

---

### Post by fng on 2006-04-14
[QUOTE=ice60]Wow, Baobab is excellent, i really like it :cool: thanks for the help, fng, lol i like your name - FNG lol
hmm, i just looked it up [here](http://www.acronymfinder.com/af-query.asp?String=exact&Acronym=fng&Find=Find) and the closest to what i thought you ment is this - Friendly New Guy
edit i mean this - Freaking New Guy (polite form) :D[/QUOTE]

rofl, Well ... not even close :)
It's a short version from my original nick back in the old days. 1 dutch word, 9 letters, 3 syllables.  Every syllable starting with 1 letter from fng. (FxxxNxGxx)

---

### Post by ice60 on 2006-04-15
thanks, everyone. fuscia, i'm going to try conky when i install my new HDD, i want to try it with a light Desktop Environment or WM or whatever, it just looks good with them, i don't have enough HDD space atm to install anything else. 


@jasay i would have tried filelight, until i saw [SpaceMonger](http://www.snapfiles.com/reviews/SpaceMonger/spacemonger.html) being used, when you see it being used you see how good it is, and Baobab is very similar, plus if you don't like that UI you can have a more normal one
[http://www.marzocca.net/Immagini/treemap2.png](http://www.marzocca.net/Immagini/treemap2.png)
[http://www.marzocca.net/Immagini/bb1.png](http://www.marzocca.net/Immagini/bb1.png)

@fng oh well, i'm glad i made the edits to say what i ment otherwise you might have thought i was abit odd :-#

---

### Post by sapo on 2006-04-15
```
df -T -h
```

---

