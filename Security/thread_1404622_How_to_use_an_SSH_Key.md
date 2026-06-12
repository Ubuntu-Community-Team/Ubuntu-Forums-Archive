---
title: "How to use an SSH Key"
date: 2010-02-11
forum: Security
---

### Post by sinerasis on 2010-02-11
I see the other SSH questions posted recently, and I'm trying to connect to a server via SSH (to do SFTP), but I don't know how to do that.

I'm using 9.10. If I go places>connect to server and select SSH from the dropdown it seems to only allow user/pass authentication? Is this correct? Is there an easy to way allow the use of a key via that interface?

My goal is to mount the remote folder as a drive so I can edit files. I can connect to other servers that use user/pass authentication just fine, so I'm sure that's what I'm after.

My apologies if this belongs in the newb section... any help is appreciated. I'm new to SSH keys...

---

### Post by sinerasis on 2010-02-11
I've been searching around in the man...

if I do ssh -i [the key file] [user@address]

I get a warning: unprotected private key file message, then it tells me that the private key will be ignored and my permission is denied.

I should be able to input my key password at some point, is that correct?

---

### Post by FuturePilot on 2010-02-11
You don't need to do anything special to use a key with Nautilus (Places -> Connect to Server). Put the username in and leave the password field blank. When you attempt to connect it will prompt you for the key passphrase.

But it sounds like you don't have the correct permissions on the key so you'll probably have to 
```
chmod 700 ~/.ssh
chmod 600 ~/.ssh/*
```
for the above to work.

---

### Post by sinerasis on 2010-02-11
You're right on target FuturePilot, thank you.

I needed to copy the key to my .ssh directory first (at least to allow it to work using the gui), then change the permissions. 

It's working like a charm now! :)

Thanks!

---

### Post by sinerasis on 2010-02-12
...ok another somewhat related question I'm running into:

I've noticed that when I use a regular ftp connection and create a folder or file on the server it will have the permissions that I want, however using the sftp connection the permissions are set too high. Is it possible to set that by default? Where might that be done?

---

