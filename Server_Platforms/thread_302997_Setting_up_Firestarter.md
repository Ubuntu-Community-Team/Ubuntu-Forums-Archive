---
title: "Setting up Firestarter"
date: 2006-11-19
forum: Server Platforms
---

### Post by henrywm on 2006-11-19
I need help setting up Firestarter.
When outbound traffic is set in permissive mode it blocks my web browser. I tried restrictive mode and told it to permit various ports (including port 80) and had the same problem.

---

### Post by DaveBorealis on 2006-11-19
> **henrywm said:**
> When outbound traffic is set in permissive mode it blocks my web browser. I tried restrictive mode and told it to permit various ports (including port 80) and had the same problem.

So if you turn the firewall off, then Firefox works?

The permissive mode has a blacklist of what you cannot connect to.  The restrictive mode has a whitelist of what you can establish a connection to.

If Firefox works with the firewall stopped, then it's possible that you have somehow added something to either list (black or white) that's blocking it.

Best regards,
Dave

---

