---
title: "SSH login as different user"
date: 2006-03-05
forum: Server Platforms
---

### Post by Iowan on 2006-03-05
If I'm logged into my workstation as **Iowan**, but want to SSH into my server as **supersoul**, I can **ssh supersoul@server**.  The server will request a password - that of supersoul.  Now... if I want to set this up for password-less SSH (via id_rsa and/or id_dsa files - and their associated .pub files), do I **ssh-keygen** the files as **Iowan** on the workstation and copy the .pub files  to the server under **supersoul's** home directory?  Or must I create **supersoul** on the workstation long enough to build the **id_** files?

---

### Post by claes on 2006-03-09
You copy the .pub key the the .ssh/authorized_keys file of the user you want to log in to. SSH does no username matching only public key to private key matching.

Claes

---

### Post by Iowan on 2006-03-09
> You copy the .pub key the the .ssh/authorized_keys file of the user you want to log in to.I'm a li'l dense this morning... 
**ssh-keygen** as **supersoul** on the server, then copy the .pub files to .ssh/authorized_keys file of **Iowan** on the workstation???
Or... 
**ssh-keygen** the files as **Iowan** on the workstation and copy the .pub files to **supersoul's** .ssh/authorized_keys file on the server?
Or... 
have I missed it completely?

---

### Post by claes on 2006-03-10
[QUOTE=Iowan]
**ssh-keygen** the files as **Iowan** on the workstation and copy the .pub files to **supersoul's** .ssh/authorized_keys file on the server?
[/QUOTE]

That's correct.

Claes

---

### Post by Iowan on 2006-03-23
IT WORKS!! I read the OpenSSH FAQ : > Typically this is caused by the file permissions on $HOME, $HOME/.ssh or $HOME/.ssh/authorized_keys being more permissive than sshd allows by default.

In this case, it can be solved by executing the following on the server.

    $ chmod go-w $HOME $HOME/.ssh
    $ chmod 600 $HOME/.ssh/authorized_keys

If this is not possible for some reason, an alternative is to set StrictModes no in sshd_config, however this is not recommended. **supersoul's** home directory had too many permissions for group and other.

---

