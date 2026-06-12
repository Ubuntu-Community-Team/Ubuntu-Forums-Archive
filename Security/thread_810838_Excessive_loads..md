---
title: "Excessive loads."
date: 2008-05-28
forum: Security
---

### Post by 1_zombie on 2008-05-28
Hi,
A friend installed ubuntu and I was messing with it whenever he looked away, however the results of one of my pranks really surprised me.

```
yes `yes`
```

I knew it would do 'something' but I wasn't expecting it to be quite so bad.    It appears 'yes' wont print anything until the second yes has returned, which means there are a lot of y's in memory.  The load shown in top was 3.6, and got to 92.0% memory.  Furthermore, neither ctrl+C/D, kill or pkill were able to stop it.  In the end I used ctrl+alt+bspc

Firstly, how should this have been stopped?  Secondly, how could I prevent something like this happening?

I was taught at school that the school ran checks to ensure processes weren't growing to quickly in order to detect malicious software.  Is there anything like this that is used in the real world?

---

### Post by Monicker on 2008-05-28
You can adjust the values in /etc/security/limits.conf to curtail the effects of runaway processes.

---

### Post by Oldsoldier2003 on 2008-05-28
> **1_zombie said:**
> Hi,
A friend installed ubuntu and I was messing with it whenever he looked away, however the results of one of my pranks really surprised me.

```
yes `yes`
```

I knew it would do 'something' but I wasn't expecting it to be quite so bad.    It appears 'yes' wont print anything until the second yes has returned, which means there are a lot of y's in memory.  The load shown in top was 3.6, and got to 92.0% memory.  Furthermore, neither ctrl+C/D, kill or pkill were able to stop it.  In the end I used ctrl+alt+bspc

Firstly, how should this have been stopped?  Secondly, how could I prevent something like this happening?

I was taught at school that the school ran checks to ensure processes weren't growing to quickly in order to detect malicious software.  Is there anything like this that is used in the real world?

you could have killed the pts on which you were running yes. ```
sudo kill -9 <processid of terminal window running bash>
``` You didnt need to kill your x-session.

---

