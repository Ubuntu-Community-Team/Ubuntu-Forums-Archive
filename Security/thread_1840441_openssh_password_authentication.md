---
title: "openssh password authentication"
date: 2011-09-07
forum: Security
---

### Post by rp11235 on 2011-09-07
Hello

I use openssh for remote logins

When you login for the first time,(no preset key, public key) the remote host might send its public key. How exactly is the key sent? Is it encrypted? (Its probably not necessary since its the public key)
But how is the password sent when you login? Which encryption? Hashed?

It would also be ok if someone could put a link to the exact documentation link.
Thanks
rp11235

---

### Post by haqking on 2011-09-07
> **rp11235 said:**
> Hello

I use openssh for remote logins

When you login for the first time,(no preset key, public key) the remote host might send its public key. How exactly is the key sent? Is it encrypted? (Its probably not necessary since its the public key)
But how is the password sent when you login? Which encryption? Hashed?

It would also be ok if someone could put a link to the exact documentation link.
Thanks
rp11235


public keys are exactly that, public.

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

the keys use hashing, encryption and compression depending on type of key

---

### Post by rp11235 on 2011-09-08
Thanks

[rp11235@rp11235 ~]$ ssh <ipaddr>
The authenticity of host '<ipaddr> (<ipaddr>)' can't be established.
RSA key fingerprint is 
<Long Key>
Are you sure you want to continue connecting (yes/no)? 
Warning: Permanently added '<ipaddr>' (RSA) to the list of known hosts.

rp11235@<ipaddr>'s password: 


In this case is the public key sent unencrypted over the network ? In either case i suppose subsequent connections will be encrypted with the public key, but does ssh do anything to ensure the authenticity if the initial transmission of the public key? That it is from the remote host?
And what about the password part? Is it hashed , then encrypted and sent?

Thanks
rp11235

---

### Post by Bachstelze on 2011-09-08
All this is described in the RFCs. Read them.

[http://openssh.org/manual.html](http://openssh.org/manual.html)

---

### Post by Lars Noodén on 2011-09-08
[http://tools.ietf.org/html/rfc4250](http://tools.ietf.org/html/rfc4250)
[http://tools.ietf.org/html/rfc4251](http://tools.ietf.org/html/rfc4251)
[http://tools.ietf.org/html/rfc4252](http://tools.ietf.org/html/rfc4252)
[http://tools.ietf.org/html/rfc4253](http://tools.ietf.org/html/rfc4253)
[http://tools.ietf.org/html/rfc4254](http://tools.ietf.org/html/rfc4254)
[http://tools.ietf.org/html/rfc4255](http://tools.ietf.org/html/rfc4255)
[http://tools.ietf.org/html/rfc4256](http://tools.ietf.org/html/rfc4256)

---

