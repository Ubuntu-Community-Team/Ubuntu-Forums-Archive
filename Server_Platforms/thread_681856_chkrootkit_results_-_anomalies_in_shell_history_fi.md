---
title: "chkrootkit results - anomalies in shell history files"
date: 2008-01-29
forum: Server Platforms
---

### Post by Frank98 on 2008-01-29
After running chkrootkit I received the following warning.

Searching for anomalies in shell history files... Warning: `' is linked to another file

Does anyone know what this means? I tried searching google for this specific warning "Warning: `' is linked to another file" but didn't find any information.
Thanks in advance for any and all help.

---

### Post by john.allen@dublinux.net on 2008-03-19
This is a bug in chkrootkit. It executes the find command without "-type f", so finds .history directories which by definition have a link count of 2, and reports them as an issue.

---

