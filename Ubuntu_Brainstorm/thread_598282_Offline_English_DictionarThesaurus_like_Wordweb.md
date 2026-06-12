---
title: "Offline English Dictionar/Thesaurus like Wordweb"
date: 2007-10-31
forum: Ubuntu Brainstorm
---

### Post by legends2k on 2007-10-31
I feel, and have also seen, quite some posts requesting an application similar to Wordweb in Win. It would be nice if the next Ubuntu ships which a free, offline, handy dictionary/thesaurus like [Wordweb]("http://en.wikipedia.org/wiki/Wordweb").

Features like invoking the dict. on selecting text and pressing some key-combo, which would pop-up with the meaning would be an awesome advantage, IMHO. Its very well, possible too, since Worbweb, itself, uses [Wordnet]("http://en.wikipedia.org/wiki/Wordnet"), a free english semantic lexicon, for its data (Eng. part of it).

Try this [thread]("http://ubuntuforums.org/showthread.php?t=598267") too, if you feel so.

---

### Post by coolen on 2007-10-31
I'm worried about disc space here. To have that information available offline, you'd need to have it on disc, and it seems like an awful lot of data.
So, you'd have to either sacrifice disc space, do a massive download at some point, or cache data (which still means you have to get it from the net, since I certainly wouldn't be looking up most words twice).
Of course, if it's been done for Windows, it's possible. I can't imagine a lot of users suffering through a massive download for a disctionary application.

---

### Post by legends2k on 2007-10-31
The Wordnet total wordbase base is not more than 7 MB, I tried getting it by
```

sudo apt-get install wordnet
 
```
is it really that big to be included in the live disc??

---

### Post by coolen on 2007-10-31
Well, it was just my first impression. If you can fit all of the data into 7 Mb, then it could probably be made to fit somewhere.
Are you sure that's not just the client? Seems kind of big for a single program, but rather small for a language which had Shakespeare contributing to it.

---

### Post by legends2k on 2007-10-31
I am sure, since the package has word repository, and a lightweight browser named Wordnet browser to lookup the word defs. Toetehr the package is 7 MB. You can try pulling it from the Universe rep. and see for yourself, if interested.

```

~$ sudo apt-get install wordnet
...
...
...
~$ wn "animation" -over
(will give you the look up of 'animation'')

~$ wnb

```

will popup the Wordnet Browser

---

### Post by coolen on 2007-10-31
Well, there you go. I knew our language sucked :P
If you could write a nice GTK GUI for it (or convince someone else to), it could make it on as a replacement for the current dictionary. The base would be too small for the Live CD, I'd say, but it'd be a relatively small download for most users as a once-off. Perhaps they could choose (when first launching it) whether to get the base now, or just fetch it normally, with an option to get the base later on.

---

### Post by legends2k on 2007-10-31
Ok, I will try to write a decent GUI with Python's Help, then we can think of the further proceedings, as per what users feel about it.

---

