---
title: "SSH Login Question"
date: 2012-06-04
forum: Security
---

### Post by Tamalin on 2012-06-04
Just out of curiosity (I don't really plan on implement this), but is it possible to have an SSH server require a key and password authentication to log in?  In my experience it has always been one or the other...

---

### Post by papibe on 2012-06-04
Hi Tamalin.

Not possible, but the next best thing is pretty close.

The default process of generating a key involves encrypting  the key with a passphrase (a long password). That way, you would be required to first unlock your key with a passphrase, to gain access to your key that would allow you to connect to the server.

That is a very good practice BTW, because if someone gained access to your key, it wouldn't allow that person to connect without the passphrase. 

Does that answer your question?
Regards.

---

### Post by CharlesA on 2012-06-04
Papibe pretty much covered it.

See here: [http://serverfault.com/questions/161699/how-can-i-increase-ssh-security-can-i-require-both-a-key-and-password](http://serverfault.com/questions/161699/how-can-i-increase-ssh-security-can-i-require-both-a-key-and-password)

For more infos.

---

