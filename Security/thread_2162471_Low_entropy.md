---
title: "Low entropy"
date: 2013-07-14
forum: Security
---

### Post by Hungry Man on 2013-07-14
My system has 100-200 entropy at any given time. Seems somewhat low... is there a way to improve this without some method that involves using less random data?

---

### Post by cariboo on 2013-07-14
It seems to me that when creating ssh keys, if the entropy is to low, the program suggest moving the mouse around, while generating keys.

BTW on my system it shows entropy_avail = 134

---

### Post by DanR01 on 2013-07-15
I've installed haveged from the repos

[http://www.issihosts.com/haveged/](http://www.issihosts.com/haveged/)

My available entropy is normally in the range of 2500-3500 with this program.

---

### Post by ITfromScratch on 2013-08-07
> **DanR01 said:**
> I've installed haveged from the repos

[http://www.issihosts.com/haveged/](http://www.issihosts.com/haveged/)

My available entropy is normally in the range of 2500-3500 with this program.

Same here. I installed haveged on a server that was running a web app. My available entropy shot up to about the same range as you and the app started responding MUCH faster.

---

### Post by CharlesA on 2013-08-07
> **cariboo907 said:**
> 
BTW on my system it shows entropy_avail = 134

Home server has 258 for entropy_avail. VPS has 193.

Interesting.

---

