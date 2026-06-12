---
title: "White Rectangle Randomly Appears"
date: 2012-03-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Jdogzz on 2012-03-20
I'm not sure if this is a bug for Precise specifically but it has only happened to me on it and on multiple machines. Without doing anything that I am aware of, a white rectangle will appear in the top left of the screen. It doesn't seem to be clickable and doesn't have a program running in the launcher to cause it. I tried Googling the problem but if there were any solutions they were drowned out by a similar but different problem (terminal window and small white line protruding from the left side of the screen). I've attached a screenshot of the box. Has anyone else encountered this before?

---

### Post by Harry33 on 2012-03-21
You must give us a bit info on your setup.
- for how long have you experienced this bug?
- what graphics card and which drivers are you using?
- what is your GTK+3 version?
- is your setup fully updated?

This seems to be a GTK+3 issue.

---

### Post by Funnnny on 2012-03-21
It's reported to be some issue with notification in Google Chrome, if you beleive that it's not the problem, file a bug in launchpad.

---

### Post by maciejg on 2012-03-21
Same here, but I can confirm it is related to Chrome browser.

---

### Post by Jdogzz on 2012-03-21
After you gave me the additional insight into what it was I managed to find the bug in Launchpad here: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/940603](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/940603)
Guess this can be marked solved for now as the problem isn't unique and a fix is on the way:)

---

