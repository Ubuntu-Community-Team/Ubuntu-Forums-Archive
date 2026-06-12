---
title: "what user runs init.d?"
date: 2009-04-06
forum: Server Platforms
---

### Post by termdex on 2009-04-06
I've setup dhcpd.conf to include the rndc.key file from bind. I've included the dhcpd user account in the bind group and the bind group has read permission on the rndc.key file.

Yet when dhcpd launches it fails to open rndc.key responding with "Permission denied." However if I change the permissions on rndc.key to 'o+r' dhcpd obtains permission.

This tells me that dhcpd is being run as some account other than root or dhcpd. I've checked the init.d script for dhcpd but I don't see where the launch account is specified. start-stop-daemon is used to launch dhcpd but its chuid switch is not used.

Any ideas?

---

### Post by BkkBonanza on 2009-04-06
Use the command **ps aux** or **top** to see which user is running a process.
Init is run by root so generally shouldn't have permission issues. 
But some processes will drop root privileges after starting (for safety) so it may be using other permissions.

---

### Post by termdex on 2009-04-07
> **BkkBonaza said:**
> Use the command **ps aux** or **top** to see which user is running a process.
Init is run by root so generally shouldn't have permission issues. 
But some processes will drop root privileges after starting (for safety) so it may be using other permissions.

Oh, sorry. I forgot to mention that the dhcpd process does end up running as the dhcpd user account, but as I said, that user is a member of the bind group, and so should have read permissions on the rndc.key file, yet still receives "Permission denied" unless 'o+r' is set.

So there must be a time when the init script is run neither by root nor by the dhcpd account, because root would never be denied permission and dhcpd has group read permission.

---

