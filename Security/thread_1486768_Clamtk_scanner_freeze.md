---
title: "Clamtk scanner freeze"
date: 2010-05-18
forum: Security
---

### Post by joeman225 on 2010-05-18
Hi all,

I've been trying to run some malware/virus scans on with ClamTK, but I've been hitting a snag. The program keeps freezing up when I scan File System, and freezes on one specific file... Could this file be infected? How can I get the scan to proceed normally?

---

### Post by cariboo on 2010-05-18
What's the name of the file it chokes on?

---

### Post by joeman225 on 2010-05-18
Thanks for your reply.

The name of the file it stops on is /home/.ecryptfs/alla...Gu.0h1UbGslk-pEcN7Bc6---...

---

### Post by the_phenom on 2010-05-18
If that's an encrypted filesystem, you could try adding /home/.ecryptfs to the whitelist.

---

### Post by cariboo on 2010-05-18
+1 for whitelisting the /home/.encryptfs directory, because you are already logged on so the home directory is decrypted, why scan the encrypted directory too?

---

