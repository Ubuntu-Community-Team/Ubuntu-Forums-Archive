---
title: "Multi-Core monitoring?"
date: 2010-04-20
forum: Server Platforms
---

### Post by TuckLive on 2010-04-20
I'm about to build a quad core server.  Can I monitor each core's performance from the command line?  What can I use?

---

### Post by VeeDubb on 2010-04-20
I think covers it pretty well.

[http://www.cyberciti.biz/tips/how-do-i-find-out-linux-cpu-utilization.html](http://www.cyberciti.biz/tips/how-do-i-find-out-linux-cpu-utilization.html)

In particular

```
mpstat -P ALL
```

---

### Post by iponeverything on 2010-04-20
htop is good for giving a per-core in real time.

---

### Post by TuckLive on 2010-04-20
Thanks guys!  I was hoping top had a command.

---

