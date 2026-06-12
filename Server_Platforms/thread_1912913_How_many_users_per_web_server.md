---
title: "How many users per web server"
date: 2012-01-21
forum: Server Platforms
---

### Post by t_ras on 2012-01-21
Considering I can buy strong severs (well at least severs for arroun 10K$ ;) )
How many users per web server I can get if I run a facebook lite like apllication?

Thanks for the answer.

---

### Post by TFroehlich3 on 2012-01-21
> **t_ras said:**
> Considering I can buy strong severs (well at least severs for arroun 10K$ ;) )
How many users per web server I can get if I run a facebook lite like apllication?
 
Thanks for the answer.
 
 
 
A server like that can manage A LOT! But another important factor is the internet connection. You would have to have at least business class cable internet.... At the very least, if you can get a fiber optic connection, do it.

---

### Post by t_ras on 2012-01-21
of course it will be hosted in a profetional farm

---

### Post by kevinthecomputerguy on 2012-01-22
Facebook is comprised of servers all over the world, with over 10 backups for every location, each with its own LVM snapshots over raid. $10K wont get you anything like facebook. But without redundancy and global positioning in your question, and without ISP costs mentioned above, i would say for every 1,000 dollars of server hardware you could support 1,000 reads. Writes and authenticated databases writes is a whole other chapter. You compared your ideas to the biggest social networking site in the world :- )

---

### Post by t_ras on 2012-01-22
1) of course I didnt meant I will buy only one server, I was thinking of a few docens.
2) I only need to take care of web, DB is taken care of
3) of course I'm not planning to be facebook, I was thinking of a hundred thousand users at most. just a similar type of application.
4) Thanks for the answer :)

I'll clarify my self better next time.

---

### Post by SeijiSensei on 2012-01-23
I'd consider starting with one or more virtual servers from a reputable company like Linode.  You can get a pretty [substantial server]("https://manager.linode.com/signup/#plans") from them for $500 per month or so.  That gives you a lot more flexibility to expand as your business grows.  

If you're uncomfortable with a virtual server, then renting physical servers from hosting companies is another good option.  I wouldn't invest in hardware at the outset.

I'd spend a lot more on marketing than I would on server resources if you're just starting out.

---

### Post by t_ras on 2012-01-23
Thanks for the answers.

---

