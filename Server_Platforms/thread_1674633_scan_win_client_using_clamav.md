---
title: "scan win client using clamav"
date: 2011-01-24
forum: Server Platforms
---

### Post by bigboy16 on 2011-01-24
hello guys

is possible scan win client file using clamav that installed on ubuntu server?

i use ubuntu server 10.10 with clamav, squid and samba.

if possible, what i have todo


thank's before

---

### Post by lykeion on 2011-01-24
ClamAV is for UNIX so it cannot access windows drives. However there is a Windows port of ClamAV, 
and I also found these forum discussions/blog posts that might shed some light:
[http://www.gossamer-threads.com/lists/clamav/users/50623](http://www.gossamer-threads.com/lists/clamav/users/50623)
[http://www.gossamer-threads.com/lists/clamav/users/50925](http://www.gossamer-threads.com/lists/clamav/users/50925)
[http://www.andornot.com/blog/post/How-to-set-up-ClamAV-as-a-Windows-Service-to-scan-file-streams-on-demand.aspx](http://www.andornot.com/blog/post/How-to-set-up-ClamAV-as-a-Windows-Service-to-scan-file-streams-on-demand.aspx)

Hope that it helps

---

