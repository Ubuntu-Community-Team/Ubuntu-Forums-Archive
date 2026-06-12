---
title: "[SOLVED] Do any KDE or Ubuntu applications use port 27967?"
date: 2006-05-01
forum: Server Platforms
---

### Post by RavenOfOdin on 2006-05-01
I just had a strange entry pop up on my Firestarter log when something tried to get out using that port. 

It was TCP traffic, and neither chkrootkit nor rkhunter show anything. Nor do the last - utilities.

What could this have been?

---

### Post by LordHunter317 on 2006-05-01
[QUOTE=RavenOfOdin]I just had a strange entry pop up on my Firestarter log when something tried to get out using that port.

It was TCP traffic, and neither chkrootkit nor rkhunter show anything. Nor do the last - utilities.

What could this have been?[/QUOTE]Did you start an outgoing connection?  All outgoing connections will use higher numbered ports in that range.  Could have been anything.

---

### Post by souki on 2006-05-01
try this to identify the process
```
netstat -anp | grep 27967
``` ```
lsof -i -nP | grep 27967
```

---

### Post by RavenOfOdin on 2006-05-11
Tried it. Can't get the connection before it goes down. 

I think I was using Konqueror before that, and every single time the transmits have been to 66.83.137.5

---

