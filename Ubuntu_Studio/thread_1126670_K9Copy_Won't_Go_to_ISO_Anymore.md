---
title: "K9Copy Won't Go to ISO Anymore"
date: 2009-04-15
forum: Ubuntu Studio
---

### Post by Smiley Coyote on 2009-04-15
All I get is the TS folders and between K9, Brasero, and DeVeDe, I cannot seem to add the folders as with Nero in order to just burn a DVD.  I used to watch as K9 ripped the files and converted to an ISO but now, when it gets to the part of creating an ISO it just says it is done after a fraction of a second and, of course, there is no ISO to be found anywhere, let alone the set destination directory.

I certainly don't remember changing any settings that would induce this and cannot find any settings that seem like they would even have such an effect.  It WAS working so well.  I wonder what happened.  I can't remember exactly when I upgraded to Ubuntu Studio but it could have been since my last backup attempt.

A little help in this matter would certainly rock.

---

### Post by Smiley Coyote on 2009-04-15
Now, all the files that were in the TS folders are gone.  I can assure you that I did not accidentally delete them.  They, as well, are not in the trash.  It started a few weeks ago, really, when the ISOs I created were invisible in the directories I sent them to.  I would open a program to burn it and find the ISO from there but it would not be visible by simply browsing my directories.

What the @#$% is going on here?!?

Does anyone know?

---

### Post by skullmunky on 2009-04-15
No idea, but here's my workflow which I came up with because I was having some trouble getting k9copy to work exactly right...

1. in k9copy, use the "Copy to DVD" button, to just burn a DVD directly.
2. when it finishes ripping and asks for you to insert a blank DVD, cancel.
3. open K3B, create a new Video DVD project, and find the files in [code]/tmp/kde-[username]/k9copy
4. drag the files in the VIDEO_TS folder into the VIDEO_TS folder in the K3B project.
5. burn

good luck ...

---

### Post by indytim on 2009-04-16
Check your available space.  You may be approaching a fill condition.

IndyTim

---

### Post by rfurman24 on 2009-05-07
In Intrepid with K9copy 2.0.2 I could rip to iso. Now with Jaunty it leaves half the dvd out of the iso.

---

### Post by rfurman24 on 2009-05-07
Installing Xine(and apparently some codecs that get installed with Xine) fixed my problem in Jaunty. I do not know for sure how.

---

