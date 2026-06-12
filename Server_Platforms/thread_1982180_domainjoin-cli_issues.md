---
title: "domainjoin-cli issues"
date: 2012-05-18
forum: Server Platforms
---

### Post by Manyrootsofallevil on 2012-05-18
I ran domainjoin-cli to join a test machine (running ubuntu 12.04) to a Windows AD domain and it seems to have worked, except that the DNS server is not updated.

I've joined a RHEL machine to this domain and the DNS server was updated, so it's not an issue with the DNS server, which is allowing Nonsecure and secure updates.

Any ideas?

TIA

---

### Post by Manyrootsofallevil on 2012-05-18
I found the *lw-update-dns* command which seems to do the trick

---

