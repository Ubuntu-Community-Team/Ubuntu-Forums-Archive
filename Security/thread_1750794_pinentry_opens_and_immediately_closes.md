---
title: "pinentry opens and immediately closes"
date: 2011-05-05
forum: Security
---

### Post by brock201 on 2011-05-05
So, I have (I think) done everything I need to in order to start using gnupg on my netbook running the latest version of kubuntu, but when I go to check to see if it work, I run...

```
gpg --sign -b --use-agent temp.text
```...pinentry opens and immediately closes without waiting for me to enter a passphrase three times.  The output is...

```

You need a passphrase to unlock the secret key for
user: "Brock Rogers (10T Web Design) <brock@10twebdesign.com>"
2048-bit RSA key, ID 068CFFA6, created 2011-05-05

gpg: Invalid passphrase; please try again ...

You need a passphrase to unlock the secret key for
user: "Brock Rogers (10T Web Design) <brock@10twebdesign.com>"
2048-bit RSA key, ID 068CFFA6, created 2011-05-05

gpg: Invalid passphrase; please try again ...

You need a passphrase to unlock the secret key for
user: "Brock Rogers (10T Web Design) <brock@10twebdesign.com>"
2048-bit RSA key, ID 068CFFA6, created 2011-05-05

gpg: no default secret key: bad passphrase
gpg: signing failed: bad passphrase

```Anyone have any idea what's going on here?

---

