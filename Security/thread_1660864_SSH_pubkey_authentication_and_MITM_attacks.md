---
title: "SSH pubkey authentication and MITM attacks"
date: 2011-01-05
forum: Security
---

### Post by aschlosberg on 2011-01-05
Given that my public key is a pre-shared secret is sshd made in a way that this negates the possibility of a man in the middle attack?

In other words, if the known_hosts file were to be deleted, would it be safe to ignore the fingerprint of a server that already has my public key in authorized_keys?

---

### Post by bodhi.zazen on 2011-01-06
> **aschlosberg said:**
> Given that my public key is a pre-shared secret is sshd made in a way that this negates the possibility of a man in the middle attack?

In other words, if the known_hosts file were to be deleted, would it be safe to ignore the fingerprint of a server that already has my public key in authorized_keys?

I am not sure what you are asking exactly, but I think the answer is no as IMO the known_hosts is part of the prevention of a mitm attack (you may not be able to connect to the mitm server, but there is no reason to give out your password).

---

### Post by mail2345 on 2011-01-06
Nope, pubkey auth has the client send the public key to the server to avoid unneeded decryption/encryption.

---

### Post by anomie on 2011-01-06
[QUOTE=aschlosberg]Given that my public key is a pre-shared secret is sshd made in a way that this negates the possibility of a man in the middle attack?[/quote]

Yes. OpenSSH helps thwart MITM attacks *after* your client has saved the server's key ID (in ~/.ssh/known_hosts, as mentioned). 

[QUOTE=aschlosberg]In other words, if the known_hosts file were to be deleted, would it be safe to ignore the fingerprint of a server that already has my public key in authorized_keys?[/QUOTE]

Definitely not. If someone cracks foo.local, and poisons .local DNS, they can just as easily grab your account's public key and put it on bar.local (posing as foo.local). 

Not likely, but certainly possible. 

Try not to delete known_hosts if you can help it. It's there for your protection.

---

### Post by bodhi.zazen on 2011-01-06
> **anomie said:**
> Try not to delete known_hosts if you can help it. It's there for your protection.

You almost never need to delete known_hosts, use ssh-keygen

```
ssh-keygen -R hostname
```

[http://bodhizazen.net/Tutorials/SSH_overview#Security](http://bodhizazen.net/Tutorials/SSH_overview#Security)

Many blogs and posts advise you remove known_hosts, but that is not the "best practice".

---

### Post by CharlesA on 2011-01-06
> **bodhi.zazen said:**
> You almost never need to delete known_hosts, use ssh-keygen

```
ssh-keygen -R hostname
```

+1.

If I have done a reinstall and needed to remove the old entries from known_hosts, I have had to remove both the hostname and the ip address.

---

