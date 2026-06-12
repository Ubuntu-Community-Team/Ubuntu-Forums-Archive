---
title: "PCMANFM: Encryption"
date: 2016-05-09
forum: Security
---

### Post by asearle on 2016-05-09
Hallo Everyone,

I am currently setting up a newly acquired laptop with Lubuntu (my favourite due to the speed, simplicity and classic-style menu-structures) and would like to include encryption.

I was pondering selecting encryption during the install but as only a small part of my "stuff" needs to be protected that seemed to be using a sledge-hammer to crack a nut.

So my question now is whether there is an encryption tool that I can use to encrypt/protect specific directories and which will work seamlessly with common file-managers (e.g. PCMANFM in Lubuntu)?

Or would it be better to simply not "mess around" and instead select encrypt at install?

Many thanks for any tips that you can give me.

Regards,
Alan
Cologne, Germany

---

### Post by DuckHook on 2016-05-09
For non-critical, relatively insensitive installs&#8213;which covers most ordinary users&#8213;I do not recommend full disk encryption. Note the important caveats: if you are keeping sensitive data, then the added trouble and potential difficulty of recovery of full disk encryption are not only worthwhile but necessary. However, for most ordinary use, full disk encryption is IMO overkill. Also, if you forget the key, or something goes wrong, it is a real bear to try to decrypt and recover your data.

You could instead encrypt just your /home directory, but this has a lot of the drawbacks of full disk encryption and not many of the benefits, since your passwords, etc are in the un-encrypted part of your disk (although they are separately encrypted). But again, if you forget your key or your decryption sector gets corrupted, your data is, for all intents and purposes, unrecoverable.

I have found that the best method for me is to set up an encrypted *Private* directory. It is the only encrypted directory on my system. I put all of my really important private stuff there: like my RSA and PGP keys, my Firefox passwords and user data, etc and then symlink back to where the system expects to find these files. The result is that relatively innocuous data&#8213;but stuff that's still important to me and that I wouldn't want lost forever&#8213;like my personal photos, music, etc remain un-encrypted, but sensitive data is fully encrypted. Instructions for setting up an encrypted *Private* directory follows:

[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

Make sure that you don't have automatic login enabled on your machine (why people would want to do that and still use encryption is beyond me). The moment that you log in, your *Private* directory will be automatically mounted and accessible and PCmanFM should work seamlessly with it.

PS. I have also moved your thread to the *Security* forum which is more appropriate to your question.

---

