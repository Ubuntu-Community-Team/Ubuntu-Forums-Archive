---
title: "Reverse File System Encryption Mounts - Other Solutions than ENCFS?"
date: 2014-09-30
forum: Security
---

### Post by mattlach on 2014-09-30
Hey all,

I am researching setting up a dedicated server to handle my cloud backups.  The more I research the various cloud backup services out there, the less confident I become in their handling of privacy concerns.

My solution for this fell into my lap when I was reading about the --reverse switch in EncFS.

So, it's simple.   You mount EncFS, it presents an unencrypted file system as an encrypted one in the mount location, and you point your backup software at that encrypted folder.

Problem is EncFS is kind of dated. I have A LOT of backups to do, and it doesn't support (at least anywhere I can find) AES-NI instructions.

Are there any other alternatives to EncFS that can accomplish this same goal, of presenting an unencrypted file system, as an encrypted mount point to backup software?

Much obliged,
Matt

---

