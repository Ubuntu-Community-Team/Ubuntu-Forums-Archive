---
title: "SSH /etc/ssh/ssh_host_rsa_key"
date: 2008-03-23
forum: Security Discussions
---

### Post by alsehendo34 on 2008-03-23
When you use the ssh client you generate the key pair in your home dir  .ssh  and move the pub one to your hosters server.
client$ mkdir ~/.ssh
client$ chmod 700 ~/.ssh
client$ ssh-keygen -q -f ~/.ssh/id_rsa -t rsa
# first, upload public key from client to server
client$ scp ~/.ssh/id_rsa.pub server.example.org:
# next, setup the public key on server
server$ mkdir ~/.ssh
server$ chmod 700 ~/.ssh
server$ cat ~/id_rsa.pub >> ~/.ssh/authorized_keys
server$ chmod 600 ~/.ssh/authorized_keys
server$ rm ~/id_rsa.pub

Now what my question is?
What the heck is the  /etc/ssh/ssh_host_rsa_key  file used for and how did it get generate @ install time  :confused:

---

### Post by Dr Small on 2008-03-23
I really do not know, but here is an easier way to copy your public key to the remote server:
```
ssh-copy-id -i ~/.ssh/id_dsa.pub user@remotehost
```

That should be a simpler process.

Dr Small

---

### Post by hyperair on 2008-03-23
/etc/ssh/ssh_host_rsa_key is used to verify the authenticity of the server you are connecting to. If I'm not mistaken, every RSA key generated is unique. So one will be generated for the SSH server, so that it can prove to you that it's the server you are trying to connect to, not some random redirected server which is trying to steal your password and/or other personal data.

---

### Post by pana.corbului on 2008-03-23
ssh_host_rsa_key is the secret key of sever's localhost let's say. It contains the server's fingerprint key that helps you to know that when you're connenting to your server you don't get a man in the middle attack.

How to use it in your own advantage you can get if you read this : [http://www.securityfocus.com/infocus/1806](http://www.securityfocus.com/infocus/1806)

---

### Post by kevdog on 2008-03-23
you only need to generate a host key if you are running a ssh server

---

### Post by alsehendo34 on 2008-03-24
"you only need to generate a host key if you are running a ssh server"

I thought this was true that you were running sshd, but why do I have keys in /etc/shh.  I did not generate them.  Is it done @ install time or when openssh is installed?  I just looked and ssh service was running.  I don't know how it got started.  Is their a utility in ubuntu that can keep it starting @ boot I am more familiar with Yast in SUSE.

---

### Post by hyperair on 2008-03-24
It's done at install time for the SSH server if I'm not mistaken.

---

