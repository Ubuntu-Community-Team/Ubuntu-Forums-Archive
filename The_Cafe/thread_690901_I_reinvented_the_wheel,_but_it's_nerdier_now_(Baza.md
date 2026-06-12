---
title: "I reinvented the wheel, but it's nerdier now (Bazaar powered TODO list)"
date: 2008-02-07
forum: The Cafe
---

### Post by jdong on 2008-02-07
I was looking for a TODO list software to manage my MIT coursework this term, as I found my TODO list was no longer just a predictable "one problem set per course, Friday 12:00 noon" but rather a flurry of smaller assignments for each class on inconsistent due dates.

When I looked around, I found nothing that really matched my criteria. I needed something that either moves around with me on the 5+ computers I use during a given day, or can be easily accessed (i.e. CLI/ssh to my always-on server). I also wanted them in a plaintext, human-parseable format JUST IN CASE I managed to get stuck somewhere or broke enough that I don't have a client anymore, I should be able to either directly use a text editor or hack up a 5-minute program that can parse the storage format.

I also wanted as little NONSENSE as possible. I just need a todo list that tracks a deadline and a description, no calendar, no ICS, no attachments, none of that stuff that just adds complexity.

So, eventually I gave up my search and flexed my Ruby-foo to write my own. Thus, jtd is born: [http://jdong.mit.edu/~jdong/jtd-source/](http://jdong.mit.edu/~jdong/jtd-source/) (this location is also a bzr branch)

It's still in its infancy but README shows it in its daily routine. In short, by the end of the first hour I was able to input my day's assignments into the tool and use it to plan out the rest of my day. Over the course of the next two days, I added little tweaks and features as I found inconveniences in my workflow. As of today, about 2 days and a few hours later, I'm declaring it feature complete for my own work and am no longer putting any chunks of time towards developing it.

Oh yeah, it uses bzr to version-control itself. Now isn't that geeky?

Now, the lesson from all of this is that sometimes it's FUN to reinvent the wheel, and it can be done in a short period of time too. I only posted this because I thought some people might get a laugh or two out of this story, and also to show the world that I write really hackish code when in a hurry! I don't actually intend anyone to seriously consider this tool for themselves, though it'd be interesting if someone took the inspiration from this tool to evolve it into something better.


If you're wondering what I have to do now:

```

[jdong@jdong:~]$ jtd list                                         (02-07 23:18)
+ 6.005 Lab 1 prep, sw         | hw/6.005/lab1        | 86% | Fri 02/08/08 12:00
+ Add/Drop form turnin         | addform              |  0% | Fri 02/08/08 15:00
  Homework stuff               | hw/6.005/hw1         |  0% | Mon 02/11/08 12:00
  HASS readings                | hw/21W.746/read2     |  0% | Tue 02/12/08 15:00
  6.042 Reading; TP2           | hw/6.042/read1       |  0% | Tue 02/12/08 21:00

```

---

### Post by Mary.Riley on 2008-02-08
That's ridiculously cool. Good idea!

---

