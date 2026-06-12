---
title: "Apache2 crashing."
date: 2009-01-30
forum: Server Platforms
---

### Post by Initsil on 2009-01-30
Hey Ubuntu Community.

I've been having trouble with apache2. I'm running Ubuntu 8.04. I'm not sure what I can do at this point. But every so often(a few times a day) apache2 overflows. What happens is:

-Websites on my server get lots of visitors.
-I run htop, server load is high and swap starts getting used. 
-If I'm lucky I can run killall apache2 and it'll stabalize. 

If I don't get to it in time I have to unplug it from the wall and plug it back in. 

Any ideas on how to optimize apache2? Or anything I can do at all?
I have 256MB's of ram on the server.:D

---

### Post by volkswagner on 2009-01-30
What type of sites are you running, PHP, mysql backends, etc.?

---

### Post by albinootje on 2009-01-30
> **Initsil said:**
>  Any ideas on how to optimize apache2? Or anything I can do at all? I have 256MB's of ram on the server.:D

Check this thread :
[http://ubuntuforums.org/showthread.php?t=117073](http://ubuntuforums.org/showthread.php?t=117073)
-> comment nr. 4

---

