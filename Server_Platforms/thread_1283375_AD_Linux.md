---
title: "AD Linux"
date: 2009-10-05
forum: Server Platforms
---

### Post by zetanuxi on 2009-10-05
Is there a Linux equivalent to Active Directory?
I want to make every part of my server software free.

I know Linux can join AD server, but can they be AD servers?

---

### Post by lykwydchykyn on 2009-10-05
> **zetanuxi said:**
> Is there a Linux equivalent to Active Directory?
I want to make every part of my server software free.

I know Linux can join AD server, but can they be AD servers?

Define "equivalent" in this context.  Does it need to be drop-in replacement, or just do something similar?  What features from AD do you require?

There won't be a drop-in replacement for AD until samba 4 is stable, which will be heaven-knows-when.

---

### Post by openfly on 2009-10-05
You can go pretty far with samba / kerberos / openafs / ldap.

But it's going to hurt your brain and make you forever hate the world.

---

### Post by HermanAB on 2009-10-05
NIS and LDAP.  On their own though these are not secure, since credentials are sent in plain text.  You can do a number of things to fix that using e.g. Kerberos or SSL tunnels using stunnel or SSH.

Setting it up is easier than it seems.  The main problem is that most setup guides are arcane.

---

### Post by zetanuxi on 2009-10-05
What I wanted for the system is something that I can store user info on, edit network permissions, deploy software to Windows based end-PCs, and link a user's account to a network folder on a separate file server. Those are my needs.

Thanks for the help so far!

---

### Post by yknivag on 2009-10-05
[This thread](http://ubuntuforums.org/showthread.php?t=640760) is slightly out of date, but I believe that the methodology is still applicable.

---

### Post by lykwydchykyn on 2009-10-05
For software deployment, look at wpkg: [http://wpkg.org/](http://wpkg.org/)

I looked into it once, but I've never actually deployed it.

---

