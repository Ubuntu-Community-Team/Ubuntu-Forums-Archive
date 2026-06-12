---
title: "linux client"
date: 2010-05-14
forum: Server Platforms
---

### Post by gb1986 on 2010-05-14
How do you access linux-based services from a linux client?

---

### Post by BoneKracker on 2010-05-14
I don't know what you mean.  That's an extremely general question.

As far as communication or data transfer goes, it depends on the service.  There are a whole host of application-level network protocols associated with various services.

For example, I would use a web browser to access a web server (and any web-based service).  I would use ssh to securely open a terminal session on a remote server.  I might use nfs or cifs to mount an exported file share on a remote machine to my filesystem.  I would use an ftp client to access files shared by an ftp server.  I would use rsync to synchronize directories or filesystems, or to back up remotely.  If I wanted remote desktop type of capability, I'd choose between X session forwarding (possibly over ssh), any of a number of VNC-type applications, or any of a number of NX-type applications, depending on my requirements (security, network bandwidth, latency, etc.). The list is endless.

As far as access control goes, there are a variety of access control methods, some system-centric, some application-centric, and some enterprise-level.  The system has basic user account and password functionality, along with filesystem-level permissions.  PAM (pluggable authentication modules) integrates a variety of authentication methods into a coherent framework.  Some applications can use a variety of means (for example, ssh can handle its own authentication of remote sessions, rely on the system's login functionality, use PAM, and/or use Kerberos.  There are numerous possibilities.

If you want a meaningful answer, you're going to have to be more specific in your question.

---

