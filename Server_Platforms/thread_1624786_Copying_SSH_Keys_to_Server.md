---
title: "Copying SSH Keys to Server"
date: 2010-11-18
forum: Server Platforms
---

### Post by trentscott on 2010-11-18
I'm trying to connect to my Ubuntu Server via SSH with key-based authentication from Mac OS X. Unfortunately, you can't run the ssh-copy-id command on a Mac -- it just won't work. Instead, should I just copy the file id_rsa.pub from my Mac and put it on the server manually? Does it go in ~/.ssh/authorized_keys and should the file have the same name (id_rsa.pub)? It looks like my user account on the server doesn't have a folder called .ssh in the home directory (at least I can't cd to it), should I just create it or am I missing some critical process that does that for me?

---

### Post by abix_adam_pl on 2010-11-18
Yes, Yes....   (commands in CODE shoud be done on server.

ssh to server
```
mkdir .ssh
```logout
```
scp -C id_rsa.pub user@server:~/.ssh/authorized_keys
```ssh to server
```
chmod g-rwx,o-rwx .ssh -R
```logout
ssh to server (shoud be without asking password).

Adam

---

### Post by trentscott on 2010-11-18
Thank you, that worked like a charm!

---

