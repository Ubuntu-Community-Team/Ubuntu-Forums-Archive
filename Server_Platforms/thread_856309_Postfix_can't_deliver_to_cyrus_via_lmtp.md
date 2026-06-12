---
title: "Postfix can't deliver to cyrus via lmtp"
date: 2008-07-11
forum: Server Platforms
---

### Post by dcroxton on 2008-07-11
I'm migrating a cyrus + postfix server to Ubuntu Hardy.  Everything else works -- old mail is migrated, I can read it, and I can send mail -- but I can't receive mail.  It gets stuck in postfix, with the error "warning:  connect #[x] to subsystem private/lmtp:  Connection refused".

I discovered that the lmtp socket in Hardy is, by default, /var/run/cyrus/socket/lmtp, and I set master.cf accordingly.  I saw one warning that the file needs to be accessible to both the cyrus and the postfix users.  The /var/run/socket directory is owned by cyrus:mail, and has permissions of 740.  The lmtp file itself is owned by root:root, but has permissions of 777.  (Actually, the permissions line reads "srwxrwxrwx"; I can't remember what the leading "s" means.)  I don't know what user postfix runs as.

Thanks far any help you can provide.

Sincerely,
Derek

---

