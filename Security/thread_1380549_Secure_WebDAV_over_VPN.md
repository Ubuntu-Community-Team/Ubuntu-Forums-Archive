---
title: "Secure WebDAV over VPN"
date: 2010-01-13
forum: Security
---

### Post by frogotronic on 2010-01-13
Hello,

  My workplace recently switched to Active Directory for our netdisk space (I work at a University in the US).  The "only way" (recommended) by our IT department is to use a **cifs** protocol.  I've had absolutely no luck with that at all.

  However, it turns out that there is secure WebDAV protocol setup which works well on campus.  If I'm off campus I have to connect via a VPN connection; our school uses Cisco Anyconnect 2.3.0254.  It works well for me to connect to a printer, etc on campus.

  _**Here's my problem:**_  I can't connect to my netdisk space from off-campus using the Secure WebDAV bookmark that was working oncampus, even when I am connected via the VPN connection.  I am using UFW.  Is there a port I need to open up, or am I missing something else?

Thanks,
CH

---

### Post by Lars Noodén on 2010-01-14
Sounds like a sad environment.

Usually WebDAV is secured with SSL so that you can connect with HTTPS.  
Try that first.

---

### Post by frogotronic on 2010-01-15
Yeah, its super-lame.

Well, I can get to the main server and then manually navigate to my folder, but I can't bookmark directly to my folder.  Wierd.

Thanks,
CH

---

### Post by Lars Noodén on 2010-01-15
> **cement_head said:**
> 
Well, I can get to the main server and then manually navigate to my folder, but I can't bookmark directly to my folder.  Wierd.


Would that be using SSL/TLS (HTTPS) or some VPN?

---

