---
title: "What is SSH Key Agent ?"
date: 2018-05-23
forum: Security
---

### Post by linuxyogi on 2018-05-23
[ATTACH=CONFIG]279809[/ATTACH]

Click to enlarge

I have no ssh installed. 

What is SSH Key Agent ?

This is Ubuntu 18.04.

---

### Post by #&amp;thj^% on 2018-05-23
> **linuxyogi said:**
> [ATTACH=CONFIG]279809[/ATTACH]

I have no ssh installed. 

What is SSH Key Agent ?

This is Ubuntu 18.04.
It's part of the Keyring Agent
```
core/libssh2 1.8.0-2
```
Installed by default.

The SSH agent handles signing of authentication data for you. When authenticating to a server, you are required to sign some data using your private key, to prove that you are, well, you.

As a security measure most people sensibly protect their private keys with a pass phrase, so any authentication attempt would require you to enter this passphrase. This can be undesirable, so the ssh agent caches they key for you and you only need to enter the password once, when the agent wants to decrypt it (and often not even that, as the ssh agent can be integrated with pam, which many distros do).

The SSH agent never hands these keys to client programs, but merely presents a socket over which clients can send it data and over which it responds with signed data. A side benefit of this is that you can use your private key even with programs you don't fully trust.

Another benefit of the SSH agent is that it can be forwarded over SSH. So when you ssh to host A, while forwarding your agent, you can then ssh from A to another host B without needing your key present (not even in encrypted form) on host A.
Also See:[https://wiki.archlinux.org/index.php/SSH_keys](https://wiki.archlinux.org/index.php/SSH_keys)

---

### Post by linuxyogi on 2018-05-23
Thanks. :P

---

### Post by deadflowr on 2018-05-23
For what it's worth Ubuntu breaks ssh into two parts a client and a server.
The desktop does not come with a server, but it does come with a client.
This allows you to connect to any ssh server without the need to install anything.

---

### Post by linuxyogi on 2018-05-23
Got it. Thanks.

---

