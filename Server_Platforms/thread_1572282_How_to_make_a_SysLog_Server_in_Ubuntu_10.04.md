---
title: "How to make a SysLog Server in Ubuntu 10.04?"
date: 2010-09-10
forum: Server Platforms
---

### Post by 321 on 2010-09-10
Hi!

I wanted to make a SysLog Server in Ubuntu 10.04 Desktop to collect the startup log of all the workstation inside the local area network,

which should have a similar functionality to this guide here:

[[COLOR="Blue"]Debian Syslog Server[/COLOR]]("http://www.aboutdebian.com/syslog.htm")

However, when editing the sysklogd, i noticed it was empty and does not have any default values, along with the /etc/syslog.conf, which does not also exist. 

I'm stuck because I'm having doubts if what i'm doing would work.

I know the tutorial was for debian, so how do i proceed from here?

Any reply is appreciated. :)

---

### Post by Sef on 2010-09-10
Moved to Server Platforms.

---

### Post by BkkBonanza on 2010-09-11
Look for **rsyslog.conf**.
I think this is a newer version as that web page is rather dated now.
How it's different I couldn't say offhand but it seems Ubuntu runs rsyslog now instead.

Apparently the conf file is backward compatible. I have little practical experience with it. **man rsyslog.conf** may help making sure what you do will work.

See also some info - [http://www.rsyslog.com/doc/rsyslog_ng_comparison.html](http://www.rsyslog.com/doc/rsyslog_ng_comparison.html)

---

