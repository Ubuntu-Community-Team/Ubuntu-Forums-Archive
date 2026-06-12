---
title: "smb.conf Table with all Options"
date: 2013-04-10
forum: Ubuntu, Linux and OS Chat
---

### Post by Bathroth on 2013-04-10
First i am not sure if this is more for outtopic or for the Server section so i just try it first here.

I am surprised that there is nothing like a real table of all possible configurations of samba out there.

The most complete **list **i found was here: [http://www.tamos.net/guide/manpages/samba/smb.conf.5.html#toc20](http://www.tamos.net/guide/manpages/samba/smb.conf.5.html#toc20)

But i would like it as a **table**. Is there anything out there? google didnt gave me much about tables of the smb.conf

Like:
[TABLE]
[TR]
[TH]Option
[/TH]
[TH]Parameters
[/TH]
[TH]Function
[/TH]
[TH]Default
[/TH]
[TH]Scope
[/TH]
[/TR]
[TR]
[TD]path (directory)
[/TD]
[TD]string (directory name)
[/TD]
[TD]Sets the Unix directory that will be provided for a disk share or used for spooling by a printer share.
[/TD]
[TD]/tmp
[/TD]
[TD]Share
[/TD]
[/TR]
[TR]
[TD]comment
[/TD]
[TD]string
[/TD]
[TD]Sets the comment that appears with the share.
[/TD]
[TD]None
[/TD]
[TD]Share
[/TD]
[/TR]
[TR]
[TD]volume
[/TD]
[TD]string
[/TD]
[TD]Sets the MS-DOS volume name for the share.
[/TD]
[TD]Share name
[/TD]
[TD]Share
[/TD]
[/TR]
[TR]
[TD]read only
[/TD]
[TD]boolean
[/TD]
[TD]If yes, allows read-only access to a share.
[/TD]
[TD]yes
[/TD]
[TD]Share
[/TD]
[/TR]
[TR]
[TD]writable (write ok or writeable)
[/TD]
[TD]boolean
[/TD]
[TD]If no, allows read-only access to a share. If yes, both reading and writing are allowed.
[/TD]
[TD]no
[/TD]
[TD]Share


[/TD]
[/TR]
[/TABLE]

But like a FULL list?

I couldnt found anything. If someone have a link or a excel file or whatever - Please tell me :)

Regards,
Bathroth

---

