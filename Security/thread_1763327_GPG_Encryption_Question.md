---
title: "GPG Encryption Question"
date: 2011-05-20
forum: Security
---

### Post by spynappels on 2011-05-20
Hi Guys,

This may seem like a stupid question, but to decrypt and GPG encrypted file, the secret key is needed rather than the public key, right? But for checking a signature the public key is fine?

Where I'm confused is in Encrypting email messages etc.

If I sign them with my secret key, then the recipient will not be able to decrypt the email, but I obviously don't want them to have my secret key.

Can I encrypt a mail message using the recipient's public key so they can decrypt it with their secret key, or have I completely missed the point of what can be done here?

I've done lots of reading, but not been able to get my head round this so far. Thanks for any help.

---

### Post by matt_symes on 2011-05-20
Hi

> **spynappels said:**
> Hi Guys,

This may seem like a stupid question, but to decrypt and GPG encrypted file, the secret key is needed rather than the public key, right? But for checking a signature the public key is fine?

Where I'm confused is in Encrypting email messages etc.

If I sign them with my secret key, then the recipient will not be able to decrypt the email, but I obviously don't want them to have my secret key.

Can I encrypt a mail message using the recipient's public key so they can decrypt it with their secret key, or have I completely missed the point of what can be done here?

I've done lots of reading, but not been able to get my head round this so far. Thanks for any help.

In it's most basic form this is what happens. 

Say you want to send a message to your friend Fred. 

Fred has a public key that he gives to you and a private key that he keeps to himself. 

You encrypt the message that you want to send to Fred with the public key Fred has given you. You then mail that encrypted message to Fred. Fred uses his private key to unencrypt the message. He can then view the message.

When you want to reply, you send Fred your public key and keep your private key hidden. Fred then encrypts his response using your public key that you gave him. When you receive his response, you decrypt it using your private key.

Hope that helps.

Kind regards

---

### Post by spynappels on 2011-05-20
Hi Matt,

I kinda figured that that was the way it worked, thanks for clarifying that for me.

Just to confirm that I got the other end of it correct, if I sign a message, I do so with my secret key and my public key is used to verify that my signature is correct?

Thanks for the quick reply!

---

### Post by matt_symes on 2011-05-20
Hi

> **spynappels said:**
> 
Just to confirm that I got the other end of it correct, if I sign a message, I do so with my secret key and my public key is used to verify that my signature is correct?

That is exactly correct. Safe e-mailing :)

Kind regards

---

### Post by spynappels on 2011-05-20
Cool, thanks.

---

