---
title: "Question about RSA keys"
date: 2012-03-05
forum: Server Platforms
---

### Post by Hell's Chicken on 2012-03-05
I'm trying to login to another server using an RSA key. But I've got a problem with this. Don't know if what I'm trying to do is wrong, but I want to understand it better. 

I have correctly setup the RSA key. I can connect to the other server without password, when I'm logged in as the user (ssht), but when I try to connect when I'm logged in as another user, but with ssht@192.168.2.205, the connection fails. 

```
server@dns2:~$ su ssht
Password:
ssht@dns2:/home/server$ ssh 192.168.2.205
Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-8-server x86_64)

Last login: Mon Mar  5 13:35:45 2012 from 192.168.2.206
ssht@dns1:~$

```

```

server@dns2:~$ ssh ssht@192.168.2.205
ssht@192.168.2.205's password:

```

Can anyone give me an explanation of why this happens?

---

### Post by Grenage on 2012-03-05
Keys are per-user, not per-host; they are stored in:

```
/home/USER/.ssh/
```

So you'll need to copy them across.

---

### Post by Hell's Chicken on 2012-03-05
I know. They are stored in the correct folder. I can connect with the user ssht when I'm logged in as the user ssht, but I can't connect with another user, when I'm using "ssh ssht@192.168.2.205". 

I thought that when I'm using this method, I'm telling the other server that I want to login with the user ssht, or am I wrong?

---

### Post by spynappels on 2012-03-05
Are you user ssht on the local machine as well as on the remote machine?

If you are a different user on the local machine, you need to add that user's public key to ssht's authorized_keys on the remote machine for this to work.

As Grenage said, ssh keys are per user, at either end of the connection.

---

### Post by Hell's Chicken on 2012-03-05
Yes, user ssht exists on the local machine & the server. 

I'm trying to connect with the user ssht, which I have setup the ssh key for, with the command "ssh ssht@192.168.2.205". This doesn't work. Only when I am logged in as the user ssht itself. 

When I am using the command I mentioned before, I believe I am telling the server that I want to connect with the user ssht, am I correct? Or is there something else I don't know about?

---

### Post by spynappels on 2012-03-05
> **Hell's Chicken said:**
> Yes, user ssht exists on the local machine & the server. 

I'm trying to connect with the user ssht, which I have setup the ssh key for, with the command "ssh ssht@192.168.2.205". This doesn't work. Only when I am logged in as the user ssht itself. 

When I am using the command I mentioned before, I believe I am telling the server that I want to connect with the user ssht, am I correct? Or is there something else I don't know about?

If you have set up the key for user ssht on the local machine to access ssht account on the server, that key will only work when you are logged in as ssht on the local machine.

If you are logged in as anything else on the local machine, you need to create a new ssh key pair and also copy the public key just created to the authorized_keys file for user ssht on the remote machine.

Each keypair will only work for a specified user at either end of the connection. If either changes, you need a different keypair.

---

### Post by Hell's Chicken on 2012-03-05
Ah, now it's clear, thanks!

---

### Post by spynappels on 2012-03-05
No problem!

---

