---
title: "CNAME or A record?"
date: 2011-04-23
forum: Server Platforms
---

### Post by Doulos1 on 2011-04-23
I have my DNS set up using the CNAME for www .  A fellow I know said I should not use CNAME, but should instead use an A record for www . Is that correct?  I have seen examples both ways online.

---

### Post by brettg on 2011-04-23
Use an A record. 

CNAME records are intended to point to a zone over which you have no control, so if the IP changes there DNS can still find it.

Because of this a CNAME requires 2 lookups.

---

### Post by BkkBonanza on 2011-04-24
"A Record" is preferred when it will suffice, as in this case. It's not going to make any practical difference in your case but it's nice to do it right.

---

### Post by Doulos1 on 2011-04-24
What is happening to cause this concern is this:

Users occasionally say when they try to register (which requires clicking an activation link sent via email) the process never completes.  I have been unable to replicate this myself, but one user claims it was happening because he accessed the site with sitname.com, but the activation link uses [www.sitename.com](www.sitename.com).  He claimed it was a DNS issue with www .  

I did not  think it is a DNS issue but thought I would ask here.

Thanks.

---

