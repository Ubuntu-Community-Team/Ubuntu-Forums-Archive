---
title: "xsession-errors no more rotated ?"
date: 2012-03-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by dino99 on 2012-03-10
Usually we was starting a new xsession-errors log on each log out/in or cold boot. But since a few days its no more the case. Have you seen the same issue on your system ?

---

### Post by mc4man on 2012-03-10
i noticed that a couple of days ago, but it didn't really register what was happening.
Not going to be good, i've got 20K lines today

---

### Post by dino99 on 2012-03-10
> **mc4man said:**
> i noticed that a couple of days ago, but it didn't really register what was happening.
Not going to be good, i've got 20K lines today

is that an rsyslog problem or something else like conf settings changed ?

---

### Post by mc4man on 2012-03-10
Don't know - can't see any use of having a 'forever' xsession log, seems worth a bug report (maybe on lightm?

Ot - did you happen to notice our little bug on pitfdll was finally dealt with after 4 releases

---

### Post by dino99 on 2012-03-10
> **mc4man said:**
> Don't know - can't see any use of having a 'forever' xsession log, seems worth a bug report (maybe on lightm?

Ot - did you happen to notice our little bug on pitfdll was finally dealt with after 4 releases

pitfdll is removed here since a while as it seems not needed anyway but was disturbing the video processes.

---

### Post by mc4man on 2012-03-10
Downgrading lightdm/liblightdm-gobject to 1.1.6 restores previous behavior, see nothing in the changelog for 1.1.7 other than 'new upstream' so a bug on lightdm would seem appropriate

---

### Post by dino99 on 2012-03-10
> **mc4man said:**
> Downgrading lightdm/liblightdm-gobject to 1.1.6 restores previous behavior, see nothing in the changelog for 1.1.7 other than 'new upstream' so a bug on lightdm would seem appropriate

interesting, will report against lightdm: [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/951597](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/951597)

---

### Post by mc4man on 2012-03-11
Did a new  install today, xsession-errors is now totally worthless.
Was written to only on the 1st session or so, then it stops completely & just shows the same thru restarts. log outs 

So it's not replaced & it's being treated as if it was modified which prevents any further writing to

---

### Post by dFlyer on 2012-03-17
Same problem with xsession-error since upgrading to beta 1

---

### Post by lucazade on 2012-03-24
this issue is still present on my system. :/

---

