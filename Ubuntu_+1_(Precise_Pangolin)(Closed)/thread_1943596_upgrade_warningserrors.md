---
title: "upgrade warnings/errors"
date: 2012-03-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Gregory Lee on 2012-03-19
I sometimes notice warnings or errors in the output of "aptitude safe-upgrade".  Should I do anything about these?  Here are a couple:
```
[3/17, 10am]
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.

[3/19, 1pm]
Processing triggers for libglib2.0-0 ...
Unable to open directory /usr/lib/gio/modules: Error opening directory '/usr/lib/gio/modules': No such file or directory
[/usr/lib/x86_64-linux-gnu/gio/modules/ exists -- I made a link to it]
```For the second message, as noted, just guessing, I made a soft link to another directory which I thought might be the intended one.

---

