---
title: "ad hoc WIDS"
date: 2012-10-30
forum: Security
---

### Post by Leo Matheus on 2012-10-30
Well, here im again!

Today i want to know if there is any wids that works in an ad hoc wireless network. I have some nodes, and i need that he can detect in all of them. :)

---

### Post by Leo Matheus on 2012-10-30
oh, i have forget, im using dd-wrt routers

---

### Post by chadk5utc on 2012-10-31
Im not %100 sure what your looking for if your looking for wireless intrusion detection or prevention there are a number of howto's online heres one
[http://sagan.quadrantsec.com/papers/wireless-ids/](http://sagan.quadrantsec.com/papers/wireless-ids/)
perhaps you can post more information as to what your trying to do?

---

### Post by Leo Matheus on 2012-11-01
well, i have an ad hoc network, and i this network is connect with an eternet network, that provide some services for the wireless one. I need to see any attack that come to the wireless to the wired network. I have an IDS working in the border of the networks, but It would be really good if i can be able to detect on the 802.11 network.

---

### Post by chadk5utc on 2012-11-01
ok I think I understand better. what I would do then is setup remote logging from all your DD-WRT routers and send those logs to your IDS for analizing. I believe that each of the DD-WRT have the option for remote syslog. I would pay close attention to logs. possibly setup Kismet/Snort or some other packet analyzer. Are these Dual band routers?

---

### Post by Leo Matheus on 2012-11-08
well, i have tried that, but its look like they cant process this kind of logs.

---

