---
title: "Connecting to multiple SSH servers using the same SSH client"
date: 2014-11-15
forum: Security
---

### Post by project722 on 2014-11-15
Planning on using a single Ubuntu system to access multiple SSH servers. When I get the private key for the new server how would I tell the client machine which private key file to use? And would I also need to put the servers public key in the authorized_keys file on the client as well?

---

### Post by The Cog on 2014-11-15
You don't get the private key for the server. The server keeps that private.

If you want to use passwordless logins, then you need to add the client's public key to the authorized_keys file of each of the servers.

When the client connects to the server, it will add (with your permission) a fingerprint to the known hosts file to verify the server identity in subsequent connections.

---

### Post by project722 on 2014-11-15
Then what does this mean:

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

Second paragraph:

"The private key is kept on the computer you log in from, while the public key is stored on the **.ssh/authorized_keys** file on all the computers you want to log in to" 

log in from =client
log in to = server

I had to configure the private key in both putty and my Ubuntu client before it would work.

---

### Post by project722 on 2014-11-15
Well sure enough if I remove "id_rsa" (which is the private key) from the client system I can no longer SSH to the server. As soon as I put it back it works. Am I missing something here? Did I configure the client/server correctly? Everything I find on setting up OpenSSH has no reference on putting the private key on the server.

---

### Post by The Cog on 2014-11-15
It is talking about the client's private key. 
The client keeps its private key private, but adds its public key to the server's list of authorised keys.

---

### Post by project722 on 2014-11-15
I'm thoroughly confused now. You clearly said that the private key is kept private by the server, which to me implies that it must go on the server somewhere. I only created a single key pair and never put the private key on the server. I guess OpenSSH works a bit different than SSL servers. Anyway what I am going to do is just use the same keypair for each server I want to connect to. That way I can use the same private key for all servers and not have to worry about multiple private keys.

---

### Post by The Cog on 2014-11-15
I don't think the server's private (or public key) come into it, unless it's public key is used as part of the fingerprinting process. If it is, it is invisible to the user.

Forget about the server's keys. What matters is the client's keys. 
Keep the client's private key private. Add the client's public key to the server's authorized_keys file (repeat for each server). That's all.

You add the public key to authorized_keys by concatenating it:
```
cat client_public_key >> authorized_keys
```

---

### Post by project722 on 2014-11-15
Yeah, had to do that already since putty requires the public in a different format than native Linux SSH. So I have the same public in there twice just formatted differently. One allows me to log in with putty, the other with Linux ssh. Thanks for the help :)

---

### Post by The Cog on 2014-11-16
l didn't know that. Putty really is a strange beast.
Its default action for right-click is to paste the entire copy/paste buffer into the conversation. It's caused so much damage where I work that they have banned it.

---

### Post by fugu2 on 2014-11-27
> **project722 said:**
> Then what does this mean:

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

Second paragraph:

"The private key is kept on the computer you log in from, while the public key is stored on the **.ssh/authorized_keys** file on all the computers you want to log in to" 


Each computer (both client and server) need separate public/private key pairs. The above statement is referring to only the client's key pair only.

---

