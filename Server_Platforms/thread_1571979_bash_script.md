---
title: "bash script"
date: 2010-09-10
forum: Server Platforms
---

### Post by terazen on 2010-09-10
I'm thinking of a few ways to do this I'm curious how many better/equal ways there are to do the same task. ;)

In a file with format like:
20 text Gi0/2 some other junk

I have it reformatted to look like this before going in a database:
0/2 20 text

But for whatever reason some of the new input text looks like this now:
20 text Gi1/0/2 some other junk

My script makes it look like this:
1/0/2 20 text

I want it to remove the leading number and slash if the input file is in the new format.

---

### Post by BobVila on 2010-09-10
You'll find that people will be more willing to respond if you post the code you've already written. We're here to help and share knowledge, but no one wants to do anyone's work for them.

---

### Post by terazen on 2010-09-10
I would have but most of it doesn't pertain to the question so it would just be confusing.  My script gets it to the point of what I listed and the rest bounces the information off a mysql database and sends emails so it's unnecessary to the question as well.

Also, I've got it working already so noone is doing my work for me.  I'm just looking to learn other ways (possibly better) of doing the same thing.  My scripts work, they just might be 3x longer and way slower than they need to be!

---

### Post by DaithiF on 2010-09-10
what are you using so far?  if sed, this should do it:
```
$ sed 's#^\(20 text\) Gi\(1/\)\?\(0/2\).*$#\3 \1#' < <( echo -e "20 text Gi0/2 s
ome other junk\n20 text Gi1/0/2 some other junk")
0/2 20 text
0/2 20 text

```

---

### Post by terazen on 2010-09-10
The only thing I used sed for was to replace spaces with underscores and back so a "for i in `cat filename`" would have $i as the whole string, not each individual word.

I'm really weak in awk/sed so I only caught about 80% of that.  Gonna look it over to fully understand it.  Thanks! :)

---

### Post by terazen on 2010-09-10
Got it after I figured out the \# thing was recalling earlier matches. Went from 386 lines to 378 from just this...I kinda suck lol.

Anyhow, yay for learning something on a Friday.  Thanks DaithiF! :D

---

