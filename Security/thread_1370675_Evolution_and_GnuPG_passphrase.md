---
title: "Evolution and GnuPG passphrase"
date: 2010-01-02
forum: Security
---

### Post by MMYoung on 2010-01-02
Let me first start out by saying that I've searched on this forum and couldn't find the answer to the problem I'm having, it could be that I just didn't search for the right thing.

Anyway, Evolution will/cannot access my GPG passphrase agent (Seahorse), or at least it doesn't seem to since I have to type in the passphrase for my signing key each time I send an email. I can select the "remember for session" check box and I won't have to type it in as long as I have that session open. Close that session and I'm back to square one and typing in the passphrase again. I don't have that problem with anything else, encrypting/decrypting files just asks for authorization.

Running 9.10 64 bit and did install the seahorse-plugins package.

Any help would be greatly appreciated.

MMYoung

---

### Post by zivagolee on 2010-05-20
I am getting this issue in Lucid as well.  Was working fine in Karmic.

---

### Post by rookcifer on 2010-05-20
I recommend you use Thunderbird + Enigmail if you want e-mail encryption.  The reason is that Evolution silently defaults to using SHA-1, no matter what hash you have set in your gpg.conf.  Evolution does not support any SHA2 hash.

More info [here.]("http://blogs.ubuntu-nl.org/dennis/2009/05/10/evolution-vs-sha256/")

---

