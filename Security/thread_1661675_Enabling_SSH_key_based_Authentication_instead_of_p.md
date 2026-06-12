---
title: "Enabling SSH key based Authentication instead of password"
date: 2011-01-07
forum: Security
---

### Post by kanagaraj.rk on 2011-01-07
Dear Friends,

I have Ubuntu 8.04 and Ubuntu10.10 both are VPS server on Internet. It has 12 Users each and they usually login by using **ssh** like this **ssh username@ip. **Now i need to disable the password authentication and authenticate those users by using their valid **ssh** key. After logging in they can be able to switch to root. please tell me how to configure this. Since I am a beginner please ignore my mistakes.

---

### Post by mail2345 on 2011-01-07
Have them create and upload their own keys with these instructions:
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
Once that's done for all users, follow the instructions here to disable password login:
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

---

### Post by CharlesA on 2011-01-07
They can create the keys on their client machine using this:

```
ssh-keygen
```

Then transfer them to the server by using this:

```
ssh-copy-id
```

---

### Post by sj1410 on 2011-01-10
Hi

I hope you got the answer. I also have a detailed procedure which i can share with you.


1) The first step involves creating a set of RSA keys for use in authentication.
This should be done on the client.
To create your public and private SSH keys on the command-line:

mkdir ~/.ssh
chmod 700 ~/.ssh
ssh-keygen -t rsa -b 2048

do not use password use blank password

2) you can transfer your RSA key by doing the following from your own computer:

ssh-copy-id root@ipaddress


3) on ssh server change the following from yes to no in /etc/ssh/sshd_config


PasswordAuthentication no


to add new keys

4) generate new rsa key on client as in step 1

5) copy content of ~/.ssh/id_rsa.pub to ~/.ssh/authorized_keys of server


for more information please visit

[http://sial.org/howto/openssh/publickey-auth/](http://sial.org/howto/openssh/publickey-auth/)




hope this helps

---

### Post by cariboo on 2011-01-10
@sj1410

You've got two mistakes in your post. when tranfering keys to the server the command should be:

```
ssh-copy-id user@server
```

as you also want to disable root login in /etc/ssh/sshd_config

and your link at the bottom of your post leads to a placeholder web site, with no info on it.

---

### Post by CharlesA on 2011-01-10
Either disable root logins totally, or set it like so:

```
PermitRootLogin without-password
```

That way you can login as root with a public key, but not with a password.

Using keys stops bruteforce attacks in their tracks.

@sj1410: Here's a [link]("http://web.archive.org/web/20080822232047/http://sial.org/howto/openssh/publickey-auth/") that works - sial.org looks like it's been dead since 2008.

---

### Post by sj1410 on 2011-01-10
> **cariboo907 said:**
> @sj1410

You've got two mistakes in your post. when tranfering keys to the server the command should be:

```
ssh-copy-id user@server
```

as you also want to disable root login in /etc/ssh/sshd_config

and your link at the bottom of your post leads to a placeholder web site, with no info on it.

Thnaks for the update.

---

