---
title: "Error in Ubuntu Server Guide? DSA SSH keys?"
date: 2010-07-17
forum: Server Platforms
---

### Post by JoelInDenmark on 2010-07-17
In the Ubuntu 10.04 Server Guide, the SSH setup section suggests creating DSA keys for SSH authentication.
[https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html#openssh-keys](https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html#openssh-keys)

According to SSH/OpenSSH/Keys guide at [https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Key-Based%20SSH%20Logins](https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Key-Based%20SSH%20Logins)  (among many others), RSA is more secure than DSA: 
> SSH can use either "RSA" (Rivest-Shamir-Adleman) or "DSA" ("Digital  Signature Algorithm") keys.  Both of these were considered  state-of-the-art algorithms when SSH was invented, but DSA has come to  be seen as less secure in recent years.  RSA is the only recommended  choice for new keys, so this guide uses "RSA key" and "SSH key"  interchangeably. Shouldn't the Server Guide setup guide users through creation of the more secure RSA keys? as in
```
ssh-keygen -t rsa
```Is there some compelling reason to use DSA when running Ubuntu Server?

---

### Post by jbrown96 on 2010-07-17
RSA is a better algorithm for encrypting communications. It generates a good secure stream; whereas, DSA isn't really meant for that.
For SSH keys, the entire point is moot. You are only creating a very small key for authentication purposes. SSH automatically uses AES-128 I think, so your key cipher doesn't dictate the stream cipher. Both are secure for the small amount of data that a key uses. 

On my systems, I use RSA, but not for any particular reason.

---

### Post by JoelInDenmark on 2010-07-17
Good point, jbrown96.  Thanks for your input.

So it's certainly not an error, but it is perhaps unnecessarily complex for the guide to suggest **ssh-keygen -t dsa** when **ssh-keygen** (which is identical to **ssh-keygen -t rsa**) would be sufficient.

This is a small point, but I'll suggest it to the Documentation people.

---

