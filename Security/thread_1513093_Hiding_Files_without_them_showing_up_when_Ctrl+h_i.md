---
title: "Hiding Files without them showing up when Ctrl+h is pressed"
date: 2010-06-19
forum: Security
---

### Post by Weepleman on 2010-06-19
Hi, the title pretty much says it all.  I want to be able to hide things so that they do not show up when show hidden files is pressed.  Maybe something like a file that you can only get to by already knowing its location?

---

### Post by Ryan Dwyer on 2010-06-19
$ cd ~/Documents/
$ mkdir Hidden
$ echo "Here's a hidden file" > Hidden/secretmessage
$ chmod -r Hidden
$ ls Hidden # Permission denied
$ cat Hidden/secretmessage # displays message
$ nano Hidden/secretmessage # file is writeable

---

### Post by Weepleman on 2010-06-19
Thanks!  That worked really well.

---

### Post by BkkBonanza on 2010-06-19
That doesn't do anything that "sudo" can't immediately get around. 

$ ls Hidden # Permission denied

$ sudo ls Hidden # no problemo, shows contents

I didn't try it but I expect "gksu nautilus" would show the files too.

If you want to really hide stuff I'd suggest using Truecrypt with a hidden volume. Not only can you make the visible volume look like some other file (eg.mpg) but the hidden volume inside is undetectable. Nowadays Truecrypt is fairly easy to use with Ubuntu.

---

