---
title: "bit of a newbie"
date: 2011-02-12
forum: Virtualisation
---

### Post by morphy richards on 2011-02-12
I've installed a backtrack vm image and launched virtual box, i can boot up into backtrack no prob's, and Ive set the networking devices eevry possible way but cant get a connection through the backtrack vm, if i have a look at ifconfig - I've only got my loop-back address in there and nothing else.  Ive used virtual box on a windows machine before and didn't have any problems sorting the network connection out - any ideas ?
 Im running Ubunutu 1010 and useing virtual box 3.2.8.  
Ive got a backtrack 4 iso as well

Any help appreciated!

---

### Post by morphy richards on 2011-02-12
just add that im useing a network connection eth0!

---

### Post by CharlesA on 2011-02-12
IIRC you need to start networking:

```
/etc/init.d/networking start
```

You might have better lucky posting over on the backtrack forums.

---

