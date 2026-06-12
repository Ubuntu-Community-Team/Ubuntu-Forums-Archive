---
title: "AVG not testing all files"
date: 2008-02-27
forum: Security Discussions
---

### Post by ubacct3 on 2008-02-27
I'm running AVG for Linux, and when I choose to run a complete test, it only does about 2000 to 5000 files.  When I chose only one of my USB HD drives, it searched all 20,000 files.  

So when I run my complete test, I know it should search at least 25,000 files, but it stops very quickly.  Any idea why?

---

### Post by Omnios on 2008-02-27
This sounds like it might be a permissions problem. When run as user it would allow you to scan your home folders but themain linux stuff is owned by root. Not shur how to fix that but gives a place to start.

---

### Post by ubacct3 on 2008-02-27
> **Omnios said:**
> This sounds like it might be a permissions problem. When run as user it would allow you to scan your home folders but themain linux stuff is owned by root. Not shur how to fix that but gives a place to start.

I run the application with sudo privileges, so I'm not sure either.

---

### Post by ./. on 2008-03-01
If I run AVG as a regular user, I normally encounter about 35 locked files.

So I just type "sudo avggui" from the Command Line.  AVG then scans and reports only one locked file.  As mentioned, it's probably something to do with permissions.

---

