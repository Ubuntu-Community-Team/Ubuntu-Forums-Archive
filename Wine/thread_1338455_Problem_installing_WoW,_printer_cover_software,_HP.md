---
title: "Problem installing WoW, printer cover software, HPLIP. and other problems"
date: 2009-11-26
forum: Wine
---

### Post by samsam_eli on 2009-11-26
I am trying to switch from Windows to Linux, and have installed Ubuntu 9.10 
Now I want to install WoW, HP deskjet 3425 cover software and HP Linux Imaging and Printing.

I need step by step instructions for this.

With the WoW installation, the problem is that when I insert a CD in the CDROM, the CD/DVD drive disappears. That is, I can't find it. 
I have the same problem with the printer cover software.

Also, I don't know how to use Wine when it doesn't start automatically. 

And where can I find out what the command line means?

---

### Post by cariboo on 2009-12-03
A bump for the move.

---

### Post by doas777 on 2009-12-03
well, to run an app with wine, just enter
```

wine <pathtoapplication>
```

your wine root in in your home folder in .wine (folders that start with . are hidden, so hit ctrl+h to show them). 

after you put in a cd, open a terminal and run:
```

ls /media/cdrom0

```
what output do you get?

---

