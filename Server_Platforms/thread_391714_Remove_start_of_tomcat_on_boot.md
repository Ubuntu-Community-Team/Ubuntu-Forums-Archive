---
title: "Remove start of tomcat on boot"
date: 2007-03-23
forum: Server Platforms
---

### Post by romaluca on 2007-03-23
When i star start obuntu tomcat start automatically.
I dont want this.
I control in the session startup in the preferences but tomcat there isn't.

How i can to remove the start automatically of it?
Thanks

---

### Post by mvoorberg on 2007-03-27
I'll trade you problems.  Mine doesn't start automagically and I want it to...  ;)

When you find it, let me know!

---

### Post by graylion on 2007-03-27
rename the symlink in /etc/rc*n*.d from S20tomcat5 to K20tomcat5

---

