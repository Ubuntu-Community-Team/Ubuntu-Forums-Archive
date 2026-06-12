---
title: "Exclude files from Samba full_audit"
date: 2018-05-23
forum: Server Platforms
---

### Post by kowaiser on 2018-05-23
Hello everyone, and thanks in advance. I'm running a fileserver with Samba on an ubuntu server, and recently the need to log who deletes or modifies files have become quite critical.

In order to do that, i added the following lines to /etc/samba/smb.conf:

```

vfs objects = full_audit

full_audit:prefix = %u|%I|%m|%S
full_audit:success = mkdir rename unlink rmdir pwrite
full_audit:failure = none
full_audit:facility = local7
full_audit:priority = NOTICE

```

and this on /etc/rsyslog.conf
```

local7.*                        /var/log/samba/log.audit

```


The issue is that we have at all times at least 40 people accessing the fileserver, which result in a giant wall of text with .tmp files on the logs.

Is there a way to make full_audit exclude the TMP files from the audit?

---

### Post by TheFu on 2018-05-23
egrep -v?

---

