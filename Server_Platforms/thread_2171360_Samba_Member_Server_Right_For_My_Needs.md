---
title: "Samba Member Server Right For My Needs?"
date: 2013-08-30
forum: Server Platforms
---

### Post by lingpanda on 2013-08-30
Looking to add a member server to my Samba4 Active Directory. Before I do though I have some questions. 

[LIST=1]
[*]Is this suggested to have a secure place to redirect Windows folders?
[*]Will I be able to redirect Ubuntu home folders to this server?
[/LIST]

---

### Post by Toxic64 on 2013-08-30
Hi lingpanda,

1If you are talking about users home directories, it certainly is indeed.
2.I can't seem to find a reason why you couldn't though I wouldn't recommend it

What I'd do is an Rsync of those folders just to keep the datas synchronized but not a full redirection.

---

