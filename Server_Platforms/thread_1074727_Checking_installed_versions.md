---
title: "Checking installed versions"
date: 2009-02-19
forum: Server Platforms
---

### Post by creolbuay on 2009-02-19
I was wondering if there was a command I could use to show what version of different software is installed on a server. Say for example... Apache released a httpd patch and I want to ensure I have the latest package installed. I want to do this for all the other software I have installed.  Maybe something that produces a list of everything installed and the current version installed?

I really appreciate your time.

---

### Post by cdenley on 2009-02-19
```

dpkg -l apache*|grep -e ^i

```

---

### Post by creolbuay on 2009-04-30
Thanks for the reply. Sorry for the long delay, been super busy in training classes at work.

This thread can be closed as resolved.

---

