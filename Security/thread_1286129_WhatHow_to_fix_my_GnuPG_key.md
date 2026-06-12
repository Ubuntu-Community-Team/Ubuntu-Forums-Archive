---
title: "What/How to fix my GnuPG key"
date: 2009-10-08
forum: Security
---

### Post by ermeyers on 2009-10-08
I need some help figuring out what to do with gpg.  This is a key and subkey question regarding encryption and decryption.  I can't decrypt something that someone has sent me, or that I encrypted myself.

I've had my GnuPg key for a while, and all I really used them for was signing packages:
```
$ gpg --list-keys 83CE80A3
pub   1024D/83CE80A3 2005-07-08
uid                  <my email address>
sub   1024g/AB3CB709 2005-07-08
```
I still have a secret key:
```
$ gpg --list-secret-keys 83CE80A3
sec   1024D/83CE80A3 2005-07-08
uid                  <my email addres>
uid       [ revoked] <old email address 1>
uid       [ revoked] <old email address 2>
```

When I try to decrypt a file, I get "gpg: decryption failed: secret key not available".
Here's the encryption of toenc.txt:
```
gpg -r my_email_address --encrypt toenc.txt
```

Here's the decryption:
```
gpg --decrypt toenc.txt.gpg
gpg: encrypted with 1024-bit ELG-E key, ID AB3CB709, created 2005-07-08
      "<my emai address>"
gpg: decryption failed: secret key not available
```

Should I "gpg --gen-revoke 83CE80A3" for the reason "Key is superseded", and description "Subkey problem".  Or something else?

Thanks --Eric

---

### Post by ermeyers on 2009-10-08
NEVERMIND.  Nobody answered, so I made a descision on my own.

---

### Post by ermeyers on 2009-10-08
> **ermeyers said:**
> NEVERMIND.  Nobody answered, so I made a descision on my own.

I revoked my public key.  Then, did according to [https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)

The End.

---

### Post by kevdog on 2009-10-08
Um Im not sure you had to do that?  I think you needed to specifiy the ID of your key on the command line rather than use the email address.

---

### Post by ermeyers on 2009-10-13
The "-r <email_address>" is to list yourself as a recipient, so that you can decrypt an encryption.

---

