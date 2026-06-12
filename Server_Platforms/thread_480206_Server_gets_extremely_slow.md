---
title: "Server gets extremely slow"
date: 2007-06-21
forum: Server Platforms
---

### Post by Rizado on 2007-06-21
I have an old macintosh powermac 466mhz running as a server at home. Most things are working great and all but there's one very annoying thing. After some time it becomes very slow, right now it has been up 47 days and it's almost unusable. The routing and nfs services work perfectly and it has 400mb free ram. Running top will not show anything unusual. When logging in through ssh it takes probably a minute before it's usable and restarting apache is ridicolous. 

What can it be? I'd rather not reboot it all the time.

---

### Post by Widodh on 2007-06-21
What does your "kern.log" and "dmesg" (is a command say)?

And what does "free -m" say, is your machine swapping?

---

### Post by Rizado on 2007-06-21
> **Widodh said:**
> What does your "kern.log" and "dmesg" (is a command say)?

And what does "free -m" say, is your machine swapping?Nothing out of the ordinary, only thing I don't really know what it is is: "Ingress scheduler: Classifier actions prefered over netfilter"

-/+ buffers/cache: 400mb free out of 512. No swap used.

Anyway I think I managed to fix it, I uninstalled xinetd and a vnc server that was running, suddenly gzip used 99% cpu. Killed that and the system is much more responsive now. No ports have been opened and vnc has not been accessed.

---

