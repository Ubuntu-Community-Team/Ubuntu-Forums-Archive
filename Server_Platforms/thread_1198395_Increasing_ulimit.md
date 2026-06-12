---
title: "Increasing ulimit"
date: 2009-06-27
forum: Server Platforms
---

### Post by zemon_ on 2009-06-27
How do I increase the ulimit for the utorrent process?

Thanks in advance

---

### Post by jhannah on 2009-06-30
Isn't uTorrent a Windows client? ulimit applies per-shell and would need to be modified before running application in that shell (or you could push it to the back with job control, namely by pressing Ctrl-Z). Am I misunderstanding what you are asking?

---

### Post by kerry_s on 2009-07-01
"man ulimit" should help you.

---

