---
title: "[IDEA] GUI-based dpkg lock resolution"
date: 2007-10-18
forum: Ubuntu Brainstorm
---

### Post by aysiu on 2007-10-18
**Summary:**
A fully GUI (GTK or QT) dialogue that will allow users who are trying to run multiple instances of *apt* simultaneously to properly kill one instance of it and use the desired one.

**Scope and Use Cases:**
Maria opens up Add/Remove to install some programs. Then a notification appears on the panel saying there are updates to be installed. She clicks on the updates to be installed and then gets an error message saying *Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)*. She gets confused by this message and doesn't know how to fix it.

**Implementation Plan:**
Create an extension of *apt* that allows one instance to override another instance and let the user decide: > Add/Remove needs to be closed before you can install updates to your system. Do you want to close Add/Remove and discard changes or install updates after Add/Remove is finished?
* Close Add/Remove
* Install updates later

---

### Post by nesl247 on 2007-10-18
I like the idea to a point. But I think that instead of doing that, it should attempt to wait until the other instance is completed, or that the other instance could have the new instance's commands appended.

---

### Post by Zdravko on 2007-10-19
Yeah, nesl is right.

---

### Post by coolen on 2007-11-01
To my knowledge, neither Add/Remove nor Software Updates will lock APT. Only when you attempt to add/remove/update will it do that.
Perhaps a kind of queue could be implemented for APT? As long as the actual package operations aren't occuring in parallel, it should be safe. Let the user select their options, ask for confirmation for whatever's needed, and when they go to install, inform them that another package manager is running, and theirs will continue afterwards (with an option to remove their operation from the queue).

---

