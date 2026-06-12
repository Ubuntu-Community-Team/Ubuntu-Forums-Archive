---
title: "Apport"
date: 2012-01-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-01-12
Apport became just too unstable for me. It crashes more than half of the times I decide to use it report something. 

A new behavior I am seeing as of the past few days is that after creating the report, it tries to open a second instance of Firefox, instead of using a new tab in the currently running browser. A Firefox pop-up warns that Firefox is already running, and it's pid must be killed before I can start a new session. It makes no sense: Why would I kill a perfectly good session anyway. At this point apport report is lost, apport itself crashes.

---

### Post by mc4man on 2012-01-12
apport does seem to have some issues atm & have seen similar here though mainly with root owned crashes, user ones *usually* work out ok.

You can try checking in /var/crash for .crash's, any .1000 ones you can just r. click on > Open with report ..
Any that are locked you can do the same as root, (root browser or other means

---

