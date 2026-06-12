---
title: "vsftpd error on connecting"
date: 2020-12-01
forum: Server Platforms
---

### Post by mark-angus-nz on 2020-12-01
Newbie Question...

I'm getting this error - can not retrieve directory listing, and can not understand why?

Any assistance most appreciated

See the error I am getting here:  [https://ibb.co/8Xc1ZJs](https://ibb.co/8Xc1ZJs)

Many Thanks :-)

---

### Post by wildmanne39 on 2020-12-01
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by darkod on 2020-12-01
First of all, lets start from the most important.

FTP is VERY unsecure so if you can avoid using it, do it. It's much better to use SFTP or SCP to connect to linux servers. Plus it makes connecting through a firewall much easier.

Next, the welcome message says you are not using TLS over this FTP connection. That's very bad. Anyone can intercept your password and have access to your FTP.

Finally, the message for directory listing might point that the user does not have necessary permissions. But this is the last thing you should worry about. First address the above two points, they are much more important.

PS. You need to also make sure the firewall is allowing all necessary ports, like the passive port range too.

---

### Post by LHammonds on 2020-12-01
Here is how I configured vsftpd to use SSL on Ubuntu Server 18.04 (when I dealt with a bank for EDI transactions...but now I don't so I will likely not update that tutorial for 20.04+)

[How to Install an FTP over SSL (FTPS) on Ubuntu Server 18.04](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=265)

LHammonds

---

