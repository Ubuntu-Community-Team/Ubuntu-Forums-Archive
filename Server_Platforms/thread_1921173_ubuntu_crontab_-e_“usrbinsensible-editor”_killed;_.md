---
title: "ubuntu crontab -e “/usr/bin/sensible-editor” killed; signal 9 (no core dumped)"
date: 2012-02-06
forum: Server Platforms
---

### Post by nfxpnk on 2012-02-06
```
Welcome to Ubuntu 11.04 (GNU/Linux 2.6.32-042stab037.1 x86_64)
user@server:~$ crontab -e
no crontab for user - using an empty one

Select an editor.  To change later, run 'select-editor'.
  1. /bin/ed
  2. /bin/nano        <---- easiest
  3. /usr/bin/mcedit
  4. /usr/bin/vim.basic

Choose 1-4 [2]: 2
crontab: "/usr/bin/sensible-editor" killed; signal 9 (no core dumped)
Received SIGHUP or SIGTERM
Error writing /tmp/crontab.qcuMPr/crontab.save: No such file or directory
Buffer not written to /tmp/crontab.qcuMPr/crontab.save: No such file or directory
```

Why is this happening?

---

