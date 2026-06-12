---
title: "Need help transferring a domain from a Windows 2003 server to Hardy Server"
date: 2009-08-16
forum: Server Platforms
---

### Post by Zack McCool on 2009-08-16
OK, for years I have been running Linux pretty much exclusively.  EXCEPT that my primary servers are both running Windows 2003 to provide AD, DNS and DHCP (All the shares have already been moved).

I will be abandoning AD, so now I need the easiest way to transfer the DNS zones (There are 2) to the Hardy server, then shut down the services in Windows.  I assume it is fairly simple, but I don't feel like messing with it for too long, so I'd prefer to rely on the past experiences of someone else.

DHCP, I assume, will require that I just shut down the old, create the new, add the old static assignments, and get on with life...   ;)

Thanks for any help...

Joe

---

### Post by koenn on 2009-08-16
dns zone files on linux are plain text files, so all you need to do is export your windows dns zones to a text file and copy/paste the contents.

You may need to clean up the syntax. if it's a large file, you might want to look for a find & replace statement, but that will largely depend on how Windows exports its records.

---

