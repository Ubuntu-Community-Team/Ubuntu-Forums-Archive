---
title: "OpenSSH &amp; Blowfish"
date: 2011-03-07
forum: Security
---

### Post by mimor on 2011-03-07
I've read that blowfish encryption is much faster and still safe enough to transfer files between hosts.

What's the default encryption used by openSSH? (if not already blowfish):confused:

---

### Post by DZ* on 2011-03-07
> **mimor said:**
> I've read that blowfish encryption is much faster and still safe enough to transfer files between hosts.

What's the default encryption used by openSSH? (if not already blowfish):confused:

man ssh_config says: The default is "3des"
You can change that by editing /etc/ssh/ssh_config ("Cipher" line)

---

### Post by mimor on 2011-03-07
Ok. Thx, I'll check that out later on. :guitar:

---

