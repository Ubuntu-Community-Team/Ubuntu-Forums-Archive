---
title: "Samba PDC and Windows Server 2003 PDC"
date: 2010-02-11
forum: Server Platforms
---

### Post by renierengelbrecht on 2010-02-11
Hi there,
I come from a background where SAMBA PDC was the only domain server. However, at my new word they are running windows server 2003. They do not want to give this up as they do not know linux.
I want to establish my own ubuntu server with its own PDC runnning my own division. 
Is there going to be any conflict between the two servers?

---

### Post by wgarider on 2010-02-11
If I understand your question - you want to create a new domain on a Samba server.....it would be a seperate domain from the existing one or would be a child domain of the existing domain?

If it's a seperate domain, no problem, if it's a child of the existing domain, I don't know enough about Samba to say for sure but I would think all you'd need is a domain admin account in order to set that up.

---

### Post by renierengelbrecht on 2010-02-11
Yes, it would be a separate domain from the current domain. Thank you for the advice.

---

