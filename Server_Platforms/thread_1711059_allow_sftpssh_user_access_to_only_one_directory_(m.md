---
title: "allow sftp/ssh user access to only one directory (/media/externalHD)"
date: 2011-03-20
forum: Server Platforms
---

### Post by starjones on 2011-03-20
im really new to servers and just set mine up to experiment with kind of.

i want to allow some friends to ssh/sftp/scp into my system but i only want them to have access to my external hard drive (/media/externalHD/), and i dont want them to be able to delete or add anything, only download.

i have found instructions on how to limit a user to his/her home directory and thought about just creating a user with the home directory /media/externalHD but idk if this will work and im afraid i might make a mistake and delete 800gb of 'files';)

ty

ubuntu 10.04 server

---

### Post by hawk2010 on 2011-03-21
The best solution for you is chrooting through SFTP. You can chroot the users to [B]/media/externalHD so that users can only access that and nothing else. YOu have to configure sshd_config accordingly.
[/B]

---

### Post by Lars Noodén on 2011-03-21
It is very easy to chroot SFTP users.

Make a group.  Add the to-be chrooted users. Then add something like the following to /etc/ssh/sshd_config:
```

Subsystem sftp internal-sftp

Match Group *sftpusers*
        ChrootDirectory */media/externalHD*
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp

```

---

