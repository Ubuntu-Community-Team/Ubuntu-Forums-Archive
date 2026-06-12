---
title: "encrypted backup over SSH"
date: 2006-11-12
forum: Server Platforms
---

### Post by Chayak on 2006-11-12
This is more of a high level question but does anyone have any suggestions on say using tar to compress a backup and then encrypt it before sending it over ssh to a remote system for storage.  I can easily do it unencrypted but as I don't own the remote system I'd prefer to have my backup encrypted.

This is what I can do currently

```
tar -czvf /home/me | ssh -l user server.org "cat > backup.tgz"
```

now I've tried aespipe but I get errors from tar, any suggestions?  I know I could do a shell script to tar an archive then use gpg on it before doing an scp but I like things in one line :twisted:

---

### Post by elst on 2006-11-12
The duplicity utility uses SSH and automatically stores the backups as GPG-encrypted archives. The package is "duplicity", and it's definitely in Universe for Edgy.

---

