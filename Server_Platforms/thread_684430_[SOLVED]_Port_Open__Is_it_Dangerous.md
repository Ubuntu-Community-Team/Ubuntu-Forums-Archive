---
title: "[SOLVED] Port Open ? Is it Dangerous ?"
date: 2008-02-01
forum: Server Platforms
---

### Post by pat_pat on 2008-02-01
I run a Firewall Test and found Three Ports Open, Is it dangerous ? How do I Close a port  :?:

---

### Post by MJN on 2008-02-01
An 'open' port implies a listening process hence to 'close' a port you would stop the process or firewall it off (which would effectively stop access to it from the outside).
 
What was the test, and what ports were open?
 
Mathew

---

### Post by wieman01 on 2008-02-01
Also, what services are running on those ports?

---

### Post by HermanAB on 2008-02-01
The fear of 'open ports' comes from the Windows world, where MS has numerous undocumented listeners in their network stack with no password challenges on most.  On Linux, an open port indicates that something is listening, but you can always tell exactly what it is and why and there is always authentication involved.

The most important network protection is long passwords.  Always use passwords with more than 8 characters, since the common brute forcers all go up to 8 characters.  All the hacked machines that I had to fix were compromised by some ***-hat thinking it wise to use a 4 character password.  

I use 16 character semi-pronounceable passwords and my machines don't get hacked.

Cheers,

Herman

---

### Post by wieman01 on 2008-02-02
> **HermanAB said:**
> The most important network protection is long passwords.  

And - I guess - security updates.

---

### Post by pat_pat on 2008-02-05
Thanks Anyway ;  I found out after I installed an security Update , It is fixed:)

---

### Post by MJN on 2008-02-05
What was the port (and update)?
 
Mathew

---

