---
title: "proftpd buffer help"
date: 2008-01-19
forum: Server Platforms
---

### Post by brad28304 on 2008-01-19
Hello, this is my first post, I hope I don't screw this up.
I setup proftpd and everything works.  I have 2gb of memory and I was wondering if I could use that as a buffer to help speed up transfers.  Right now I am using about 160mb of the 2gb of memory.  I would like to use the rest of the memory as a buffer for FTP transfers, mainly when I write to the server.  Is this possible?

---

### Post by brad28304 on 2008-01-20
Also, the system is on a UPS so I am not worried about power loss.  I know there is some times issues about losing data that is in the buffer when the power goes out.

---

### Post by brad28304 on 2008-02-17
I still have not found out if this is possible, I am thinking it might be a setting in the OS itself.

---

### Post by faulkes on 2008-02-17
> **brad28304 said:**
> Hello, this is my first post, I hope I don't screw this up.
I setup proftpd and everything works.  I have 2gb of memory and I was wondering if I could use that as a buffer to help speed up transfers.  Right now I am using about 160mb of the 2gb of memory.  I would like to use the rest of the memory as a buffer for FTP transfers, mainly when I write to the server.  Is this possible?

The system will dynamically add addtional ram to the process as required, however this will not speed up transfers.

While not garraunteed to improve performance, you may wish to look at altering the linux kernel TCP options to provide additional benefit.

You can find a good write-up here:

[http://www.santa-li.com/linuxonbb.html](http://www.santa-li.com/linuxonbb.html)

Note that this page is directed towards broadband users, however the changes are just as effective when applied against WAN situations.  The only exception being that if the WAN does not have sufficient bandwidth, any amount of tuning may not solve the issue.

Faulkes

---

