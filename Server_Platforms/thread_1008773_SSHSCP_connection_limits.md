---
title: "SSH/SCP connection limits"
date: 2008-12-11
forum: Server Platforms
---

### Post by pjennings on 2008-12-11
Is there a default limit on the number of ssh or scp connections from a remote network within a certain amount of time on 8.10?  I have a script that runs scp a few times successively and the last couple of them seem to time out.  After that I can't connect with ssh for a few minutes from the same IP, but I can from a different address.  I am using shared key authentication.  The logs only show successful authentications.  Am I missing a config option somewhere?

---

### Post by pdtpatrick on 2008-12-12
check your sshd conf files to see what parameters you have set in there.

/etc/ssh/ssh_config (this is the client form)

---

