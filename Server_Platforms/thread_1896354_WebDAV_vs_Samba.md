---
title: "WebDAV vs Samba"
date: 2011-12-16
forum: Server Platforms
---

### Post by anXieTyPB on 2011-12-16
Hi there.

I am now at a point where i need to decide between Samba and WebDAV [+apache] or whether i might use both of them.

_Pros WebDAV:_
[LIST]
[*]more secure
[*]internet access via SSL
[/LIST]

_Cons WebDAV:_
[LIST]
[*]4GB File Size Limit (very bad for what I'm doing)
[*]native Win7-Support is really BAD (speed [i know the IE fix] and session-timeouts...
[*] no simultaneous data transfers possible?
[/LIST]


_Pros Samba_
[LIST]
[*]easy to configure
[*]easy to mount in Win7
[*]no file size limits
[/LIST]

_Cons Samba_
[LIST]
[*]quite insecure (as far as i read)
[*]no SSL -> therefore no internet access
[/LIST]


Currently, i got both methods configured on my homeserver.
I cannot decide, really. 

Some opinions?

---

### Post by volkswagner on 2011-12-16
Perhaps neither.

Have you considered sftp.

For windows clients you can use FTP clients supporting sftp such as Filezilla or even winSCP.  For Linux clients you can use ssh or an ftp client.

---

