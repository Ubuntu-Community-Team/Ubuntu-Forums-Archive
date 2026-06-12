---
title: "security question ?  --MARK-- ?"
date: 2007-05-30
forum: Server Platforms
---

### Post by firedancer on 2007-05-30
i'm a newbie so if i have it wrong , i have it wrong 


but twice (and i have been attacked violently a few times in the past , that's one of the reasons i switched), things shut off without me wanting or doing something to do that, just working on O.O. (open office)


in my system log i find    :

May 30 10:03:29 dragon-desktop hald: mounted /dev/sda1 on behalf of uid 1002
May 30 10:17:01 dragon-desktop /USR/SBIN/CRON[7827]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 30 10:27:02 dragon-desktop -- MARK --  [COLOR="Red"]here is when my rythmbox went dead [/COLOR]
May 30 10:47:02 dragon-desktop -- MARK -- 

is this somethig to worry about or not and what is MARK all about , had it once after fresh install and thought it was an intruder , i'm not so good at this, i don't mind ppl watching me , but can't afford a crashed system

i'm graduate dramastudent without a studyloan nor a job , this last year need all my time (bread and water is fine, but i need my pc 

looking forward to and explainable answer

---

### Post by MKR. on 2007-05-30
That's just the logger daemon's way of saying "The system was working fine at this time." It's useful for finding out what is causing a system crash, because it helps identify when it likely happened.

---

### Post by firedancer on 2007-05-30
thnx for the insight 


found out what made it stop has something to do with 'buffering' it's a problem with the radiostream i 'm listening to,  rythmplayer is playing good now , just have to check other station (url) 



many thnx MKR 
(i thought it was MARK self, :D)

---

