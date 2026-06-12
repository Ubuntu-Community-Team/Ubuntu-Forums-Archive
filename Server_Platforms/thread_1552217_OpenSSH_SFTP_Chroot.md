---
title: "OpenSSH SFTP Chroot"
date: 2010-08-13
forum: Server Platforms
---

### Post by v8YKxgHe on 2010-08-13
Morning all,

I'm wanting to setup SFTP in a chroot, which is simply enough to do and I already have it working; however I also want it so that when they connect via SFTP it goes directly to their home directory. Currently I have the following in "/etc/ssh/sshd_config":

```
Subsystem sftp internal-sftp

Match Group sftp-users
        ChrootDirectory /home
        AllowTCPForwarding no
        ForceCommand internal-sftp
```

Which works perfectly fine, however when they connect there are shown the contents of the "/home" directory which they then have to "cd username" to get to their home directory. This I do not like, and it confuses our clients who connect saying they can see "random folders that aren't mine", or some that think they've "hacked" the server.

I really need it so upon connection they go to "username" directory. I can do this by using:

```
usermod -d /username username
```

Which changes the users home directory to "/username", and then upon connection it works just fine, they are taken directory to their home directory. However, I really really do not like the fact that "/etc/passwd" shows a different home directory to their real home directory, i.e it states "/username" when actually it is "/home/username".

I've spent the entire day looking a different ways of doing it, and I can't come up with anything.

Any help?

---

### Post by cj13579 on 2010-08-13
Can you not use the following to go directly to the users home directory:

```
Subsystem sftp internal-sftp

Match Group sftp-users
        ChrootDirectory /home/%u
        AllowTCPForwarding no
        ForceCommand internal-sftp
```

---

### Post by v8YKxgHe on 2010-08-13
You can, and that's what I've just done actually (well, using "%h" which is a var for their home directory). However it does mean the user can not have write access to their main home directory. Which isn't too bad. Hum

---

### Post by cj13579 on 2010-08-13
Does changing the permissions on the /home/user folder make any difference to this? If they can't cd from that dir maybe it wouldn't be TOO insecure. If it does anything at all that is...

---

