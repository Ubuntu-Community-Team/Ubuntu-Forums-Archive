---
title: "apt cannot fetch data from ubuntu-repos"
date: 2006-09-21
forum: Repositories &amp; Backports
---

### Post by jsteidl on 2006-09-21
Hello there, i am having some trouble with my sources.list

it started like this: by doing a $sudo apt-get update i was exposed to a massive ammount of "connection errors on $IP". Hm, so i tried $ping, $dig and a normal browser to test the urls.
All were working so i was starting to look for the next big road to jump on the street when the next truck were about to pass me. BUT NO, life (and Ubuntu!) is to beautifull (****** up, heh? My Computer is preventing me from commiting suiccide). I got a clean sources.list from here and tried that one... who knows. IT DIDN'T WORK! (<== Caps are not by mistake)

I tried to use different urls like de.archive.ubuntu.com or just archive.ubuntu.com and so on but i cant fetch information from the default repo.

Is that a common problem now? Will this feature be included in Edgy +1? Cool stuff, no just kidding! Does anybody want to give me a tiny clue because i feel really n00bish right now and i am not very comfortable with that. :-({|=

---

### Post by mssever on 2006-09-21
Is apt-get trying to use the IP address 1.0.0.0? In that case, see if [this thread]("http://www.ubuntuforums.org/showthread.php?t=250149") helps.

---

### Post by jsteidl on 2006-11-12
i've dealed with this allready too long. i reinstalled the server. Problem sovled. Or Not. Depends on the view.

---

