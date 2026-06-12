---
title: "Which ports to forward for Citadel"
date: 2008-08-07
forum: Server Platforms
---

### Post by devonps on 2008-08-07
Hi,

I've recently installed Citadel :) and am in the process of understanding how things work, can anyone tell me which ports  I should forward, on my router, to allow inbound Citadel traffic?

Thanks in advance,

Steve.

---

### Post by gtdaqua on 2008-08-07
Its an email server. So ideally you should allow SMTP port 25 from outside. If you are using POP3, IMAP, you should allow those ports also. Use SSL for encryption - Citadel supports this I guess. 

SMTP Port: 25
POP3 Port: 110
IMAP Port: 143 

POP3S Port: 995 (POP3 over SSL)
IMAPS Port: 993 (IMAP over SSL)

---

### Post by HermanAB on 2008-08-07
Also ports 80 HTTP and 443 HTTPS for WebCit.  

On my system I use the secure protocols and only use the insecure ones for debugging.

Cheers,

Herman

---

### Post by devonps on 2008-08-08
Would this be a standard set of ports to open, either secure or not, for a Citadel installation?

---

### Post by HermanAB on 2008-08-08
Yes.  The ports are enumerated in the admin manual on the Citadel web site, but these are the same for any mail server.

---

### Post by Harbard on 2008-10-16
As an alternative,  if your Citadel server is on it's own box, just connect it to the DMZ port of your router.

---

