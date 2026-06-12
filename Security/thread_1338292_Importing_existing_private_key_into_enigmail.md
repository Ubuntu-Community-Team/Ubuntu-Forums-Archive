---
title: "Importing existing private key into enigmail?"
date: 2009-11-26
forum: Security
---

### Post by knottshawk on 2009-11-26
I have pgp on an XP box... I'm migrating to Ubuntu with Thunderbird. I installed enigmail but I can't figure out how to import my private key into enigmail. How do I tell it what MY key is? I've read tutorials but they seem focused on importing public keys... so that I can read other peoples messages. Any tips would be great...

---

### Post by nunki on 2009-11-26
You need to import the private key into your keyring, then enigmail should be able to access it.

Import private key to keyring:
```

gpg --allow-secret-key-import --import private.key


```

Where private.key is the keyfile

Then open up Thunderbird and click on OpenPGP on the top bar and select "Key Management". If you see your key there, you should be all set.

---

### Post by knottshawk on 2009-11-26
Okay... I'm a moron... I accidentally missed the "include private key" in my export. So, when I did that, it appears to have imported properly.. but now I have a different issue. When I try to send to one of my public keys (a friend of mine) it comes back with the error "encryption command failed"
Then it says "skipped" and "[stdin]: clearsign failed: secret key not available"

---

### Post by bodhi.zazen on 2009-11-26
First confirm that the key was imported.

Assuming it is, you then need to mark it as trusted

```
gpg --edit-key KEY_NAME
```

Mark the key as trusted, ultimate

---

