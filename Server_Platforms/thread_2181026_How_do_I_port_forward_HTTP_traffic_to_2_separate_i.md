---
title: "How do I port forward HTTP traffic to 2 separate internal IP?"
date: 2013-10-15
forum: Server Platforms
---

### Post by Maheriano on 2013-10-15
I've got a computer currently running at [www.mydomain.com](www.mydomain.com) which forwards through my wireless switch to the proper computer and has been working great for years. Now I want to add an additional computer for [www.mydomain2.com](www.mydomain2.com) to forward to Apache on this second machine, how do I accomplish this? I've already forwarded all HTTP traffic coming in from port 8080 to port 80 on my second machine but when I try to go to my external IP on port 8080, it doesn't show my Apache page from that machine.

---

### Post by Maheriano on 2013-10-16
Never mind, I got it. Apparently for some weird reason in the Asus port forwarding setup, you can save all the port forwarding but it doesn't actually work until you click the apply button. Weird. I assumed if I saved it, it would become effective immediately.

---

