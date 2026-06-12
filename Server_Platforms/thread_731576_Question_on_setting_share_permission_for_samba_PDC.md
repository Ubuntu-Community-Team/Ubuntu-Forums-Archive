---
title: "Question on setting share permission for samba PDC"
date: 2008-03-22
forum: Server Platforms
---

### Post by cpthk on 2008-03-22
I am setting up a domain controller with share folders. I have a folder set to: ```
write list = @test
```Does samba ignore the system file/folder permission and file ownership? And letting test group able to write even though it doesn't have system permission to write? Or I still have to change the system file/folder(chmod) and ownership(chown) to make sure user can access the files.

---

### Post by kidders on 2008-03-23
Hi there,

Filesystem permissions aren't "optional" ... Samba can't override them.

Samba's access controls are essentially a Microsoft-compatible abstraction sitting on top of whatever happens to be underneath (eg Ubuntu + Ext3). In practice, the degree of access users get to your files is a product of the two. For example...[LIST]
[*]Samba can prevent a user accessing something, even though the underlying access controls would have allowed it.
[*]Conversely, Samba might permit access to files, only to be locked out of them, in the end, by your filesystem permissions.
[/LIST]

The best practice is often to leave access control in the hands of your filesystems, unless there's something particularly awkward or security-critical you'd like Samba to do differently than the rest of your system.

---

