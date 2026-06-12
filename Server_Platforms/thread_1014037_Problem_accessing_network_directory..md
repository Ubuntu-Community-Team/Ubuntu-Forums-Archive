---
title: "Problem accessing network directory."
date: 2008-12-17
forum: Server Platforms
---

### Post by Super-Fly on 2008-12-17
Background: I have a 8.04.1 server that is connected to a file server through smb. I have a script on there that runs once a week to pass a backup of my server to the network. 

Recently (between my last backups) something happened and now I've lost the ability to access the directory I usually post my backups to from my server. When I checked my syslog I saw this error:

CIFS VFS: Error 0xfffffff3 on cifs_get_inode_info in lookup of \Directory\Backup

The odd thing to me is, when I remounted the directory using a different set of credentials (the original and this new set have the same rights and such) I can access the directory. When I then remounted with the original cred's, the problem was still there. Also, I can access directories on the file server all around my desired one, just not the one I want. Any suggestions would be great.

One thing of note, I don't have direct access to the file server (it's administered by someone else), but I'm assured that nothing there has changed.

Thanks.

---

