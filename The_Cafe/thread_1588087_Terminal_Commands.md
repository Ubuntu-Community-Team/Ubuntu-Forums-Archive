---
title: "Terminal Commands"
date: 2010-10-04
forum: The Cafe
---

### Post by shadowfax1 on 2010-10-04
Is there documentation showing all the terminal commands and what they each achieve.
and perhaps an explanation as to how their structured?

---

### Post by realzippy on 2010-10-04
....start [here]("https://help.ubuntu.com/community/UsingTheTerminal")

---

### Post by s.fox on 2010-10-04
Hello,

[This]("http://linuxmanpages.com/") site should prove useful to you.

-s.fox

---

### Post by cariboo on 2010-10-04
Our own jpeddicord, created [this]("http://fosswire.com/post/2007/08/unixlinux-command-cheat-sheet/") cheat sheet. I have it tacked to the wall in my shop, although I don't check it very often any more. :)

---

### Post by conundrumx on 2010-10-04
Using octal notation for chmod is great for a lot of things, but you don't have to use it.  Some people struggle with it, and many only really know one or two combinations associated to a certain end result (755 being extremely common).

These are all equally valid:

```

chmod +x [file] to add execute permission for the current user
chmod u+rwx [file] to add read, write and execute permissions for the current user
chmod go-rw [file] to strip read and write permissions for group and other

```

---

