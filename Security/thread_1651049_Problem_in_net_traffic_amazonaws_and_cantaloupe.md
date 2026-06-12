---
title: "Problem in net traffic: amazonaws and cantaloupe"
date: 2010-12-22
forum: Security
---

### Post by agrgal on 2010-12-22
First of all, please forgive my poor English. 

I came across a scaring problem, surfing on the net. Webpages downloaded slowly, so I checked my physical connection and everything seemed to work fine.

But I noticed there was an unusual uploading traffic, as if data was being picked up. So I checked traffic list in Firestarter.

And there was an IP (174.129.241.144, and another one afterwards ...193.12) which was connected and belonged to amazonaws.com. As I didn't know what's going on I banned both connections and, after a while, have seemed to stop connecting.

I read something about amazons but I haven't understood what does exactly. Have they tried to catch some HD storage space to be hired on the net? Have I activated it using a specific program or web? Can I figure it out?

Later on, I realised another connection was activated: cantaloupe.canonical.com. It is joined to Ubuntuone which I activated recently, I suspect? It doesn't use up so much bandwidth as the former one did.

I haven't made up my mind. Whatever information you can share with me, it will be welcome. Thank you. Must I be worried?

---

### Post by The Cog on 2010-12-22
Next time you get unexpected connections like that, try the command 
**sudo netstat -pant**
to see what processes are connecting where. This should give a good clue.

---

### Post by cariboo on 2010-12-22
Did you have Ubuntuone setup and enabled? If you do, that is what you were probably seeing. Ubuntu uses Amazon's EC2 network for Ubunutone.

---

