---
title: "help:  proftpd server and masquerade address"
date: 2008-02-04
forum: Server Platforms
---

### Post by dmkuster on 2008-02-04
Hi all,

I have a proftpd server up and running on my LAN using proftpd.

I'm using the free no-ip service and have the masquerade address
set up and working.

Here's the problem:  When comcast changes my router's IP address it seems that proftpd continues to masquerade as the "old" IP address.
In other words, proftpd seems to read the proftpd.conf file once when
it starts, and it never goes back and "refreshes" the masquerade 
address.

The end result is if I leave my server up it becomes unreachable after
several days.

Is there any way around this limitation??

Thanks!

---

### Post by dmkuster on 2008-02-04
After a little digging I found this on the proftpd web site:

Question: If proftpd resolves any DNS names to IP addresses when it starts up, and I am using dynamic IP addresses which change after my proftpd has started, will proftpd see my new IP addresses?
Question: Unfortunately not. ProFTPD has no easy way of handling dynamic IP addresses by itself. One way of dealing with this situation is to restart proftpd periodically, which will force it to re-parse its configuration and thus re-resolve all IP addresses. 

What I don't like about this is, if set up a cron job to restart the ftp server, say, once a day, then there could be a long period of time (up to a day) when my ftp server would be unreachable.

But if set it to restart much more frequently, the likelihood that it could be restarted in the middle of a file transfer goes way up.  :confused:

---

### Post by pearj on 2008-04-18
Just reload proftpd instead of restarting it.  I was testing on my machine and active transfers will continue while reloading.

I was changing the MasqueradeAddress and it would change during reloads, but it wouldn't kill active connections.

Best of both worlds!

---

