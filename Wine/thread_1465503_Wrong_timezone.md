---
title: "Wrong timezone"
date: 2010-04-29
forum: Wine
---

### Post by Calash on 2010-04-29
This is something I have never seen before and the all-mighty Google has not been kind enough to guide me to a solution.

I am running Wine 1.1.42 on my work system (Ubuntu 10.04 x64).  I use PlayOnLinux to give wine extensions to each of my applications.  Two of them have no use for Date, or pull it from a server so they do not notice.

However one, Sametime Connect by IBM, records instant messages based on the internal clock.  In this application all the messages are exactly 4 hours ahead of my time, Eastern Standard Time.

(ie, I send a message at 3:00pm and Sametime date stamps it as 7:00pm)

While not a huge issue it is something I would like to resolve.

My timezone in Ubuntu is set to America/New York.  I verified that the system date/time is fine.  I have two VM's that are also fine as far as date, and nothing else on the system outside of Wine is having this problem.

Here is the output of date
```

Thu Apr 29 15:11:13 EDT 2010

```

I am at a bit of a loss as to where to check next.

---

### Post by asdfoo on 2010-04-30
hmm, interesting...

if you insert the date and time inside wine notepad, is it correct?

If not, I suggest you file a bug in the winehq bugzilla, link to a download if one is available, give the name of the program, attach terminal output as a text file and say that you have tested the date using notepad.

---

### Post by Calash on 2010-04-30
I never thought of that...such a simple test too.  Head is hitting the keyboard right now.

Inserting the date give the correct date and time.  However, and at the same time, Sametime reports 4 hours later.

It must be an issue in the application.  Time to dig into the settings and see what I can find.


Thanks for the guidance :)

---

