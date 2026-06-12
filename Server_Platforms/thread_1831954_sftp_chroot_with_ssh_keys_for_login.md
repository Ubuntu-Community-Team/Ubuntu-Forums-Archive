---
title: "sftp chroot with ssh keys for login"
date: 2011-08-24
forum: Server Platforms
---

### Post by Frozen Forest on 2011-08-24
Would it be possible to have a chrooted sftp that uses ssh-keys for login, that after login uses  ChrootDirectory = /home/sftp/ . I think that in order to use ssh keys does sshd require that a folder is owned by the user that login and that a public key is contained in ~/.ssh/authorized_keys .
[PHP]
/home/user1/ # owned by user1
/home/user2/ # owned by user2
/home/sftp/ # owned by root
[/PHP]

---

