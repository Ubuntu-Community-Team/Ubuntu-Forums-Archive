---
title: "Encryption"
date: 2011-07-16
forum: Security
---

### Post by TimeDistort12 on 2011-07-16
Does an RSA private key mean RSA could decrypt my data if they got hold of it?

Can people that make encryption decrypt your data?

---

### Post by insane_alien on 2011-07-16
no. not unless they had your private key.

---

### Post by haqking on 2011-07-16
> **TimeDistort12 said:**
> Does an RSA private key mean RSA could decrypt my data if they got hold of it?

Can people that make encryption decrypt your data?

private means exactly that, it is private.

your keys are as secure as the encryption algorithm and strength used.

---

### Post by TimeDistort12 on 2011-07-16
I am looking at the process of getting an SSL cert for my website, but in the process, its asking me to paste the private key. That would mean the CA would be have the ability to decrypt the data as well, right?

---

### Post by tubbygweilo on 2011-07-16
Can yon please let us know the name of the site asking for key details then we may have enough information to form an opinion as to why such a request is being made of you.

---

### Post by TimeDistort12 on 2011-07-17
All of them. When submitting some CSR thing, they ask you for your key or something. I'm guessing this would mean they would be able to decrypt your encrypted data if you gave it to them.. So, your server, client... and CA have the ability to read the encrypted data?

---

### Post by HermanAB on 2011-07-17
No, the key they ask for is probably in case you put an additional password on the CSR - if you don't want to send the CSR to them in plain text.  Usually that is not done.

---

