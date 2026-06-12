---
title: "Public key AND password authentication?"
date: 2008-09-09
forum: Security
---

### Post by kizza on 2008-09-09
Has anyone worked out a way to force users to provide a public key and a password before they can log in? My reasons for wanting this are:
* I want a way to mitigate the risk of a key logger being present
* I can use a password policy, but I can't force users to sign their keys, or to make them sign them with a good passphrase

Therefore, I think that this provides a good enough way to do two-factor authentication. Is there a way to do this on Ubuntu? If you want to question my security assumptions that's fine too :)

---

### Post by HermanAB on 2008-09-09
You have to study PAM.

The most important thing with PAM is to make a complete backup of /etc/pam.d before you touch anything.

Cheers,

Herman

---

### Post by koenn on 2008-09-10
> **kizza said:**
> 
* I can use a password policy, but I can't force users to sign their keys, or to make them sign them with a good passphrase

Therefore, I think that this provides a good enough way to do two-factor authentication. Is there a way to do this on Ubuntu? If you want to question my security assumptions that's fine too :)

couldn't you just assign passphrase signed keys to your users ?

---

### Post by Biochem on 2008-09-11
> **koenn said:**
> couldn't you just assign passphrase signed keys to your users ?

The user can still change/delete the passphrase on the key.

---

### Post by kizza on 2008-09-12
As I said, the reason for wanting passwords is so I can have policies like password expiry, minimum lengths, etc. 
Anyway, it looks like it's not an option in OpenSSH:
[http://www.nabble.com/Requiring-multiple-authentication-td15853991.html](http://www.nabble.com/Requiring-multiple-authentication-td15853991.html)
This suggests that patches are necessary, but I'm not really comfortable doing that with something so important!

So it looks like the best way is to use certificates + trust users to use good passphrases.

---

