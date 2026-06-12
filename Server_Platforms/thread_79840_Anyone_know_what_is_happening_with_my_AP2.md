---
title: "Anyone know what is happening with my AP2"
date: 2005-10-20
forum: Server Platforms
---

### Post by dbee on 2005-10-20
I've had a load of trouble of one sort or another with apache2 lately and no-one seems to be able to answer any of my questions.

Where is the best place to get apache support do you think ??

My latest woes include these lines when I run make 

*** Warning: Linking the executable httpd against the loadable module
*** mod_access.so is not portable!

---

### Post by LordHunter317 on 2005-10-20
Posting what you tried to do would be helpful.  Not seeing at least hte configure you ran makes helping you rather impossible, as it could be one of a million things.

Unless you have a reason to build Apache2 from source, don't.  And if you had a reason, you wouldn't need help buliding it.

---

### Post by dbee on 2005-10-21
Thanks LordHunter, but I've kinda given up on getting any help so I guess I didn't bother posting the full message.

Basically I was running a

make 

on a 

./configure --prefix=/usr/local/apache2 --enable-so

and it kept telling me that the .so files were 'unportable', whatever that means.

As per second comment. Building apache is a whole lot more complicated than I thought it would be. I want to get it just right though, and I'm prepared to put in the time in order to do that. That way if my server gets own3d down the line somewhere I'll be able to deal with it, as opposed to having to come back and ask all the questions that I should have asked in the first place.

Apologies if it seems like I'm projecting my frustrations on to the ubuntu board though ... that wasn't my intentions, believe me. :smile:

---

### Post by LordHunter317 on 2005-10-21
Well, it means you can't run them on any other platform I believe, and it's a perfectly normal warning.  I haven't done an Apache build in a while though, so I could be mistaken.

---

