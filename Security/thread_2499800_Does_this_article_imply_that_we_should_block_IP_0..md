---
title: "Does this article imply that we should block IP 0.0.0.0?"
date: 2024-08-11
forum: Security
---

### Post by Paddy Landau on 2024-08-11
I read that browsers are susceptible to an old vulnerability that accesses IP address 0.0.0.0

[https://thehackernews.com/2024/08/0000-day-18-year-old-browser.html](https://thehackernews.com/2024/08/0000-day-18-year-old-browser.html)

I've read that Chromium (and therefore Chrome, Edge, etc.) is currently being patched to remove this vulnerability.

But, it made me wonder: Should we, as a matter of course, block 0.0.0.0? (This is for a standard desktop user.)
```
sudo ufw deny from 0.0.0.0 to any
```

---

### Post by currentshaft on 2024-08-11
.

---

### Post by Paddy Landau on 2024-08-11
Thanks, @currentshaft. I didn't fully understand the problem, obviously.

I use Chrome, and they're busy fixing the vulnerability, so I'll wait for them to do the job.

I'll mark this thread as solved.

---

