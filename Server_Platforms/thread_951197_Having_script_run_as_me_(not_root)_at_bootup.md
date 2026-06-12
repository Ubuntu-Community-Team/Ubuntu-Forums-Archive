---
title: "Having script run as me (not root) at bootup"
date: 2008-10-17
forum: Server Platforms
---

### Post by filburt1 on 2008-10-17
I'd like to have a custom Bash script run when I boot up my server running Ubuntu 8.04 Server AMD64, but it needs to run as me and not as root, which I can't seem to figure out using rc.local.

The server doesn't run X (nor have it installed, for that matter) and most of the time, nobody is even logged in. I can't put it in my .bashrc because it requires an interactive login and I want this to happen during the bootup process as pretty much the last thing to run.

Thoughts?

---

### Post by promodus on 2008-10-17
have one script start another

```
exec sudo -u your_user your_script
```

---

