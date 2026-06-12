---
title: "When mounting NFS share from Windows 2012 default NFSv3 required NFSv4"
date: 2013-06-27
forum: Server Platforms
---

### Post by tonr on 2013-06-27
When I mount a NFS share created on a Ubuntu server, on a Windows 2012 server the default NFS version used is NFS version 3. I would like to have this set as NFS version 4 by default, as we need Japanese character support.
How are we able to get above situation to work, as I found out is that NFS v1, v2 and v3 is encoding-specific, and UTF-8 support has only been introduced in NFS v4:

[LIST]
[*] 		[RFC3530]("http://www.ietf.org/rfc/rfc3530.txt") (see paragraph '1.4.3. Filesystem Model')
[/LIST]
Can anyone guide me to the correct way to setup a situation like this?

---

