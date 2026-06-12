---
title: "Empathy - mission-control-5 exited with status 1"
date: 2012-08-31
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by 3vi1 on 2012-08-31
For some time, I've been getting this error at login from Empathy (gnome-session-properties is set to run 'empathy -h' as a startup app):

```
There was an error while trying to connect to the Telepathy Account Manager. The error was:

Process /usr/lib/telepathy/mission-control-5 exited with status 1
```

At that point, if I close out the instance of Empathy in my system tray - and restart it - it works fine.

Anyone else been seeing this for a while?  I just now noticed it again, because I had disabled Empathy for a long while.

I'm thinking that the app is starting before some background service is ready?

---

### Post by terry_gardener on 2012-08-31
i have recently installed 12.10 again and get this problem.

---

### Post by 3vi1 on 2012-09-01
> **terry_gardener said:**
> i have recently installed 12.10 again and get this problem.

I hate to say "good" to that, but misery *does* love company.  :)  Thanks for confirming it's not just me.

I was not sure if it was just this machine, because one of my other (slower) machine never had this issue... so I wasn't sure if there was something wrong with my empathy settings.

But, I had already tried removing every online account and re-adding them all... and the problem persists.

---

### Post by sj_ on 2012-09-04
[https://bugs.launchpad.net/ubuntu/+source/telepathy-indicator/+bug/1043454]("https://bugs.launchpad.net/ubuntu/+source/telepathy-indicator/+bug/1043454")

---

