---
title: "ssh protocol"
date: 2013-10-05
forum: Server Platforms
---

### Post by remo2 on 2013-10-05
What version of ssh (protocol) to use ubuntu 10.04 (1, 2, or both)?
Where is the file protocol layer is defined? In the same file (ubuntu 10.04), the setting PermitRootLogin yes PermitRootLogin should be changed to no. Why do you think this should be treated?

---

### Post by Lars Noodén on 2013-10-05
Are you talking 10.04 for the server or the desktop?  For the desktop, support ended on May 9, 2013 and it would be best if you upgrade to a supported version.  **Protocol** is set in /etc/ssh/sshd_config with the directive **Protocol**.  Recent versions of sshd use only protocol 2 and you should retrofit your old systems to use only 2 as well.  In practice, I am fairly sure that no one has been using older versions for the last 10 years.  

About the *PermitRootLogin* misconfiguration. It should be set to **no** or at least **without-password**or **forced-commands-only**.  But really it  should not be allowed. sudo, even for scripts, is preferable.  It is possible to use sudo even with "passwordless" key logins, it just requires some tuning.  IMHO **no** should be the default in Ubuntu.  If you file a bug on that, post it here so we can add to it.

---

