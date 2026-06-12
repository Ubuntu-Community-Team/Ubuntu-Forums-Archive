---
title: "Centralized Login Scheme"
date: 2010-08-18
forum: Server Platforms
---

### Post by TheSeanKelly on 2010-08-18
So, I'm trying to set up a centralized login system for a small research lab (hence my recent post on LDAP). 

Here's my situation and what I've done so far:

I've tried to set up an LDAP server for authentication and have failed miserably.  I am NOT at all new to linux administration, but LDAP still baffles the heck out of me.  I have also not found a single tutorial that really works start to finish, including the Ubuntu documentation.  I have spent 2.5 full work days trying to solve this/googling for documentation.  

This leads me to believe that even if I were to miraculously set up LDAP, maintaining it and actually adding/removing users would become a nightmare, no?  And this isn't even including adding support for Kerberos/SMB.

Which brings me to the next problem - I also need file sharing, and since we have a couple windows machines, SMB is preferred.  It seems likd LDAP with Kerberos is the only system that actually works with SMB as well?

What else could I use?  Can Kerberos be used for logons directly?  I feel that LDAP is way overkill for my application, but NIS leaves security holes, and users have to change two passwords for samba AND nis every time - a pain.

Another thing that bothered me - users can't log on until their home directory exists, which means I have to create their home directory on every machine, which almost makes LDAP irrelevant anyway since it's supposed to centralize the work.  

Thoughts on any of this?  Sorry if it seems like a double-post of my last LDAP post, but this is more broad and open to many options.

Thanks!

---

