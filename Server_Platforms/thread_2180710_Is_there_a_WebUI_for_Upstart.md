---
title: "Is there a WebUI for Upstart ?"
date: 2013-10-14
forum: Server Platforms
---

### Post by p_m2 on 2013-10-14
I would need a webUI for upstart, so i can give limited access to my power users to start & stop services. Or at time restart hung services?

---

### Post by ian-weisser on 2013-10-14
Not to my knowledge.
Non-admins should generally not be using (system-level) upstart directly.

If a process hangs without upstart automatically detecting and resetting it, please file a bug report. That's upstart's job, and the developers would like to know about that.
Upstart does, by the way, have a dbus interface. You can create a UI, launcher, or AppIndicator that talks to upstart without getting all wrapped up in permission issues.

---

