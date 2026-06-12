---
title: "domain names forwarding to router homepage"
date: 2008-03-12
forum: Server Platforms
---

### Post by cshelswell on 2008-03-12
I had a server running ubuntu perfectly the other day with zoneedit pointing my domain ([www.sueandmike.net](www.sueandmike.net)) to my server and the site displaying fine.

The other day though i had to reset my wireless router (the server takes it's feed out of an ethernet port on it) and now typing my domain in just directs me to my router login page. If i type the ip of the server it seems to work (192.168.1.100).

All my port-forwardings on the router seem to have reset could that be it? Can't quite figure this out.

Many thanks

---

### Post by Steveway on 2008-03-12
Did you do that from inside the local network or from the outside?
If inside, then it is normal behaviour, at least mine does that,too.
A solution is to change your hosts file on your computer to point that domain to the servers IP.

---

### Post by cshelswell on 2008-03-12
its inside. But it never used to do that. I have just upgraded my modem could that be it? Can you access it?

Cheers

---

### Post by cshelswell on 2008-03-12
Sorted - turns out i just needed to open port 80 on my router to the server.

Cheers

---

### Post by Steveway on 2008-03-12
> **cshelswell said:**
> Sorted - turns out i just needed to open port 80 on my router to the server.

Cheers

Good that you figured that out. Don't forget to mark this thread as solved.
Your server loads very fast, good work.

---

