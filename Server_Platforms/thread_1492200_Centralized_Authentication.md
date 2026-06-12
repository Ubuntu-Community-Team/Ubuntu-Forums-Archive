---
title: "Centralized Authentication"
date: 2010-05-24
forum: Server Platforms
---

### Post by xmsft on 2010-05-24
I need to see if someone can point me in the right direction.  I currently help with the administration of a small private K-12 school.  This school is currently using Microsoft Windows but can't afford to upgrade the software.  I would like to start moving them toward Linux and specifically Ubuntu due to the low cost, but my biggest roadblock is centralized authentication.
 
We currently use Active Directory for authentication services, but I would prefer to move the backend services to Linux as well so I can get away from the cost of client access licenses.  So, I'm looking for advice on what I should look at that would replace the Active Directory boxes with Linux boxes that would allow centralized authentication for **BOTH** Windows and Ubuntu clients.  I need the authentication to support both clients because I'll need to migrate off the Windows clients.  I can convert the computer labs first, because the kids will pick up Ubuntu very easily.  Then I can tackle migrating the faculty and staff.
 
Most of the information I've found on the Internet talks about Linux authenticating to AD or Windows authenticating to a Samba PDC.  So, I guess I could go down the route of trying to configure both clients to authenticate against a Samba PDC.  Maybe something like EBox or ClearOS, but is this the right approach?
 
One wrinkle in the equation is that the school actually has 2 physical campuses that are across town from each other.  I currently have a domain controller at each location replicating information via VPN so faculty can move between campuses and still use a single id and password.  So, I would need the solution to support this scenario.  I'm sure I can probably setup a Samba PDC replicating with a Samba BDC to accomplish this task, but again is this the right solution?
 
Anyways, I'm looking for any possible insights into this situation.  I'm trying to use free software, so if you can lean in that direction, that would be helpful.  If it can't be done with free software, then "low" cost alternatives could certainly be considered.  All clients are currently Windows XP and the domain controllers are Windows 2003 and Windows 2000.  There are approximately 100 machines total.
 
Thanks in advance!

---

### Post by HermanAB on 2010-05-24
Howdy,

Read the Official Howto on the Samba web site.  It is all explained in there.

---

