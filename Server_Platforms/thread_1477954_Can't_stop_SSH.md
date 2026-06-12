---
title: "Can't stop SSH"
date: 2010-05-09
forum: Server Platforms
---

### Post by EarthMind on 2010-05-09
With 10.04 I can't stop SSH anymore by running "/etc/init.d/ssh stop". I get an "OK" after executing it but it doesn't actually do anything.

---

### Post by Iowan on 2010-05-09
I haven't tried much with the new upstart/service... **man service** might provide more help. You might try:```
service ssh stop
```

---

### Post by CharlesA on 2010-05-09
> **Iowan said:**
> I haven't tried much with the new upstart/service... **man service** might provide more help. You might try:```
service ssh stop
```

That does indeed work. :)

I've seen a few threads asking how to start/stop SSH, Samba, etc lately. I think upstart has thrown a wrench into the works by changing the init.d/ scripts.

I'll adapt, but I'm sure it's frustrating for other users.

---

### Post by EarthMind on 2010-05-09
Thanks for the tip :)

---

### Post by Iowan on 2010-05-09
I presume "sudo" wasn't necessary - I forgot to add that.
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?

---

### Post by EarthMind on 2010-05-10
Correct, I was in sudo mode. And yes this problem is solved.

Thanks

---

### Post by arrrghhh on 2010-05-10
> **EarthMind said:**
> Correct, I was in sudo mode. And yes this question is sovled.

Thanks

I think he wants you to MARK the thread as solved ;)

---

### Post by EarthMind on 2010-05-10
Oh, I see.

Done.

---

### Post by Iowan on 2010-05-10
> **arrrghhh said:**
> I think he wants you to MARK the thread as solved ;)Yeah, I was kinda hoping the link would be a hint. I've marked the thread [SOLVED] :)

---

