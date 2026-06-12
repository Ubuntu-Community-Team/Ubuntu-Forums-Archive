---
title: "Open Office Worm"
date: 2007-06-11
forum: Server Platforms
---

### Post by gewitty on 2007-06-11
Not entirely sure where to post this, as viruses and worms don't normally seem to bother the Linux community. However, this  cropped up on CNET today, so I thought it might be worth noting.

Apparently, there is a Worm named Badbunny doing the rounds, which arrives as an Open Office file called badbunny,odg which if opened launches a macro that drops both badbunny.py as an XChat script and badbunny.pl as a Perl virus.

The report comes from Symantec, who have been monitoring the worm for over a month and have now announced that it is in the wild and affecting Windows, Mac and Linux OS's.

The full story can be read at [http://tinyurl.com/3686z9](http://tinyurl.com/3686z9)

---

### Post by jrusso2 on 2007-06-11
Sounds like symantec needs to sell Mac users their crummy antivirus.

If you see the file badbunny.odg don't open it.

You should not be opening files that you know nothing about anyway.

---

### Post by tdrusk on 2007-06-11
> **jrusso2 said:**
> 
You should not be opening files that you know nothing about anyway.
I agree. The best security is common sense.

---

### Post by Rui Pais on 2007-06-11
The question is why would anyone open a file called badbunny.odg? 
(not exactly a disguised name or something ambiguous...)
And why distribute as a oo file? a doc would hit much more people...

sounds like a pathetic lie invented to sell software.

---

### Post by Calash on 2007-06-11
If it was a lie it would be much more believable..they have departments for that type of marketing.

---

### Post by Rui Pais on 2007-06-11
Maybe... yes. 
Maybe a funny boy remember to do a bad joke for OO... or maybe symantec itself decided to write some kind of idiotic macro. To sell more (or at least spread more fear and panic, that always lead to more sales)

But check this:
> On Linux systems, the worm drops both badbunny.py as an XChat script and badbunny.pl as a Perl virus.

This macro creates (is that what drops means?) a py script, a XChat script (?) and perl virus?!? 
But whats this? 

You have to run the babunny file, then run the script voluntarily with root powers! 
and a perl virus would delete your home docs (cause it was all it can get permissions if it act dissimulated "under the table"...

:lol:

---

### Post by matchstich on 2007-06-11
[http://news.zdnet.com/2100-1009_22-6189961.html?tag=nl.e550](http://news.zdnet.com/2100-1009_22-6189961.html?tag=nl.e550)


i got the same alert.

---

### Post by dmizer on 2007-06-11
from norton who says the risk level is "1: very low"

> Wild

    * Wild Level: Low
    * Number of Infections: 0 - 49
    * Number of Sites: 0 - 2
    * Geographical Distribution: Low
    * Threat Containment: Easy
    * Removal: Easy

Damage

    * Damage Level: Low
    * Payload: May download other threats on to the compromised computer.

Distribution

    * Distribution Level: Low
[http://www.symantec.com/security_response/writeup.jsp?docid=2007-052303-3350-99&tabid=1](http://www.symantec.com/security_response/writeup.jsp?docid=2007-052303-3350-99&tabid=1)

this is fud.  don't run as root, and you won't have a problem.

---

