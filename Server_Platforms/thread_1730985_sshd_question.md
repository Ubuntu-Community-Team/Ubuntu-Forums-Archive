---
title: "sshd question"
date: 2011-04-16
forum: Server Platforms
---

### Post by DataSpy on 2011-04-16
I'm running ubuntu server 10.10 and I was wondering where do I put my public dsa key after I've generated it?  I know it goes on the server but does it go in .ssh/authorized keys?  If so how come I can't browse to that folder?

Any help greatly appreciated,
thanks in advance!

---

### Post by CharlesA on 2011-04-16
It should go in ~/.ssh/authorized_keys

---

### Post by cjhabs on 2011-04-16
authorized_keys is a file, not a directory, where entries are automatically added the first time you connect to a remote system via ssh.

I use rsa keys and the public key for my machine goes in ~/.ssh/id_rsa.pub

I assume for dsa it will be id_dsa.pub

---

### Post by SeijiSensei on 2011-04-16
The only file I know of that's updated automatically when you connect is ~/.ssh/known_hosts, and only then if you accept the remote's signature.  If you log in with a password, nothing gets added to authorized_keys.  I know there's some command-line method to add keys, but I usually just copy the line from id_[rd]sa.pub on the client to the bottom of the server's authorized_keys.

---

### Post by DataSpy on 2011-04-16
I tried copying the key over, I can log into ssh but I get an error when copying, I just want to confirm that I should create the directory or if I did something wrong?

Command to copy key:
scp ~/.ssh/id_dsa.pub [email]dataspy@192.168.1.107:.ssh[/email]/authorized_keys

Error:
scp: .ssh/authorized_keys: No such file or directory

---

### Post by deconstrained on 2011-04-16
Is it a server key or client key? If the former, it goes somewhere in /etc/ssh (read man page for details). Otherwise, use the ssh-copy-id script available on every Debian-based system to automatically do the ~/.ssh/authorized_keys appending.

---

### Post by DataSpy on 2011-04-16
when I do an ls -a (while in ~) I don't see a .ssh directory on the server?

---

### Post by SeijiSensei on 2011-04-16
If this is the only key that will be in authorized_keys, try this.  Copy the file id_dsa.pub to the remote's .ssh directory.  Then use the command:

```
cd ~/.ssh
mv id_dsa.pub authorized_keys

```

If you intend to add other keys, use these commands for the additional keys:

```
cd ~/.ssh
cat id_dsa.pub >> authorized_keys
rm id_dsa.pub

```

> Error: scp: .ssh/authorized_keys: No such file or directory

You need the full path ~/.ssh/authorized_keys.

---

### Post by CharlesA on 2011-04-16
Does the .ssh directory exist?

---

### Post by DataSpy on 2011-04-16
Thanks for the help everyone!!! I used ssh-copy-id to copy it over and it's working now :)

---

