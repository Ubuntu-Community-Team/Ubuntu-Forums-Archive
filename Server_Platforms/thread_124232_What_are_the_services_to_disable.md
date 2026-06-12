---
title: "What are the services to disable?"
date: 2006-02-01
forum: Server Platforms
---

### Post by Leo_01 on 2006-02-01
After reading some post here... It seems there are a few services in linux which is open to attacks...
can anyone list them and what are the ways to secure or disable those services?

---

### Post by alamba on 2006-02-01
Base rule...only expose services that u require. I use nmap to typically check which ports are open and by which service. If i don't use them I close them. As far as possible I only keep a port open (typically things like ssh) for as long as I'm using it.

Akshay

---

