---
title: "problem: spontaneous changes of time zone to incorrect value and then back"
date: 2008-03-26
forum: Server Platforms
---

### Post by vak on 2008-03-26
Hi all,

approximally every 15 minutes the time zone on my Ubuntu Feisty server is reported wrong for a few minutes. Then it is self-corrected again. The global time remains correct, but the timezone is jumping ;)

Example (from apache's access log):```

      66.249.70.82 - - [25/Mar/2008:10:23:34 +0100] "GET /a/en/mp3 HTTP/1.1" 200 3770 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
      66.249.70.82 - - [25/Mar/2008:08:27:18 -0100] "GET /a/en/pki HTTP/1.1" 200 2224 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
```
(first entry is correct, second is incorrect)

the only application showing me the timestamp with a timezone on my server is apache and in its logs I namely found this trouble. Apache's community doesn't see the problem is apache-specific or due to the apache configs I did. So, I am asking here.

I did no changes to the configuration of the ntpd running. Actually, after my ubuntu has been installed, I did no configuration at all regarding time adjustments...
 

I've made check via ```
date -R; sleep 7
``` loop and can't reproduce the problem

Any hints?.. 

Thanks in advance!
Vak

---

### Post by zerocode3 on 2008-04-24
Hi!

I have the same problem on Debian Etch (with apache 2.2.3).
Have you find the solution?


> **vak said:**
> Hi all,

approximally every 15 minutes the time zone on my Ubuntu Feisty server is reported wrong for a few minutes. Then it is self-corrected again. The global time remains correct, but the timezone is jumping ;)


---

