---
title: "Is storing pass as plain text safe with CheckGmail?"
date: 2008-03-16
forum: Security Discussions
---

### Post by Redrazor39 on 2008-03-16
Is it secure? I know Google encrypts gmail passwords but is it safe to use CheckGmail and safe the Password?

---

### Post by Dr Small on 2008-03-16
Having passwords plaintext is never secure, but I don't know how CheckGmail works. If it sends it plaintext to gmail and then encrypts it, the packet can be sniffed and the plaintext password revealed.

---

### Post by Redrazor39 on 2008-03-16
aw man, I really liked checkGmail. If only they would make a secure version. I even use the https version of gmail (it's not that slow) for some reason!

---

### Post by p_quarles on 2008-03-16
SSL (secure socket layer) if configured correctly will provide password security. Much like other secure protocols, an SSL connection performs a handshake between the client and the server to establish the identity of the latter, and then sends any authentication information in an encrypted form. 

Personally, I think it is more advisable to use an e-mail client which can grab your password from a key manager such as Gnome-Keyring or KWallet. If CheckGmail can't do this, I would suggest moving to a client that does (Evolution, Kmail).

---

