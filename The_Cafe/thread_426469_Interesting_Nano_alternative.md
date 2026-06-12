---
title: "Interesting Nano alternative"
date: 2007-04-28
forum: The Cafe
---

### Post by DirtDawg on 2007-04-28
I was screwing around and installed [mped]("http://www.triptico.com/software/mp") (Minimum Profit EDitor) from the repos. The gtk interface is slightly akward, but running it with the -tx option opens it with curses.
```
 mped -tx 
```

It's fast, there's pre-generated syntax highlighting, tabs, and ctrl+a opens a menu system. 
In addition, entering a blank when asked what file to open starts a basic file browser, and the user can run terminal commands and mped catches the output.

Configuring can be slightly tricky as you need to edit a file called ~/.mprc manually, but there's a premade 'sample'. The only options I've tweaked so far were for the gtk interface (what's with huge default fonts? People seem to love 'em).
```
cp /usr/share/doc/mped/mprc.sample.gz ~/
gunzip ~/mprc.sample.gz
mped -tx ~/mprc.sample
```

Anyway, I'm pretty happy with it and I can't find a single reference to it anywhere in the forums so I thought I'd share. Here's a neat-o screenshot:

[IMG]http://a425.ac-images.myspacecdn.com/images01/15/l_06a8cfbe4fd33a79d4abbabda0fb74c0.png[/IMG]

N'Joy!

---

