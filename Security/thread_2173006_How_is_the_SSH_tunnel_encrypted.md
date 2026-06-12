---
title: "How is the SSH tunnel encrypted"
date: 2013-09-07
forum: Security
---

### Post by sefs on 2013-09-07
Hi there,

How is the SSH tunnel encrypted?

The server has it's host keys to authenticate to the client.
The client has it's keys to authenticate to the server.

1/
After this is done and everyone agrees that they like each other with who's key is the tunnel encrypted.
Is the tunnel encrypted using the server host keys OR the client keys 
Or is it the case that when the client sends info to the server it is encrypted with the server's public key and when the server replies to the client it is encrypted with the client's public key.

2/
If the server has a 1024 RSA key in use and this is some how brute forced, can the person doing the brute forcing then impersonate the the server (as well decrypt the intercepted data stream) from the information he has gleaned?

Thanks.

---

### Post by CharlesA on 2013-09-07
Have a read:
[http://superuser.com/questions/383732/how-does-ssh-encryption-work](http://superuser.com/questions/383732/how-does-ssh-encryption-work)

---

### Post by sefs on 2013-09-07
> **CharlesA said:**
> Have a read:
[http://superuser.com/questions/383732/how-does-ssh-encryption-work](http://superuser.com/questions/383732/how-does-ssh-encryption-work)

Very good thank you.  I notice that by default ssh is serving up an ecdsa key.  Is their away to tell it to always use rsa?

Thanks.

---

### Post by CharlesA on 2013-09-07
It shouldn't matter, the host keys are only used to verify that you are connecting to the machine you think you are connecting to.

---

### Post by sefs on 2013-09-07
> **CharlesA said:**
> It shouldn't matter, the host keys are only used to verify that you are connecting to the machine you think you are connecting to.

Imagine a scenario where the public key of the server is brute forced.  Is it possible then for the person doing the brute force to then impersonate the server now having all the information needed to impersonate?

I see that simply removing the ecdsa key makes the server drop back to RSA.

---

