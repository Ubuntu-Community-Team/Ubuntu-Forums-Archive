---
title: "Terminal text effect"
date: 2008-09-04
forum: The Cafe
---

### Post by Daminvar on 2008-09-04
I found a strange glitch that happens when you try to "execute" a PDF file.  (I incorrectly thought that running a file from the terminal would open the file in the default player.)  Anyway, when I ran it by changing to the file's directory and running it by typing...

./file_name.pdf

...I got a bunch of glitchy text running down my screen.  After 5 minutes or so, it stopped, but it messed up all of the characters in the terminal.  I thought it looked pretty neat, so I took a screenshot

[IMG]http://img157.imageshack.us/img157/5927/screenshotseadiskdjj1.png[/IMG]

(This is me playing a MUD in the terminal with glitchy text)

Once I closed the terminal and opened it again, the text was back to normal.  I don't really know why it happened, and it didn't seem to cause any damage, so I don't really care all that much.  If you find that it works for you, then I guess you could have some fun with it.

---

### Post by lian1238 on 2008-09-04
I've seen this effect before, but don't remember how I got it. To reproduce this, print the ASCII character 16 for this "effect" and 17 for normal mode.

In C++: ```
cout << '\16'; // switch to 'drawing' mode
// do some ASCII drawing here!
cout << '\17'; // switch to normal text mode
```:)

---

### Post by LaRoza on 2008-09-04
That will happen when you try to view a binary file (or it can happen with improper ncurses programming).

Try it, cat a binary file ;)

---

### Post by Daveski on 2008-09-04
*ctrl-j*
type *reset* then press *return*
*ctrl-j* again

This will reset a terminal.

---

### Post by -grubby on 2008-09-04
> **LaRoza said:**
> 
Try it, cat a binary file ;)

```
cat /bin/cat
```

Fun stuff

---

