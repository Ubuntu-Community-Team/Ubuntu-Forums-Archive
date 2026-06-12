---
title: "Internal IP works, external doesn't..."
date: 2009-03-03
forum: Server Platforms
---

### Post by Maheriano on 2009-03-03
I've had this working for months but now for some reason it doesn't. I shut down my machine a few days ago and today I booted it up again. I logged into Webmin to make sure that's working, I restarted Apache to make sure that's working. I pointed my browser to 10.0.0.6 and that's working but when I try to visit my external IP (68.144.96.XXX), it's a page not found. I logged into my router to make sure I still have port 80 forwarded to 10.0.0.6 which I do, but for some reason it's still not resolving. Any ideas?

---

### Post by Maheriano on 2009-03-03
Okay, wierd, it fixed itself.

I enabled Apache on another machine, forwarded the router to that machine (10.0.0.2) and it worked. So I then forwarded the router back to the main server and it worked for that one too. Oh well, working now.

---

