---
title: "IP and Updates"
date: 2010-04-08
forum: The Cafe
---

### Post by shadowfax1 on 2010-04-08
Running 10.4 beta on my desktop and laptop and a thought just occurred to me that when either machine draws updates its a one time event to that ip which means the other machine wouldn't be getting that specific update and visa versa?

---

### Post by stilling on 2010-04-08
i belive that ubuntu just search your packages on your pc and see if need update or not so the answer is it does not matter if is 1 ip and 5 system for update and upgrade



hope this helps

---

### Post by cariboo on 2010-04-08
I have lucid running on three different systems, they all get the same updates. The only thing is, that because all three use the same external ip address, It only counts as one installation.

---

### Post by tica vun on 2010-04-08
> **cariboo907 said:**
> I have lucid running on three different systems, they all get the same updates. The only thing is, that because all three use the same external ip address, It only counts as one installation.

Canonical claims they don't use "phone home" to determine usage statistics, so this doesn't really matter.

---

### Post by lovinglinux on 2010-04-08
I don't think the OP is worried about statistics. Perhaps I completely misunderstood the post, but looks to me the OP wanted to be able to update all machines on the same IP, when running the update-manager from one of the machines.

---

### Post by cariboo on 2010-04-08
Canonical counts unigue ip addresses to count the number of users connecting to the repositories, to get an estimate of how many people are using Ubuntu.

We all know Ubuntu phones home every time you do an update. :)

---

### Post by cariboo on 2010-04-08
> **lovinglinux said:**
> I don't think the OP is worried about statistics. Perhaps I completely misunderstood the post, but looks to me the OP wanted to be able to update all machines on the same IP, when running the update-manager from one of the machines.

The op should have a look at apt-cacher then, it is in the repositories.

---

### Post by kenweill on 2010-04-08
> **cariboo907 said:**
> Canonical counts unigue ip addresses to count the number of users connecting to the repositories, **to get an estimate of how many people are using Ubuntu.**

We all know Ubuntu phones home every time you do an update. :)

In that case, it can't estimate on how many people are using ubuntu in the philippines, with SmartBro as their ISP.

All of us in our area, have the same public IP address. We just have different private ip address. As if, we all are connected to a wireless wide area network. The ip address we get from the ISP starts with 192.168.X.X. Another whole town got another public IP address.

---

### Post by Artemis3 on 2010-04-09
IIRC its a simple apt-get update daily, if new packages are available, update-manager will tell you. IP plays no role, except maybe unreliable statistics for Canonical ^_^

You can always enable Send statistics for package usage in the place you add repositories; see the rankings here: [http://popcon.ubuntu.com/](http://popcon.ubuntu.com/)

---

