---
title: "Question on encryption."
date: 2011-10-19
forum: Security
---

### Post by eldaria on 2011-10-19
I was wondering in regards to encryption.

I would like a cron job to automatically encrypt some text files in the background without me having to worry about entering a password, or anything like that, it would survive a reboot, etc.

However I want to avoid that if someone get hold of the computer, that they can find the decryption key on the computer.

So I would like a way to keep the encryption key and decryption key separate so that I could for example have the decryption key on a usb stick or similar and the cron script would use an encryption key to encrypt the data, but this key can not be used to decrypt the data, for this you would need the separate decryption key.

I hope you understand what I mean, is this even possible?

---

### Post by movieman on 2011-10-19
You need to use something like gpg with public key encryption; then you can store the public key on the computer to encrypt with, and keep the private key for decryption on a separate system.

---

### Post by agillator on 2011-10-19
I also advise checking out gnupg as movieman suggested. You can keep your private key on a USB stick and as long as you keep that secure you are in good shape.

---

### Post by eldaria on 2011-10-20
Great tip guys, I will look into gpg.

---

### Post by pizza-is-good on 2011-10-20
Be sure to look at the encryption laws of your country to make sure it is legal to encrypt files where you are. Some countries are very strict on this, and do not allow anyone to use any form of data encryption...

---

