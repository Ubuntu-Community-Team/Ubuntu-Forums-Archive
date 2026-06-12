---
title: "Question regarding AppArmor"
date: 2009-12-17
forum: Security
---

### Post by toadlife on 2009-12-17
I have a question about AppArmor in Ubuntu. Does apparmor restrict program that do not have a profile assigned to them...like via a default "catch-all" profile?

For example, if I downloaded a piece of software from a third party site and compiled it myself, would apparmor restrict the resulting binaries?

Thanks!

---

### Post by FuturePilot on 2009-12-17
No, if it doesn't have a profile, AA doesn't know about it.

---

### Post by toadlife on 2009-12-17
> **FuturePilot said:**
> No, if it doesn't have a profile, AA doesn't know about it.


Thanks. I read the through some of the summary docs but they were clear as mud on this particular issue.

---

