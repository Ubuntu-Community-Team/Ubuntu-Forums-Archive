---
title: "Priorities"
date: 2008-09-30
forum: Server Platforms
---

### Post by Kismet on 2008-09-30
I just had a couple quick questions on setting process priorities.

I am running tomcat servers connected to a postgresql db.

With each new tomcat connection, a new postgres process is started with what's shown as priority 0.

If I renice the top level process will its children be higher priority too?
If I do this it lists the top level as -5 for instance, but all its children still say 0!

Of course I could just do something like ps -e | grep postgres | renice ... but even if I worked that out, it would only renice the current spawned processes. 

Long story short:
Is there a way to renice an entire process tree, and ensure new processes spawned retain that higher priority?

Thanks

edit:
Also, is it worthwhile to additionally ionice postgresql with a higher priority. My system is 4 scsi's in raid and I'm just looking to maximize performance.

---

### Post by Kismet on 2008-10-01
No one knows?

---

### Post by HermanAB on 2008-10-01
You will likely find that the present Linux scheduler is so good that twiddling the process priorities makes no appreciable difference.

Cheers,

Herman

---

