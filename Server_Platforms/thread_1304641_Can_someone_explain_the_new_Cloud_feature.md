---
title: "Can someone explain the new Cloud feature?"
date: 2009-10-29
forum: Server Platforms
---

### Post by jondecker76 on 2009-10-29
I've read the cloud writeup on the Ubuntu website several times and i still don't understand what its for or its practical uses.  Can anyone clear this up for me?

thanks

---

### Post by Ghostbear121 on 2009-10-29
Sure, it's a pretty neat idea -- basically you have a bunch of servers connected together, and all their resources are pooled.  This is the "cloud", and you send processes and stuff directly to the cloud, instead of to an individual server.  The cloud then allocates enough resources to do that task. 

It's sort of like clustering several servers together, but instead of connecting only one process (like a clustered Apache server), you actually connect whole computers which can share CPU load and memory.  The OS takes care of the sharing part, whereas with clustering you need specific applications that can take advantage it.

---

