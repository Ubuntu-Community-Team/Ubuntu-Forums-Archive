---
title: "A quirk of OpenSSH and Ubuntu Servers."
date: 2009-12-20
forum: Security
---

### Post by T.Louis on 2009-12-20
Hello,

I received the message "Permission denied (public key)" recently when installing OpenSSH. I had set it up to use it without password but with a passphrase and private and public keys.

Now the message above in quotes is a common problem and can be resolved in many ways, and the most common solution is that people have forgotten to change the .ssh folder and id_xxx file rights to 700 and 600.

However, I stumbled upon another quirk:

When you are logged into your Ubuntu Server on user account and attempt to ssh in from a client with the same user name, the public/private key works great. But when you log out from your Ubuntu Server with the user name, and then try to connect with the client you get the message "Permission denied (public key)".

I honestly don't know why this is, if its the fact that the the home folder and .ssh folder on the server is encrypted when you log out or if its some quirk that I can't wrap my head around.

But the solution is to take your authorized_keys on your server out of the home directory and put them somewhere else, say in /etc/ssh and edit your sshd_config to reflect this with AuthorizedKeysFile /etc/ssh/authorized_keys and it seems to work.

Now I don't really know if this poses any security issues? If anyone has any comments on this, please do reply!

Thanks,
TL

---

### Post by Agent ME on 2009-12-20
If you choose to have your user's home directory be encrypted, then it's only accessible when you're logged on. If you're not already logged on, Ubuntu can't access your ~/.ssh folder because it's encrypted, exactly as you set it up to be.

I believe you can set it up so that your ~/.ssh folder is not encrypted but still located in your home directory.

---

### Post by T.Louis on 2009-12-20
> **Agent ME said:**
> If you choose to have your user's home directory be encrypted, then it's only accessible when you're logged on. If you're not already logged on, Ubuntu can't access your ~/.ssh folder because it's encrypted, exactly as you set it up to be.

I believe you can set it up so that your ~/.ssh folder is not encrypted but still located in your home directory.

Thanks Agent. I'll look into how to leave out the encryption on the ~/.ssh folder, or alternatively if it is possible to keep the public key on the server somewhere else without it becoming security risk.

---

### Post by CharlesA on 2009-12-20
> **T.Louis said:**
> Thanks Agent. I'll look into how to leave out the encryption on the ~/.ssh folder, or alternatively if it is possible to keep the public key on the server somewhere else without it becoming security risk.

That's why I decided not to encrypt my home directory. There isn't much of a security risk if you delete id_rsa and id_rsa.pub from ~/.ssh.

---

### Post by bodhi.zazen on 2009-12-20
If you use an encrypted home directory , and wish to ssh in, simply use an aletrnate location for your keys.

For example, you could use /etc/ssh/authorized_keys.

Set the location in /etc/ssh/sshd_config :

See : [http://www.openbsd.org/cgi-bin/man.cgi?query=sshd_config](http://www.openbsd.org/cgi-bin/man.cgi?query=sshd_config)

In particular > **AuthorizedKeysFile**
             Specifies the file that contains the public keys that can be used
             for user authentication.  **AuthorizedKeysFile** may contain tokens
             of the form %T which are substituted during connection setup.
             The following tokens are defined: %% is replaced by a literal
             '%', %h is replaced by the home directory of the user being au-
             thenticated, and %u is replaced by the username of that user.
             After expansion, **AuthorizedKeysFile** is taken to be an absolute
             path or one relative to the user's home directory.  The default
             is ``.ssh/authorized_keys''.


---

### Post by CharlesA on 2009-12-20
That's handy to know. :-)

---

### Post by T.Louis on 2009-12-22
Thank you for the replys and help guys.

TL

---

