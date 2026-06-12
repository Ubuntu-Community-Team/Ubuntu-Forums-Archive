---
title: "Checking passphrases on ssh keys"
date: 2008-07-03
forum: Security
---

### Post by wiz561 on 2008-07-03
Hi!

I'm digging around and trying to figure out if there is a way to enforce passphrases on ssh keys.  As you know, if there isn't a passphrase on the key and somebody grabs it, they can login to the system as you.

What I'm trying to do is configure sshd to not accept a connection from a ssh key that isn't password protected.  If that isn't possible, is there a way to check the public key stored on the server to ensure the private key has a passphrase?


Thanks!

---

### Post by HalPomeranz on 2008-07-03
There is no way for a remote server to figure out if the private key being used for a connection has a passphrase or not.  The only way you can test for this condition is to be on the machine where the private key is stored and examine the key file directly.

---

### Post by veNom_bz on 2008-07-04
you should definitely add pass phrases to all your keys. you can use puttygen to add a pass phrase to private key (your key pair will still be valid). or ssh-keygen of course. ```
ssh-keygen -p [-P old_passphrase] [-N new_passphrase][-f keyfile]
```

---

### Post by Biochem on 2008-07-04
This is just an idea, I have no clue how to do it, but maybe there is a way to configure sshd to ask for an rsa key and a passphrase. That way if one or the other is compromised there is a second safety net. Beside, that way you always have the control on the password policy (length and such) on the server.

---

