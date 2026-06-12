---
title: "Who remembers &quot;green screen&quot; text terminals?"
date: 2011-10-17
forum: The Cafe
---

### Post by dbsoundman on 2011-10-17
Better yet, who remembers how to use them! :p I've got a nice old IBM InfoWindow 3153 which is working nicely with an Ubuntu Server 10.04 virtual machine (meaning yes, the serial port is tunneled through the host, with no issues). The only issue I'm having is the usage of "pages"; the built-in memory that the terminal has, which you can use to run different commands and "store" the output in various ways. My issue mostly lies in commands that produce results which are longer than one screen. The terminal has a mode where you can turn on "auto pages", which basically means if, for example, I do an "ls" command which produces more than one screen worth of results, it will start filling the other pages in its memory with the overflow automatically. It's pretty nice, but it doesn't seem to have a way to clear all the pages at once, and having data left over on various pages really messes with programs like lynx, as you see remnants of the stored buffers all over the web pages you're trying to view. If I turn off auto pages, I can obviously manually switch to other pages to run a command, but if the command goes over one page length, I lose the overflow -- it doesn't move onto another empty page. I'm sure there's some way to tell it to redirect output to multiple pages, but I'm not sure how to do it. (Or, at least I'm hopeful there's a way!)

I'd really appreciate your help in figuring this out, and I'd also love to hear about your experiences with the green monsters!

-Dan

---

### Post by gsmanners on 2011-10-18
Haven't used a monochrome since the 286 days. All I can remember from way back then is playing SimCity in Hercules mode. :P

---

### Post by Dr. C on 2011-10-18
I used the IBM and Ann Arbour terminals at University in the late 70's and early 80's. We then moved to an original IBM PC running Kermit under MS DOS to emulate the IBM terminals. IBM still has support information for these terminals. [https://www-304.ibm.com/support/docview.wss?uid=isg3T1000109]("https://www-304.ibm.com/support/docview.wss?uid=isg3T1000109"). Something other tech companies need to learn.

---

### Post by ninjaaron on 2011-10-18
My dad bought an Apple IIec around the time I was born, which had a color display.  I still still saw quite a few monochrome displays around when I was little.

Of course, everyone has seen them in the Matrix.

---

### Post by forrestcupp on 2011-10-18
My wife is a SQL developer, but some of the people where she works actually still use green screen as one of the main parts of their jobs. They're pretty set against giving it up, too. My wife even has to use it sometimes.

When she told me that, I was amazed.

---

### Post by Docaltmed on 2011-10-18
First time I ever talked to a computer it was on a teletype machine. Green screen terminals were a big step up.

---

### Post by dbsoundman on 2011-10-18
Thanks for the link, Dr. C! I searched all over the web and never found that page before. Hopefully that has a better explanation of the page feature. Right now my main purpose on this thing is to play Zork (which is, believe it or not, tougher than it seems -- takes a different frame of mind than modern games), but hopefully I can find some other uses for it...or at least other games to play. ;)

forestcupp -- how do those SQL people use the terminals exactly? I've only had some vague and so far unsuccessful run-ins with SQL so far, so I don't exactly know why you would need a terminal for it.

-Dan

---

### Post by forrestcupp on 2011-10-18
> **dbsoundman said:**
> Thanks for the link, Dr. C! I searched all over the web and never found that page before. Hopefully that has a better explanation of the page feature. Right now my main purpose on this thing is to play Zork (which is, believe it or not, tougher than it seems -- takes a different frame of mind than modern games), but hopefully I can find some other uses for it...or at least other games to play. ;)I beat Zork a long time ago on the C64. Great game.

> **dbsoundman said:**
> forestcupp -- how do those SQL people use the terminals exactly? I've only had some vague and so far unsuccessful run-ins with SQL so far, so I don't exactly know why you would need a terminal for it.

-Dan
The people who use green screen aren't SQL devs. That's for something completely different, and I don't know what it is.

---

### Post by dbsoundman on 2011-10-18
I actually made some progress playing Zork, I'm starting to get the hang of it! Even figured out how to save/restore games.

Back to the issue of "pages", I looked through the IBM materials, then through the big HOWTO site on terminal computing with linux, and finally noticed that linux applications generally don't support pages, which explains why they weren't being used before automatically. So, my question is, how do I handle terminal output that's longer than one page if I can't see it? For example, let's say I say "frotz --help" in the terminal. The help file is longer than 80 lines, so it overflows, and I'm left with only the last part of the readout. How can I stop the terminal, or somehow tell it to save the top part? Is there a linux command for this? I tried doing "frotz --help > help.txt", but that didn't work. Once I figure this out, I'm pretty much good to go on terminal computing. Thanks for the help!

-Dan

---

### Post by gsmanners on 2011-10-18
Well, in Linux you can just pipe to more or less:

```
cat help.txt | less
```

---

