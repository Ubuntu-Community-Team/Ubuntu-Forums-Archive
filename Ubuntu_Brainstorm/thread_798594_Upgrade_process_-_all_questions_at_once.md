---
title: "Upgrade process - all questions at once"
date: 2008-05-18
forum: Ubuntu Brainstorm
---

### Post by kkkkdddd on 2008-05-18
Please make distribution process more unattended by asking all questions at once.

When I upgrade Ubuntu I always get 5-10 messages telling that new package is about to overwrite my old custom package(usually some config files). Subsequently, I have to choose whether I want to overwrite package or leave the old one. In my opinion it is good that I am able to make a copy of old file, review differences, etc. 
On the other hand, I am being asked some questions usually once per 5-10 minutes. When a question is asked the upgrade process waits until an answer is given. Due to it, I can not leave computer and do something else.
I have to spend an hour or two only to wait for further questions.

My solution:

When during update of a package a question is about to be asked, postpone installation of this particular package but proceed with installation of other packages. After update of all "non problematic" packages is finished, continue installation of postponed packages and then ask all questions. 

In this scenario, I would:
1. Run update manager.
2. Go to a friend for an hour.
3. Return and answer the questions.
4. After a minute update would be finished.  

Instead of:
1. Run update manager.
2. Wait 5 minutes for the first question.
3. Answer the question.
4. Wait 5 minutes for the next question.
5. Answer the question.
6. (...)

---

### Post by smartboyathome on 2008-05-18
This may have bad effects, some other packages could not be installed, due to the package that is being skipped not being installed at this moment.

---

### Post by kkkkdddd on 2008-05-18
Of course you are right, but it should be not a problem for about 90% of packages. 

If packages depend on any skipped package, they should be skipped too.

The vast majority of packages are leafs in dependency graph or there are only a few dependants. 

I would be really fond of this feature. I have been using Ubuntu since 5.04 and I always upgrade through update manager but the compulsion of waiting for these questions annoys me very much.

---

### Post by smartboyathome on 2008-05-18
Actually, that still wouldn't work. there are quite a few packages with configurations which could overwrite current ones, and which depend on quite a lot.

---

