---
title: "Sftp"
date: 2010-11-18
forum: Server Platforms
---

### Post by trentscott on 2010-11-18
Is it safe to use SFTP from outside my local network (i.e. open the port on my router) or is there some kind of key based authentication I can implement like SSH? If so, how do you do that?

---

### Post by amauk on 2010-11-18
SFTP is FTP over an encrypted SSH channel
So yes, you can use public/private keys

Just FYI,
for transfering files to/from a remote machine, using secure copy (scp) is faster than using secure FTP (SFTP)

However SFTP gives you a full interactive FTP session so you can issue commands to the remote server
SCP just transfers files, without any sort of interactive control

---

### Post by trentscott on 2010-11-18
If I don't use keys, does that mean my password will be sent out in the open and prone to sniffing?

---

### Post by amauk on 2010-11-18
> **trentscott said:**
> If I don't use keys, does that mean my password will be sent out in the open and prone to sniffing?
No
Absolutely not

SSH will establish an encrypted channel between client & server
client then sends login credentials (username & pass) over encrypted channel to server
If login credentials are OK, then connection established

Keys just change how the authentication process works
Rather than "Here's a username & password, can I come in?", it's "here's a key, can I come in?"

---

### Post by trentscott on 2010-11-18
Thanks!

---

