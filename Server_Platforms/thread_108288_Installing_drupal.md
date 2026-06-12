---
title: "Installing drupal"
date: 2005-12-25
forum: Server Platforms
---

### Post by harisund on 2005-12-25
Has anybody installed Drupal yet on Ubuntu? Could they provide a tutorial or HOWTO or something? 

The thing is, I did manage to get Drupal and all that, but then when I create my first user it doesn't send me any email? So how do I log in? 

Also, every software package that I install seems to create a user for itself. How I make sure every use is me (hari)? Apache2 has its own user to serve from /var/www and mysql seems to have created its own user? 

Any help here with Drupal please? 

Thanks !

---

### Post by Linux O)o_O7 on 2006-11-04
I NEED a guide also for Drupal installation on ubuntu. 

Searching this forum for help this week.

---

### Post by aysiu on 2006-11-05
**Step 1:** [Enable extra repositories](http://www.psychocats.net/ubuntu/sources)--it's the Universe repositories in particular that you need.

**Step 2:** ```
sudo aptitude update
sudo aptitude install drupal
```

---

