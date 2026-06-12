---
title: "Best update procedures"
date: 2009-07-12
forum: Server Platforms
---

### Post by dragos2 on 2009-07-12
I am wondering what is a good update procedure.

For example when I must do a serious update I:

- make sure that the updated packages won't break existing
  software/services/processes
- make sure that the server is not being used at that time
- make sure I am the only one from the system and disable
  other users from logging in
- stop big processes/services (like Oracle)
- perform the update
- start all previously stopped services/processes
- reestablish user access

The backup is not discussed here.

Some people enters in single user mode and some never reboots
to preserve uptime.


How do you do it ?

---

