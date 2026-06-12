---
title: "Got a process &quot;x -core :0 -seat&quot; showing in Conky. What is it."
date: 2015-07-22
forum: Ubuntu Development Version
---

### Post by philinux on 2015-07-22
In conky it's showing in the top 4 highest cpu usage. About 2.4%.

It does not appear in system monitor. What is it and what is it doing.

Anybody know.

---

### Post by QDR06VV9 on 2015-07-22
Do you see a xorg along with that?

---

### Post by philinux on 2015-08-04
> **runrickus said:**
> Do you see a xorg along with that?

No. And the process does not appear in system monitor.

I'm wondering if it is Xorg?

---

### Post by QDR06VV9 on 2015-08-04
> **philinux said:**
> No. And the process does not appear in system monitor.

I'm wondering if it is Xorg?
That would be my guess the new conky version(and the change in the code) seems to need some added tweaking to the config of the .conkyrc
The posts in both conky threads are showing that now, plus I had a small bout with it awhile ago [http://ubuntuforums.org/showthread.php?t=2285118](http://ubuntuforums.org/showthread.php?t=2285118)
I have since downgraded to the older conky, until I get head wrapped around the new changes:D
Kind regards

---

### Post by deadflowr on 2015-08-04
It's showing you the command line, instead just the program name.
In top, toggle the program and command line with 'c'.
In system monitor highlight the process right click and open properties.
(The output for the command line should be the output shown in conky)

It's a weird new behavior of conky.

conky also has a new(?) feature that allows the top name to be as long as you want (top_name_width; it's a config option. the default is 15)
So in theory, you could make it say only xorg (if you wanted to make all shown processes only 4 characters long, lol)

I haven't seen much to write home about with the new conky, except the you can now enable bi-directional scrolling. to make scroll bars scroll left to right or right to left.
(I guess there is some new features for things I never use, but I wouldn't notice, since i don't use them)

---

