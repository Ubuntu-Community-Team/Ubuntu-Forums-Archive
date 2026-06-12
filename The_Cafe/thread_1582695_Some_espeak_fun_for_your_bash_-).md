---
title: "Some espeak fun for your bash :-)"
date: 2010-09-26
forum: The Cafe
---

### Post by youbuntu on 2010-09-26
Just a little script I wrote, to have some basic info about your system:

```
(echo ping result to localhost is; ping localhost -c 1 | awk '/ttl/  {print $8}';echo milliseconds; echo your username is; whoami;echo you  are in; pwd; echo this linux box has been up for; uptime | awk '{print  $3}'; echo minutes. Your home directory listing is; cd ~/; ls; echo I  have had enough of being your slave. I am off for a break. Good bye) |  espeak
```Copy/paste to shell - enjoy this!

---

### Post by kostkon on 2010-09-26
Lol, nice. Although, the *cd ~/; ls;* can take a lot of time :P

---

### Post by matthew.ball on 2010-09-26
Cool!

---

### Post by Legendary_Bibo on 2010-09-26
This is my fresh prince of bel air espeak shell script. This was before I knew you could put words in quotes, so there's an underscore between each work.

---

